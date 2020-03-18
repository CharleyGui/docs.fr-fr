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
# <a name="channel-credentials"></a><span data-ttu-id="f1511-103">Informations d’identification de la chaîne</span><span class="sxs-lookup"><span data-stu-id="f1511-103">Channel credentials</span></span>

<span data-ttu-id="f1511-104">Comme son nom l’indique, les informations d’identification des canaux sont fixées au canal gRPC sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="f1511-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="f1511-105">La forme standard d’informations d’identification des canaux utilise l’authentification des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="f1511-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="f1511-106">Dans ce processus, le client fournit un certificat TLS lorsqu’il effectue la connexion, puis le serveur vérifie cela avant de permettre tout appel à faire.</span><span class="sxs-lookup"><span data-stu-id="f1511-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="f1511-107">Vous pouvez combiner les informations d’identification des canaux avec les informations d’identification des appels afin d’assurer une sécurité complète pour un service gRPC.</span><span class="sxs-lookup"><span data-stu-id="f1511-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="f1511-108">Les informations d’identification du canal prouvent que l’application client est autorisée à accéder au service, et les informations d’identification de l’appel fournissent des informations sur la personne qui utilise l’application client.</span><span class="sxs-lookup"><span data-stu-id="f1511-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="f1511-109">L’authentification des certificats clients fonctionne pour gRPC de la même façon qu’elle fonctionne pour ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1511-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="f1511-110">Pour plus d’informations, voir [l’authentification du certificat Configure dans ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="f1511-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="f1511-111">Pour le développement, vous pouvez utiliser un certificat auto-signé, mais pour la production, vous devez utiliser un certificat HTTPS approprié signé par une autorité de confiance.</span><span class="sxs-lookup"><span data-stu-id="f1511-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="f1511-112">Ajouter l’authentification du certificat au serveur</span><span class="sxs-lookup"><span data-stu-id="f1511-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="f1511-113">Configurer l’authentification des certificats à la fois au niveau de l’hôte (par exemple, sur le serveur Kestrel), et dans le pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1511-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="f1511-114">Configurer la validation du certificat sur Kestrel</span><span class="sxs-lookup"><span data-stu-id="f1511-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="f1511-115">Vous pouvez configurer Kestrel (le serveur CORE HTTP ASP.NET) pour exiger un certificat client, et en option pour effectuer une validation du certificat fourni, avant d’accepter les connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="f1511-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="f1511-116">Vous faites cela `CreateWebHostBuilder` dans `Program` la méthode de `Startup`la classe, plutôt que dans .</span><span class="sxs-lookup"><span data-stu-id="f1511-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="f1511-117">Le `ClientCertificateMode.RequireCertificate` paramètre amène Kestrel à rejeter immédiatement toute demande de connexion qui ne fournit pas de certificat client, mais ce paramètre en soi ne validera pas un certificat qui est fourni.</span><span class="sxs-lookup"><span data-stu-id="f1511-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="f1511-118">Ajoutez `ClientCertificateValidation` le rappel pour permettre à Kestrel de valider le certificat client au moment où la connexion est effectuée, avant que le pipeline ASP.NET Core ne soit engagé.</span><span class="sxs-lookup"><span data-stu-id="f1511-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="f1511-119">(Dans ce cas, le rappel garantit qu’il a été délivré par la même *autorité de certificat* que le certificat serveur.)</span><span class="sxs-lookup"><span data-stu-id="f1511-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="f1511-120">Ajouter ASP.NET authentification du certificat de base</span><span class="sxs-lookup"><span data-stu-id="f1511-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="f1511-121">Le package [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet fournit l’authentification des certificats.</span><span class="sxs-lookup"><span data-stu-id="f1511-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="f1511-122">Ajoutez le service d’authentification du certificat dans la `ConfigureServices` méthode, et `Configure` ajoutez l’authentification et l’autorisation au pipeline ASP.NET Core dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="f1511-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="f1511-123">Fournir les informations d’identification du canal dans l’application client</span><span class="sxs-lookup"><span data-stu-id="f1511-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="f1511-124">Avec `Grpc.Net.Client` le paquet, vous configurez des certificats sur une <xref:System.Net.Http.HttpClient> instance qui est fournie à l’utilisé `GrpcChannel` pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="f1511-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="f1511-125">Combinez ChannelCredentials et CallCredentials</span><span class="sxs-lookup"><span data-stu-id="f1511-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="f1511-126">Vous pouvez configurer votre serveur pour utiliser à la fois l’authentification du certificat et du jeton.</span><span class="sxs-lookup"><span data-stu-id="f1511-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="f1511-127">Faites-le en appliquant les modifications de certificat au serveur Kestrel, et en utilisant le middleware porte-moyens JWT dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1511-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="f1511-128">Pour fournir `ChannelCredentials` `CallCredentials` à la fois `ChannelCredentials.Create` et sur le client, utilisez la méthode pour appliquer les informations d’identification d’appel.</span><span class="sxs-lookup"><span data-stu-id="f1511-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="f1511-129">Vous devez toujours appliquer l’authentification des certificats en utilisant l’instance. <xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="f1511-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="f1511-130">Si vous transmettez des `SslCredentials` arguments au constructeur, le code client interne fait une exception.</span><span class="sxs-lookup"><span data-stu-id="f1511-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="f1511-131">Le `SslCredentials` paramètre n’est inclus que dans la `Grpc.Net.Client` méthode du `Create` paquet pour maintenir la compatibilité avec le `Grpc.Core` paquet.</span><span class="sxs-lookup"><span data-stu-id="f1511-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="f1511-132">Vous pouvez `ChannelCredentials.Create` utiliser la méthode pour un client sans authentification de certificat.</span><span class="sxs-lookup"><span data-stu-id="f1511-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="f1511-133">Il s’agit d’une façon utile de passer des informations d’identification symbolique avec chaque appel fait sur le canal.</span><span class="sxs-lookup"><span data-stu-id="f1511-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="f1511-134">Une version de la [demande gRPC échantillon FullStockTicker avec l’authentification de certificat ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) est sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1511-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1511-135">[Suivant précédent](call-credentials.md)
>[Next](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="f1511-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
