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
# <a name="call-credentials"></a>Informations d’identification de l’appel

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les informations d’identification d’appel sont toutes basées sur un type de jeton passé dans les métadonnées avec chaque demande.

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core prend en charge WS-Federation à l’aide du package NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) . WS-Federation est la alternative la plus proche disponible à l’authentification Windows, qui n’est pas prise en charge sur HTTP/2. Les utilisateurs sont authentifiés à l’aide d’Services ADFS (ADFS), qui fournit un jeton qui peut être utilisé pour s’authentifier auprès de ASP.NET Core.

Pour plus d’informations sur la prise en main de cette méthode d’authentification, consultez l’article [authentifier les utilisateurs avec WS-Federation dans ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) .

## <a name="jwt-bearer-tokens"></a>Jetons du porteur JWT

Le [JSON Web Token](https://jwt.io) standard offre un moyen d’encoder des informations sur un utilisateur et leurs revendications dans une chaîne encodée, et de signer ce jeton de telle sorte que le consommateur puisse vérifier l’intégrité du jeton à l’aide du chiffrement à clé publique. Vous pouvez utiliser différents services, tels que IdentityServer4, pour authentifier les utilisateurs et générer des jetons OpenID Connect (OIDC) à utiliser avec les API gRPC et HTTP.

ASP.NET Core 3,0 peut gérer des jetons Web JSON à l’aide du package du porteur JWT. La configuration est exactement la même pour une application gRPC en tant qu’application ASP.NET Core MVC.

Ce chapitre se concentre sur les jetons de porteur JWT, car ils sont plus faciles à développer avec WS-Federation.

## <a name="adding-authentication-and-authorization-to-the-server"></a>Ajout de l’authentification et de l’autorisation au serveur

Le package du porteur JWT n’est pas inclus dans ASP.NET Core 3,0 par défaut. Installez le package NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) dans votre application.

Ajoutez le service d’authentification dans la classe Startup et configurez le gestionnaire du porteur JWT.

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

La `IssuerSigningKey` propriété requiert une implémentation de `Microsoft.IdentityModels.Tokens.SecurityKey` avec les données de chiffrement nécessaires pour valider les jetons signés. Ce jeton doit être stocké en toute sécurité dans un *serveur de secrets* comme Azure Key Vault.

Ajoutez ensuite le service d’autorisation, qui contrôle l’accès au système.

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
> L’authentification et l’autorisation sont deux étapes distinctes. L’authentification est utilisée pour déterminer l’identité de l’utilisateur. L’autorisation décide si cet utilisateur est autorisé à accéder aux différentes parties du système.

Ajoutez maintenant l’intergiciel d’authentification et d’autorisation au pipeline ASP.net core dans `Configure` la méthode.

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

Enfin, appliquez l' `[Authorize]` attribut à tous les services ou méthodes à sécuriser et utilisez la `User` propriété du sous- `HttpContext` jacent pour vérifier les autorisations.

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

## <a name="providing-call-credentials-in-the-client-application"></a>Fournir des informations d’identification d’appel dans l’application cliente

Une fois que vous avez obtenu un jeton JWT à partir d’un serveur d’identité, vous pouvez l’utiliser pour authentifier les appels gRPC à partir du client en l’ajoutant comme en-tête de métadonnées à l’appel, comme suit :

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

Maintenant, vous avez sécurisé votre service gRPC en utilisant des jetons de porteur JWT comme informations d’identification d’appel. Une version de l' [exemple d’application GRPC portefeuille avec l’authentification et l’autorisation ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) se trouve sur GitHub.

>[!div class="step-by-step"]
>[Précédent](security.md)
>[Suivant](channel-credentials.md)
