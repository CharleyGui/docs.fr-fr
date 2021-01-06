---
title: Appeler les informations d’identification-gRPC pour les développeurs WCF
description: Comment implémenter et utiliser les informations d’identification d’appel gRPC dans ASP.NET Core 3,0.
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938440"
---
# <a name="call-credentials"></a><span data-ttu-id="e1cb9-103">Informations d’identification de l’appel</span><span class="sxs-lookup"><span data-stu-id="e1cb9-103">Call credentials</span></span>

<span data-ttu-id="e1cb9-104">Les informations d’identification d’appel sont toutes basées sur un jeton passé dans les métadonnées avec chaque demande.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="e1cb9-105">Un certificat de fournisseur d'identité WS-Federation</span><span class="sxs-lookup"><span data-stu-id="e1cb9-105">WS-Federation</span></span>

<span data-ttu-id="e1cb9-106">ASP.NET Core prend en charge WS-Federation à l’aide du package NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="e1cb9-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="e1cb9-107">WS-Federation est l’alternative la plus proche disponible à l’authentification Windows, qui n’est pas prise en charge sur HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="e1cb9-108">Les utilisateurs sont authentifiés à l’aide de Services ADFS (AD FS), qui fournit un jeton qui peut être utilisé pour s’authentifier auprès d’ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="e1cb9-109">Pour plus d’informations sur la prise en main de cette méthode d’authentification, consultez [authentifier les utilisateurs avec WS-Federation dans ASP.net Core](/aspnet/core/security/authentication/ws-federation).</span><span class="sxs-lookup"><span data-stu-id="e1cb9-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="e1cb9-110">Jetons du porteur JWT</span><span class="sxs-lookup"><span data-stu-id="e1cb9-110">JWT Bearer tokens</span></span>

<span data-ttu-id="e1cb9-111">La norme [JSON Web Token](https://jwt.io) (JWT) offre un moyen d’encoder des informations sur un utilisateur et leurs revendications dans une chaîne encodée.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="e1cb9-112">Il fournit également un moyen de signer ce jeton, afin que le consommateur puisse vérifier l’intégrité du jeton à l’aide du chiffrement à clé publique.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="e1cb9-113">Vous pouvez utiliser différents services, tels que IdentityServer4, pour authentifier les utilisateurs et générer des jetons OpenID Connect (OIDC) à utiliser avec les API gRPC et HTTP.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="e1cb9-114">ASP.NET Core 5,0 peut gérer jetons JWT à l’aide du package du porteur JWT.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-114">ASP.NET Core 5.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="e1cb9-115">La configuration est exactement la même pour une application gRPC que pour une application MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="e1cb9-116">Ici, nous allons nous concentrer sur les jetons de porteur JWT, car ils sont plus faciles à développer avec WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="e1cb9-117">Ajouter l’authentification et l’autorisation au serveur</span><span class="sxs-lookup"><span data-stu-id="e1cb9-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="e1cb9-118">Le package du porteur JWT n’est pas inclus dans ASP.NET Core 5,0 par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-118">The JWT Bearer package isn't included in ASP.NET Core 5.0 by default.</span></span> <span data-ttu-id="e1cb9-119">Installez le package NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="e1cb9-120">Ajoutez le service d’authentification dans la classe Startup et configurez le gestionnaire du porteur JWT :</span><span class="sxs-lookup"><span data-stu-id="e1cb9-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

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

<span data-ttu-id="e1cb9-121">La `IssuerSigningKey` propriété requiert une implémentation de `Microsoft.IdentityModels.Tokens.SecurityKey` avec les données de chiffrement nécessaires pour valider les jetons signés.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="e1cb9-122">Stockez ce jeton en toute sécurité dans un *serveur de secrets*, comme Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="e1cb9-123">Ensuite, ajoutez le service d’autorisation, qui contrôle l’accès au système :</span><span class="sxs-lookup"><span data-stu-id="e1cb9-123">Next, add the Authorization service, which controls access to the system:</span></span>

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
> <span data-ttu-id="e1cb9-124">L’authentification et l’autorisation sont deux étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="e1cb9-125">Vous utilisez l’authentification pour déterminer l’identité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="e1cb9-126">Vous utilisez l’autorisation pour décider si cet utilisateur est autorisé à accéder aux différentes parties du système.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="e1cb9-127">Ajoutez maintenant l’intergiciel d’authentification et d’autorisation au pipeline ASP.NET Core dans la `Configure` méthode :</span><span class="sxs-lookup"><span data-stu-id="e1cb9-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

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

<span data-ttu-id="e1cb9-128">Enfin, appliquez l' `[Authorize]` attribut à tous les services ou méthodes à sécuriser et utilisez la `User` propriété du sous-jacent `HttpContext` pour vérifier les autorisations.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

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

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="e1cb9-129">Fournir les informations d’identification de l’appel dans l’application cliente</span><span class="sxs-lookup"><span data-stu-id="e1cb9-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="e1cb9-130">Une fois que vous avez obtenu un jeton JWT à partir d’un serveur d’identité, vous pouvez l’utiliser pour authentifier les appels gRPC à partir du client en l’ajoutant comme en-tête de métadonnées à l’appel, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e1cb9-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

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

<span data-ttu-id="e1cb9-131">Maintenant, vous avez sécurisé votre service gRPC en utilisant des jetons de porteur JWT comme informations d’identification d’appel.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="e1cb9-132">Une version de l' [exemple d’application gRPC portefeuille avec l’authentification et l’autorisation ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) se trouve sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="e1cb9-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e1cb9-133">[Précédent](security.md) 
> [Suivant](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="e1cb9-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
