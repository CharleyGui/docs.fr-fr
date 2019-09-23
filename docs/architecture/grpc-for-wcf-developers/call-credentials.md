---
title: Appeler les informations d’identification-gRPC pour les développeurs WCF
description: Comment implémenter et utiliser les informations d’identification d’appel gRPC dans ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 483f540a0ed3849883c07cc70f0e3d45a6b121ad
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184595"
---
# <a name="call-credentials"></a><span data-ttu-id="53c29-103">Informations d’identification de l’appel</span><span class="sxs-lookup"><span data-stu-id="53c29-103">Call credentials</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="53c29-104">Les informations d’identification d’appel sont toutes basées sur un type de jeton passé dans les métadonnées avec chaque demande.</span><span class="sxs-lookup"><span data-stu-id="53c29-104">Call credentials are all based on some kind of token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="53c29-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="53c29-105">WS-Federation</span></span>

<span data-ttu-id="53c29-106">ASP.NET Core prend en charge WS-Federation à l’aide du package NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="53c29-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="53c29-107">WS-Federation est la alternative la plus proche disponible à l’authentification Windows, qui n’est pas prise en charge sur HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="53c29-107">WS-Federation is the closest available alternative to Windows Authentication, which is not supported over HTTP/2.</span></span> <span data-ttu-id="53c29-108">Les utilisateurs sont authentifiés à l’aide d’Services ADFS (ADFS), qui fournit un jeton qui peut être utilisé pour s’authentifier auprès de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="53c29-108">Users are authenticated using Active Directory Federation Services (ADFS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="53c29-109">Pour plus d’informations sur la prise en main de cette méthode d’authentification, consultez l’article [authentifier les utilisateurs avec WS-Federation dans ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="53c29-109">For more information on how to get started with this authentication method, see the [Authenticate users with WS-Federation in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) article.</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="53c29-110">Jetons du porteur JWT</span><span class="sxs-lookup"><span data-stu-id="53c29-110">JWT Bearer tokens</span></span>

<span data-ttu-id="53c29-111">Le [JSON Web Token](https://jwt.io) standard offre un moyen d’encoder des informations sur un utilisateur et leurs revendications dans une chaîne encodée, et de signer ce jeton de telle sorte que le consommateur puisse vérifier l’intégrité du jeton à l’aide du chiffrement à clé publique.</span><span class="sxs-lookup"><span data-stu-id="53c29-111">The [JSON Web Token](https://jwt.io) standard provides a way to encode information about a user and their claims in an encoded string, and to sign that token in such a way that the consumer can verify the integrity of the token using public key cryptography.</span></span> <span data-ttu-id="53c29-112">Vous pouvez utiliser différents services, tels que IdentityServer4, pour authentifier les utilisateurs et générer des jetons OpenID Connect (OIDC) à utiliser avec les API gRPC et HTTP.</span><span class="sxs-lookup"><span data-stu-id="53c29-112">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="53c29-113">ASP.NET Core 3,0 peut gérer des jetons Web JSON à l’aide du package du porteur JWT.</span><span class="sxs-lookup"><span data-stu-id="53c29-113">ASP.NET Core 3.0 can handle JSON Web Tokens using the JWT Bearer package.</span></span> <span data-ttu-id="53c29-114">La configuration est exactement la même pour une application gRPC en tant qu’application ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="53c29-114">The configuration is exactly the same for a gRPC application as an ASP.NET Core MVC application.</span></span>

<span data-ttu-id="53c29-115">Ce chapitre se concentre sur les jetons de porteur JWT, car ils sont plus faciles à développer avec WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="53c29-115">This chapter will focus on JWT Bearer tokens as they're easier to develop with than WS-Federation.</span></span>

## <a name="adding-authentication-and-authorization-to-the-server"></a><span data-ttu-id="53c29-116">Ajout de l’authentification et de l’autorisation au serveur</span><span class="sxs-lookup"><span data-stu-id="53c29-116">Adding authentication and authorization to the server</span></span>

<span data-ttu-id="53c29-117">Le package du porteur JWT n’est pas inclus dans ASP.NET Core 3,0 par défaut.</span><span class="sxs-lookup"><span data-stu-id="53c29-117">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="53c29-118">Installez le package NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) dans votre application.</span><span class="sxs-lookup"><span data-stu-id="53c29-118">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="53c29-119">Ajoutez le service d’authentification dans la classe Startup et configurez le gestionnaire du porteur JWT.</span><span class="sxs-lookup"><span data-stu-id="53c29-119">Add the Authentication service in the Startup class and configure the JWT Bearer handler.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="53c29-120">La `IssuerSigningKey` propriété requiert une implémentation de `Microsoft.IdentityModels.Tokens.SecurityKey` avec les données de chiffrement nécessaires pour valider les jetons signés.</span><span class="sxs-lookup"><span data-stu-id="53c29-120">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="53c29-121">Ce jeton doit être stocké en toute sécurité dans un *serveur de secrets* comme Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="53c29-121">This token should be stored securely in a *secrets server* like Azure KeyVault.</span></span>

<span data-ttu-id="53c29-122">Ajoutez ensuite le service d’autorisation, qui contrôle l’accès au système.</span><span class="sxs-lookup"><span data-stu-id="53c29-122">Next add the Authorization service, which controls access to the system.</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="53c29-123">L’authentification et l’autorisation sont deux étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="53c29-123">Authentication and Authorization are two separate steps.</span></span> <span data-ttu-id="53c29-124">L’authentification est utilisée pour déterminer l’identité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53c29-124">Authentication is used to determine the user's identity.</span></span> <span data-ttu-id="53c29-125">L’autorisation décide si cet utilisateur est autorisé à accéder aux différentes parties du système.</span><span class="sxs-lookup"><span data-stu-id="53c29-125">Authorization decides whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="53c29-126">Ajoutez maintenant l’intergiciel d’authentification et d’autorisation au pipeline ASP.net core dans `Configure` la méthode.</span><span class="sxs-lookup"><span data-stu-id="53c29-126">Now add the Authentication and Authorization middleware to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="53c29-127">Enfin, appliquez l' `[Authorize]` attribut à tous les services ou méthodes à sécuriser et utilisez la `User` propriété du sous- `HttpContext` jacent pour vérifier les autorisations.</span><span class="sxs-lookup"><span data-stu-id="53c29-127">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="providing-call-credentials-in-the-client-application"></a><span data-ttu-id="53c29-128">Fournir des informations d’identification d’appel dans l’application cliente</span><span class="sxs-lookup"><span data-stu-id="53c29-128">Providing call credentials in the client application</span></span>

<span data-ttu-id="53c29-129">Une fois que vous avez obtenu un jeton JWT à partir d’un serveur d’identité, vous pouvez l’utiliser pour authentifier les appels gRPC à partir du client en l’ajoutant comme en-tête de métadonnées à l’appel, comme suit :</span><span class="sxs-lookup"><span data-stu-id="53c29-129">Once you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="53c29-130">Maintenant, vous avez sécurisé votre service gRPC en utilisant des jetons de porteur JWT comme informations d’identification d’appel.</span><span class="sxs-lookup"><span data-stu-id="53c29-130">Now, you've secured your gRPC service using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="53c29-131">Une version de l' [exemple d’application GRPC portefeuille avec l’authentification et l’autorisation ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) se trouve sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="53c29-131">A version of the [Portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53c29-132">[Précédent](security.md)
>[Suivant](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="53c29-132">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
