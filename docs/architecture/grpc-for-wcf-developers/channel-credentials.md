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
# <a name="channel-credentials"></a><span data-ttu-id="29aa3-103">Informations d’identification de la chaîne</span><span class="sxs-lookup"><span data-stu-id="29aa3-103">Channel credentials</span></span>

<span data-ttu-id="29aa3-104">Comme son nom l’indique, les informations d’identification du canal sont attachées au canal gRPC sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="29aa3-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="29aa3-105">Le formulaire standard des informations d’identification de canal utilise l’authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="29aa3-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="29aa3-106">Dans ce processus, le client fournit un certificat TLS lorsqu’il effectue la connexion, puis le serveur vérifie ce certificat avant d’autoriser les appels à effectuer.</span><span class="sxs-lookup"><span data-stu-id="29aa3-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this certificate before allowing any calls to be made.</span></span>

<span data-ttu-id="29aa3-107">Vous pouvez combiner les informations d’identification de canal avec les informations d’identification d’appel pour offrir une sécurité complète pour un service gRPC.</span><span class="sxs-lookup"><span data-stu-id="29aa3-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="29aa3-108">Les informations d’identification du canal prouvent que l’application cliente est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="29aa3-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="29aa3-109">L’authentification par certificat client fonctionne pour gRPC de la même façon que pour les ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="29aa3-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="29aa3-110">Pour plus d’informations, consultez [configurer l’authentification par certificat dans ASP.net Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="29aa3-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="29aa3-111">À des fins de développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPs approprié signé par une autorité de confiance.</span><span class="sxs-lookup"><span data-stu-id="29aa3-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="29aa3-112">Ajouter l’authentification par certificat au serveur</span><span class="sxs-lookup"><span data-stu-id="29aa3-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="29aa3-113">Configurez l’authentification par certificat au niveau de l’hôte (par exemple, sur le serveur Kestrel) et dans le pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="29aa3-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="29aa3-114">Configurer la validation de certificat sur Kestrel</span><span class="sxs-lookup"><span data-stu-id="29aa3-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="29aa3-115">Vous pouvez configurer Kestrel (serveur HTTP ASP.NET Core) pour exiger un certificat client et éventuellement effectuer une validation du certificat fourni, avant d’accepter les connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="29aa3-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="29aa3-116">Vous spécifiez cette configuration dans la `CreateWebHostBuilder` méthode de la `Program` classe, plutôt que dans `Startup` .</span><span class="sxs-lookup"><span data-stu-id="29aa3-116">You specify this configuration in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="29aa3-117">Le `ClientCertificateMode.RequireCertificate` paramètre oblige Kestrel à rejeter immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ce paramètre ne valide pas un certificat fourni.</span><span class="sxs-lookup"><span data-stu-id="29aa3-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="29aa3-118">Ajoutez le `ClientCertificateValidation` rappel pour permettre à Kestrel de valider le certificat client au point où la connexion est établie, avant que le pipeline ASP.net Core soit engagé.</span><span class="sxs-lookup"><span data-stu-id="29aa3-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="29aa3-119">(Dans ce cas, le rappel s’assure qu’il a été émis par la même *autorité de certification* que le certificat de serveur.)</span><span class="sxs-lookup"><span data-stu-id="29aa3-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="29aa3-120">Ajouter ASP.NET Core l’authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="29aa3-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="29aa3-121">Le package NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) fournit l’authentification par certificat.</span><span class="sxs-lookup"><span data-stu-id="29aa3-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="29aa3-122">Ajoutez le service d’authentification de certificat dans la `ConfigureServices` méthode et ajoutez l’authentification et l’autorisation au pipeline ASP.net core dans la `Configure` méthode.</span><span class="sxs-lookup"><span data-stu-id="29aa3-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="29aa3-123">Fournir des informations d’identification de canal dans l’application cliente</span><span class="sxs-lookup"><span data-stu-id="29aa3-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="29aa3-124">Avec le `Grpc.Net.Client` package, vous configurez des certificats sur une <xref:System.Net.Http.HttpClient> instance de qui est fournie au `GrpcChannel` utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="29aa3-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="29aa3-125">Combiner ChannelCredentials et CallCredentials</span><span class="sxs-lookup"><span data-stu-id="29aa3-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="29aa3-126">Vous pouvez configurer votre serveur pour qu’il utilise à la fois l’authentification par certificat et le jeton.</span><span class="sxs-lookup"><span data-stu-id="29aa3-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="29aa3-127">Pour ce faire, appliquez les modifications du certificat au serveur Kestrel et utilisez l’intergiciel (middleware) du porteur JWT dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="29aa3-127">To do this, apply the certificate changes to the Kestrel server, and use the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="29aa3-128">Pour fournir à `ChannelCredentials` la fois et `CallCredentials` sur le client, utilisez la `ChannelCredentials.Create` méthode pour appliquer les informations d’identification de l’appel.</span><span class="sxs-lookup"><span data-stu-id="29aa3-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="29aa3-129">Vous devez toujours appliquer l’authentification par certificat à l’aide de l' <xref:System.Net.Http.HttpClient> instance.</span><span class="sxs-lookup"><span data-stu-id="29aa3-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="29aa3-130">Si vous transmettez des arguments au `SslCredentials` constructeur, le code client interne lève une exception.</span><span class="sxs-lookup"><span data-stu-id="29aa3-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="29aa3-131">Le `SslCredentials` paramètre est inclus uniquement dans la `Grpc.Net.Client` méthode du package `Create` pour assurer la compatibilité avec le `Grpc.Core` Package.</span><span class="sxs-lookup"><span data-stu-id="29aa3-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="29aa3-132">Vous pouvez utiliser la `ChannelCredentials.Create` méthode pour un client sans authentification par certificat.</span><span class="sxs-lookup"><span data-stu-id="29aa3-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="29aa3-133">Il s’agit d’un moyen utile pour passer des informations d’identification de jeton avec chaque appel effectué sur le canal.</span><span class="sxs-lookup"><span data-stu-id="29aa3-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="29aa3-134">Une version de l' [exemple d’application GRPC FullStockTicker avec l’authentification par certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="29aa3-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="29aa3-135">[Précédent](call-credentials.md) 
> [Suivant](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="29aa3-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
