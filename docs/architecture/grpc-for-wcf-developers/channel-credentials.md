---
title: Informations d’identification de canal - gRPC pour WCF Developers
description: Comment implémenter et utiliser les informations d’identification du canal GRPC dans ASP.NET Core 3.0.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148203"
---
# <a name="channel-credentials"></a>Informations d’identification de la chaîne

Comme son nom l’indique, les informations d’identification des canaux sont fixées au canal gRPC sous-jacent. La forme standard d’informations d’identification des canaux utilise l’authentification des certificats clients. Dans ce processus, le client fournit un certificat TLS lorsqu’il effectue la connexion, puis le serveur vérifie cela avant de permettre tout appel à faire.

Vous pouvez combiner les informations d’identification des canaux avec les informations d’identification des appels afin d’assurer une sécurité complète pour un service gRPC. Les informations d’identification du canal prouvent que l’application client est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application client.

L’authentification des certificats clients fonctionne pour gRPC de la même façon qu’elle fonctionne pour ASP.NET Core. Pour plus d’informations, voir [l’authentification du certificat Configure dans ASP.NET Core](/aspnet/core/security/authentication/certauth).

Pour le développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPS approprié signé par une autorité de confiance.

## <a name="add-certificate-authentication-to-the-server"></a>Ajouter l’authentification du certificat au serveur

Configurer l’authentification des certificats à la fois au niveau de l’hôte (par exemple, sur le serveur Kestrel), et dans le pipeline ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Configurer la validation du certificat sur Kestrel

Vous pouvez configurer Kestrel (le serveur CORE HTTP ASP.NET) pour exiger un certificat client, et en option pour effectuer une validation du certificat fourni, avant d’accepter les connexions entrantes. Vous faites cela `CreateWebHostBuilder` dans `Program` la méthode de `Startup`la classe, plutôt que dans .

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

Le `ClientCertificateMode.RequireCertificate` paramètre amène Kestrel à rejeter immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ce paramètre en soi ne validera pas un certificat qui est fourni. Ajoutez `ClientCertificateValidation` le rappel pour permettre à Kestrel de valider le certificat client au moment où la connexion est effectuée, avant que le pipeline ASP.NET Core ne soit engagé. (Dans ce cas, le rappel garantit qu’il a été délivré par la même *autorité de certificat* que le certificat serveur.)

### <a name="add-aspnet-core-certificate-authentication"></a>Ajouter ASP.NET authentification du certificat de base

Le package [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet fournit l’authentification des certificats.

Ajoutez le service d’authentification du certificat dans la `ConfigureServices` méthode, et `Configure` ajoutez l’authentification et l’autorisation au pipeline ASP.NET Core dans la méthode.

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="provide-channel-credentials-in-the-client-application"></a>Fournir les informations d’identification du canal dans l’application client

Avec `Grpc.Net.Client` le paquet, vous configurez des certificats sur une <xref:System.Net.Http.HttpClient> instance qui est fournie à l’utilisé `GrpcChannel` pour la connexion.

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combine-channelcredentials-and-callcredentials"></a>Combinez ChannelCredentials et CallCredentials

Vous pouvez configurer votre serveur pour utiliser à la fois l’authentification du certificat et du jeton. Faites-le en appliquant les modifications de certificat au serveur Kestrel, et en utilisant le middleware porte-moyens JWT dans ASP.NET Core.

Pour fournir `ChannelCredentials` `CallCredentials` à la fois `ChannelCredentials.Create` et sur le client, utilisez la méthode pour appliquer les informations d’identification d’appel. Vous devez toujours appliquer l’authentification des certificats en utilisant l’instance. <xref:System.Net.Http.HttpClient> Si vous transmettez des `SslCredentials` arguments au constructeur, le code client interne fait une exception. Le `SslCredentials` paramètre n’est inclus que dans la `Grpc.Net.Client` méthode du `Create` paquet pour maintenir la compatibilité avec le `Grpc.Core` paquet.

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> Vous pouvez `ChannelCredentials.Create` utiliser la méthode pour un client sans authentification de certificat. Il s’agit d’une façon utile de passer des informations d’identification symbolique avec chaque appel fait sur le canal.

Une version de la [demande gRPC échantillon FullStockTicker avec l’authentification de certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.

>[!div class="step-by-step"]
>[Suivant précédent](call-credentials.md)
>[Next](encryption.md)
