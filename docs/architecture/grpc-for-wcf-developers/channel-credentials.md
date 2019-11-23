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
# <a name="channel-credentials"></a><span data-ttu-id="2f71b-103">Informations d’identification de la chaîne</span><span class="sxs-lookup"><span data-stu-id="2f71b-103">Channel credentials</span></span>

<span data-ttu-id="2f71b-104">Comme son nom l’indique, les informations d’identification du canal sont attachées au canal gRPC sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="2f71b-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="2f71b-105">La forme standard des informations d’identification de canal utilise l’authentification par certificat client, où le client fournit un certificat TLS lorsqu’il effectue la connexion, qui est vérifiée par le serveur avant d’autoriser les appels à effectuer.</span><span class="sxs-lookup"><span data-stu-id="2f71b-105">The standard form of channel credentials uses Client Certificate authentication, where the client provides a TLS certificate when it's making the connection, which is verified by the server before allowing any calls to be made.</span></span>

<span data-ttu-id="2f71b-106">Les informations d’identification de canal peuvent être combinées avec les informations d’identification d’appel pour offrir une sécurité complète pour un service gRPC.</span><span class="sxs-lookup"><span data-stu-id="2f71b-106">Channel credentials can be combined with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="2f71b-107">Les informations d’identification du canal prouvent que l’application cliente est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="2f71b-107">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person using the client application.</span></span>

<span data-ttu-id="2f71b-108">L’authentification par certificat client fonctionne pour gRPC de la même façon que pour les ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f71b-108">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="2f71b-109">Le processus de configuration sera Résumé ici, mais des informations supplémentaires sont disponibles dans l’article [configurer l’authentification par certificat dans ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="2f71b-109">The configuration process will be summarized here, but more information is available in the [Configure certificate authentication in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) article.</span></span>

<span data-ttu-id="2f71b-110">À des fins de développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPs approprié signé par une autorité de confiance.</span><span class="sxs-lookup"><span data-stu-id="2f71b-110">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="adding-certificate-authentication-to-the-server"></a><span data-ttu-id="2f71b-111">Ajout de l’authentification par certificat au serveur</span><span class="sxs-lookup"><span data-stu-id="2f71b-111">Adding certificate authentication to the server</span></span>

<span data-ttu-id="2f71b-112">Vous devez configurer l’authentification par certificat au niveau de l’hôte, par exemple sur le serveur Kestrel, et dans le pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f71b-112">You need to configure certificate authentication both at the host level, for example on the Kestrel server, and in the ASP.NET Core pipeline.</span></span>

### <a name="configuring-certificate-validation-on-kestrel"></a><span data-ttu-id="2f71b-113">Configuration de la validation de certificat sur Kestrel</span><span class="sxs-lookup"><span data-stu-id="2f71b-113">Configuring certificate validation on Kestrel</span></span>

<span data-ttu-id="2f71b-114">Vous pouvez configurer Kestrel (serveur HTTP ASP.NET Core) pour exiger un certificat client et éventuellement effectuer une validation du certificat fourni avant d’accepter les connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="2f71b-114">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate before accepting incoming connections.</span></span> <span data-ttu-id="2f71b-115">Cette configuration s’effectue dans la méthode `CreateWebHostBuilder` de la classe `Program`, plutôt que dans `Startup`.</span><span class="sxs-lookup"><span data-stu-id="2f71b-115">This configuration is done in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="2f71b-116">Le paramètre `ClientCertificateMode.RequireCertificate` fait en sorte que Kestrel rejette immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ne valide pas le certificat.</span><span class="sxs-lookup"><span data-stu-id="2f71b-116">The `ClientCertificateMode.RequireCertificate` setting will cause Kestrel to immediately reject any connection request that doesn't provide a client certificate, but it won't validate the certificate.</span></span> <span data-ttu-id="2f71b-117">L’ajout du rappel `ClientCertificateValidation` permet à Kestrel de valider le certificat client (dans ce cas, de s’assurer qu’il a été émis par la même *autorité de certification* que le certificat de serveur) au point où la connexion est établie, avant que le pipeline ASP.net Core soit engagé.</span><span class="sxs-lookup"><span data-stu-id="2f71b-117">Adding the `ClientCertificateValidation` callback enables Kestrel to validate the client certificate (in this case, ensuring that it was issued by the same *Certificate Authority* as the server certificate) at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span>

### <a name="adding-aspnet-core-certificate-authentication"></a><span data-ttu-id="2f71b-118">Ajout d’ASP.NET Core l’authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="2f71b-118">Adding ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="2f71b-119">L’authentification par certificat est fournie par le package NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .</span><span class="sxs-lookup"><span data-stu-id="2f71b-119">Certificate authentication is provided by the [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package.</span></span>

<span data-ttu-id="2f71b-120">Ajoutez le service d’authentification de certificat dans la méthode `ConfigureServices` et ajoutez l’authentification et l’autorisation au pipeline ASP.NET Core dans la méthode `Configure`.</span><span class="sxs-lookup"><span data-stu-id="2f71b-120">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="providing-channel-credentials-in-the-client-application"></a><span data-ttu-id="2f71b-121">Fournir des informations d’identification de canal dans l’application cliente</span><span class="sxs-lookup"><span data-stu-id="2f71b-121">Providing channel credentials in the client application</span></span>

<span data-ttu-id="2f71b-122">Avec le package `Grpc.Net.Client`, les certificats sont configurés sur une instance de <xref:System.Net.Http.HttpClient> fournie au `GrpcChannel` utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="2f71b-122">With the `Grpc.Net.Client` package, certificates are configured on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combining-channelcredentials-and-callcredentials"></a><span data-ttu-id="2f71b-123">Combinaison de ChannelCredentials et CallCredentials</span><span class="sxs-lookup"><span data-stu-id="2f71b-123">Combining ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="2f71b-124">Vous pouvez configurer votre serveur pour utiliser l’authentification par certificat et par jeton en appliquant les modifications de certificat au serveur Kestrel et en utilisant l’intergiciel de support JWT dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f71b-124">You can configure your server to use both certificate and token authentication by applying the certificate changes to the Kestrel server and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="2f71b-125">Pour fournir à la fois ChannelCredentials et CallCredentials sur le client, utilisez la méthode `ChannelCredentials.Create` pour appliquer les informations d’identification d’appel.</span><span class="sxs-lookup"><span data-stu-id="2f71b-125">To provide both ChannelCredentials and CallCredentials on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="2f71b-126">L’authentification par certificat doit encore être appliquée à l’aide de l’instance de <xref:System.Net.Http.HttpClient> : Si vous transmettez des arguments au constructeur `SslCredentials`, le code client interne lève une exception.</span><span class="sxs-lookup"><span data-stu-id="2f71b-126">Certificate authentication still needs to be applied using the <xref:System.Net.Http.HttpClient> instance: if you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="2f71b-127">Le paramètre `SslCredentials` est inclus uniquement dans la méthode `Create` du package `Grpc.Net.Client` pour assurer la compatibilité avec le package `Grpc.Core`.</span><span class="sxs-lookup"><span data-stu-id="2f71b-127">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="2f71b-128">Vous pouvez utiliser la méthode `ChannelCredentials.Create` pour un client sans authentification par certificat, afin de passer des informations d’identification de jeton à chaque appel effectué sur le canal.</span><span class="sxs-lookup"><span data-stu-id="2f71b-128">You can use the `ChannelCredentials.Create` method for a client without certificate authentication, as a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="2f71b-129">Une version de l' [exemple d’application GRPC FullStockTicker avec l’authentification par certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="2f71b-129">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f71b-130">[Précédent](call-credentials.md)
>[Suivant](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="2f71b-130">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
