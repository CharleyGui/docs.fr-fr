---
title: Informations d’identification de canal-gRPC pour les développeurs WCF
description: Comment implémenter et utiliser les informations d’identification du canal gRPC dans ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967962"
---
# <a name="channel-credentials"></a>Informations d’identification de la chaîne

Comme son nom l’indique, les informations d’identification du canal sont attachées au canal gRPC sous-jacent. La forme standard des informations d’identification de canal utilise l’authentification par certificat client, où le client fournit un certificat TLS lorsqu’il effectue la connexion, qui est vérifiée par le serveur avant d’autoriser les appels à effectuer.

Les informations d’identification de canal peuvent être combinées avec les informations d’identification d’appel pour offrir une sécurité complète pour un service gRPC. Les informations d’identification du canal prouvent que l’application cliente est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application cliente.

L’authentification par certificat client fonctionne pour gRPC de la même façon que pour les ASP.NET Core. Le processus de configuration sera Résumé ici, mais des informations supplémentaires sont disponibles dans l’article [configurer l’authentification par certificat dans ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

À des fins de développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPs approprié signé par une autorité de confiance.

## <a name="adding-certificate-authentication-to-the-server"></a>Ajout de l’authentification par certificat au serveur

Vous devez configurer l’authentification par certificat au niveau de l’hôte, par exemple sur le serveur Kestrel, et dans le pipeline ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Configuration de la validation de certificat sur Kestrel

Vous pouvez configurer Kestrel (serveur HTTP ASP.NET Core) pour exiger un certificat client et éventuellement effectuer une validation du certificat fourni avant d’accepter les connexions entrantes. Cette configuration s’effectue dans la méthode `CreateWebHostBuilder` de la classe `Program`, plutôt que dans `Startup`.

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

Le paramètre `ClientCertificateMode.RequireCertificate` fait en sorte que Kestrel rejette immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ne valide pas le certificat. L’ajout du rappel `ClientCertificateValidation` permet à Kestrel de valider le certificat client (dans ce cas, de s’assurer qu’il a été émis par la même *autorité de certification* que le certificat de serveur) au point où la connexion est établie, avant que le pipeline ASP.net Core soit engagé.

### <a name="adding-aspnet-core-certificate-authentication"></a>Ajout d’ASP.NET Core l’authentification par certificat

L’authentification par certificat est fournie par le package NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Ajoutez le service d’authentification de certificat dans la méthode `ConfigureServices` et ajoutez l’authentification et l’autorisation au pipeline ASP.NET Core dans la méthode `Configure`.

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

Avec le package `Grpc.Net.Client`, les certificats sont configurés sur une instance de <xref:System.Net.Http.HttpClient> fournie au `GrpcChannel` utilisé pour la connexion.

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

Pour fournir à la fois ChannelCredentials et CallCredentials sur le client, utilisez la méthode `ChannelCredentials.Create` pour appliquer les informations d’identification d’appel. L’authentification par certificat doit encore être appliquée à l’aide de l’instance de <xref:System.Net.Http.HttpClient> : Si vous transmettez des arguments au constructeur `SslCredentials`, le code client interne lève une exception. Le paramètre `SslCredentials` est inclus uniquement dans la méthode `Create` du package `Grpc.Net.Client` pour assurer la compatibilité avec le package `Grpc.Core`.

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
> Vous pouvez utiliser la méthode `ChannelCredentials.Create` pour un client sans authentification par certificat, afin de passer des informations d’identification de jeton à chaque appel effectué sur le canal.

Une version de l' [exemple d’application GRPC FullStockTicker avec l’authentification par certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.

>[!div class="step-by-step"]
>[Précédent](call-credentials.md)
>[Suivant](encryption.md)
