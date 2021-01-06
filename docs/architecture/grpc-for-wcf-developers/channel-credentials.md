---
title: Informations d’identification de canal-gRPC pour les développeurs WCF
description: Comment implémenter et utiliser les informations d’identification du canal gRPC dans ASP.NET Core 3,0.
ms.date: 12/15/2020
ms.openlocfilehash: 3663bbf061156db957241e2a32dbb9c64562ade2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938635"
---
# <a name="channel-credentials"></a>Informations d’identification de la chaîne

Comme son nom l’indique, les informations d’identification du canal sont attachées au canal gRPC sous-jacent. Le formulaire standard des informations d’identification de canal utilise l’authentification par certificat client. Dans ce processus, le client fournit un certificat TLS lorsqu’il effectue la connexion, puis le serveur vérifie ce certificat avant d’autoriser les appels à effectuer.

Vous pouvez combiner les informations d’identification de canal avec les informations d’identification d’appel pour offrir une sécurité complète pour un service gRPC. Les informations d’identification du canal prouvent que l’application cliente est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application cliente.

L’authentification par certificat client fonctionne pour gRPC de la même façon que pour les ASP.NET Core. Pour plus d’informations, consultez [configurer l’authentification par certificat dans ASP.net Core](/aspnet/core/security/authentication/certauth).

À des fins de développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPs approprié signé par une autorité de confiance.

## <a name="add-certificate-authentication-to-the-server"></a>Ajouter l’authentification par certificat au serveur

Configurez l’authentification par certificat au niveau de l’hôte (par exemple, sur le serveur Kestrel) et dans le pipeline ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Configurer la validation de certificat sur Kestrel

Vous pouvez configurer Kestrel (serveur HTTP ASP.NET Core) pour exiger un certificat client et éventuellement effectuer une validation du certificat fourni, avant d’accepter les connexions entrantes. Vous spécifiez cette configuration dans la `CreateWebHostBuilder` méthode de la `Program` classe, plutôt que dans `Startup` .

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

Le `ClientCertificateMode.RequireCertificate` paramètre oblige Kestrel à rejeter immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ce paramètre ne valide pas un certificat fourni. Ajoutez le `ClientCertificateValidation` rappel pour permettre à Kestrel de valider le certificat client au point où la connexion est établie, avant que le pipeline ASP.net Core soit engagé. (Dans ce cas, le rappel s’assure qu’il a été émis par la même *autorité de certification* que le certificat de serveur.)

### <a name="add-aspnet-core-certificate-authentication"></a>Ajouter ASP.NET Core l’authentification par certificat

Le package NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) fournit l’authentification par certificat.

Ajoutez le service d’authentification de certificat dans la `ConfigureServices` méthode et ajoutez l’authentification et l’autorisation au pipeline ASP.net core dans la `Configure` méthode.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>Fournir des informations d’identification de canal dans l’application cliente

Avec le `Grpc.Net.Client` package, vous configurez des certificats sur une <xref:System.Net.Http.HttpClient> instance de qui est fournie au `GrpcChannel` utilisé pour la connexion.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Combiner ChannelCredentials et CallCredentials

Vous pouvez configurer votre serveur pour qu’il utilise à la fois l’authentification par certificat et le jeton. Pour ce faire, appliquez les modifications du certificat au serveur Kestrel et utilisez l’intergiciel (middleware) du porteur JWT dans ASP.NET Core.

Pour fournir à `ChannelCredentials` la fois et `CallCredentials` sur le client, utilisez la `ChannelCredentials.Create` méthode pour appliquer les informations d’identification de l’appel. Vous devez toujours appliquer l’authentification par certificat à l’aide de l' <xref:System.Net.Http.HttpClient> instance. Si vous transmettez des arguments au `SslCredentials` constructeur, le code client interne lève une exception. Le `SslCredentials` paramètre est inclus uniquement dans la `Grpc.Net.Client` méthode du package `Create` pour assurer la compatibilité avec le `Grpc.Core` Package.

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
> Vous pouvez utiliser la `ChannelCredentials.Create` méthode pour un client sans authentification par certificat. Il s’agit d’un moyen utile pour passer des informations d’identification de jeton avec chaque appel effectué sur le canal.

Une version de l' [exemple d’application GRPC FullStockTicker avec l’authentification par certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.

>[!div class="step-by-step"]
>[Précédent](call-credentials.md) 
> [Suivant](encryption.md)
