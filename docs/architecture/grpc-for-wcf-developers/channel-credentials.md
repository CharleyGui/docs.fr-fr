---
title: Informations d’identification de canal-gRPC pour les développeurs WCF
description: Comment implémenter et utiliser les informations d’identification du canal gRPC dans ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 61305ee47a2c09a0b2a0fd866beb9b7c102ffeaa
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184581"
---
# <a name="channel-credentials"></a>Informations d’identification du canal

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Comme son nom l’indique, les informations d’identification du canal sont attachées au canal gRPC sous-jacent. La forme standard des informations d’identification de canal utilise l’authentification par certificat client, où le client fournit un certificat TLS lorsqu’il effectue la connexion, qui est vérifiée par le serveur avant d’autoriser les appels à effectuer.

Les informations d’identification de canal peuvent être combinées avec les informations d’identification d’appel pour offrir une sécurité complète pour un service gRPC. Les informations d’identification du canal prouvent que l’application cliente est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application cliente.

L’authentification par certificat client fonctionne pour gRPC de la même façon que pour les ASP.NET Core. Le processus de configuration sera Résumé ici, mais des informations supplémentaires sont disponibles dans l’article [configurer l’authentification par certificat dans ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

À des fins de développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPs approprié signé par une autorité de confiance.

## <a name="adding-certificate-authentication-to-the-server"></a>Ajout de l’authentification par certificat au serveur

Vous devez configurer l’authentification par certificat au niveau de l’hôte, par exemple sur le serveur Kestrel, et dans le pipeline ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Configuration de la validation de certificat sur Kestrel

Vous pouvez configurer Kestrel (serveur HTTP ASP.NET Core) pour exiger un certificat client et éventuellement effectuer une validation du certificat fourni avant d’accepter les connexions entrantes. Cette configuration s’effectue dans la `CreateWebHostBuilder` méthode de la `Program` classe, plutôt que dans `Startup`.

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

Le `ClientCertificateMode.RequireCertificate` paramètre force Kestrel à rejeter immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ne valide pas le certificat. L’ajout `ClientCertificateValidation` du rappel permet à Kestrel de valider le certificat client (dans ce cas, de s’assurer qu’il a été émis par la même *autorité de certification* que le certificat de serveur) au point où la connexion est établie, avant le ASP.net Core le pipeline est engagé.

### <a name="adding-aspnet-core-certificate-authentication"></a>Ajout d’ASP.NET Core l’authentification par certificat

L’authentification par certificat est fournie par le package NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Ajoutez le service d’authentification de certificat `ConfigureServices` dans la méthode et ajoutez l’authentification et l’autorisation au pipeline `Configure` ASP.net core dans la méthode.

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

## <a name="providing-channel-credentials-in-the-client-application"></a>Fournir des informations d’identification de canal dans l’application cliente

Avec le `Grpc.Net.Client` package, les certificats sont configurés <xref:System.Net.Http.HttpClient> sur une instance de `GrpcChannel` qui est fournie au utilisé pour la connexion.

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

## <a name="combining-channelcredentials-and-callcredentials"></a>Combinaison de ChannelCredentials et CallCredentials

Vous pouvez configurer votre serveur pour utiliser l’authentification par certificat et par jeton en appliquant les modifications de certificat au serveur Kestrel et en utilisant l’intergiciel de support JWT dans ASP.NET Core.

Pour fournir à la fois ChannelCredentials et CallCredentials sur le client, `ChannelCredentials.Create` utilisez la méthode pour appliquer les informations d’identification d’appel. L’authentification par certificat doit encore être appliquée à <xref:System.Net.Http.HttpClient> l’aide de l’instance : Si vous transmettez des arguments `SslCredentials` au constructeur, le code client interne lève une exception. Le `SslCredentials` paramètre est inclus uniquement dans la `Grpc.Net.Client` méthode du `Create` package pour assurer la compatibilité avec `Grpc.Core` le package.

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
> Vous pouvez utiliser la `ChannelCredentials.Create` méthode pour un client sans authentification par certificat, afin de passer des informations d’identification de jeton à chaque appel effectué sur le canal.

Une version de l' [exemple d’application GRPC FullStockTicker avec l’authentification par certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.

>[!div class="step-by-step"]
>[Précédent](call-credentials.md)
>[Suivant](encryption.md)
