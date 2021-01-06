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
# <a name="call-credentials"></a>Informations d’identification de l’appel

Les informations d’identification d’appel sont toutes basées sur un jeton passé dans les métadonnées avec chaque demande.

## <a name="ws-federation"></a>Un certificat de fournisseur d'identité WS-Federation

ASP.NET Core prend en charge WS-Federation à l’aide du package NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) . WS-Federation est l’alternative la plus proche disponible à l’authentification Windows, qui n’est pas prise en charge sur HTTP/2. Les utilisateurs sont authentifiés à l’aide de Services ADFS (AD FS), qui fournit un jeton qui peut être utilisé pour s’authentifier auprès d’ASP.NET Core.

Pour plus d’informations sur la prise en main de cette méthode d’authentification, consultez [authentifier les utilisateurs avec WS-Federation dans ASP.net Core](/aspnet/core/security/authentication/ws-federation).

## <a name="jwt-bearer-tokens"></a>Jetons du porteur JWT

La norme [JSON Web Token](https://jwt.io) (JWT) offre un moyen d’encoder des informations sur un utilisateur et leurs revendications dans une chaîne encodée. Il fournit également un moyen de signer ce jeton, afin que le consommateur puisse vérifier l’intégrité du jeton à l’aide du chiffrement à clé publique. Vous pouvez utiliser différents services, tels que IdentityServer4, pour authentifier les utilisateurs et générer des jetons OpenID Connect (OIDC) à utiliser avec les API gRPC et HTTP.

ASP.NET Core 5,0 peut gérer jetons JWT à l’aide du package du porteur JWT. La configuration est exactement la même pour une application gRPC que pour une application MVC ASP.NET Core. Ici, nous allons nous concentrer sur les jetons de porteur JWT, car ils sont plus faciles à développer avec WS-Federation.

## <a name="add-authentication-and-authorization-to-the-server"></a>Ajouter l’authentification et l’autorisation au serveur

Le package du porteur JWT n’est pas inclus dans ASP.NET Core 5,0 par défaut. Installez le package NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) dans votre application.

Ajoutez le service d’authentification dans la classe Startup et configurez le gestionnaire du porteur JWT :

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

La `IssuerSigningKey` propriété requiert une implémentation de `Microsoft.IdentityModels.Tokens.SecurityKey` avec les données de chiffrement nécessaires pour valider les jetons signés. Stockez ce jeton en toute sécurité dans un *serveur de secrets*, comme Azure Key Vault.

Ensuite, ajoutez le service d’autorisation, qui contrôle l’accès au système :

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
> L’authentification et l’autorisation sont deux étapes distinctes. Vous utilisez l’authentification pour déterminer l’identité de l’utilisateur. Vous utilisez l’autorisation pour décider si cet utilisateur est autorisé à accéder aux différentes parties du système.

Ajoutez maintenant l’intergiciel d’authentification et d’autorisation au pipeline ASP.NET Core dans la `Configure` méthode :

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

Enfin, appliquez l' `[Authorize]` attribut à tous les services ou méthodes à sécuriser et utilisez la `User` propriété du sous-jacent `HttpContext` pour vérifier les autorisations.

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

## <a name="provide-call-credentials-in-the-client-application"></a>Fournir les informations d’identification de l’appel dans l’application cliente

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

Maintenant, vous avez sécurisé votre service gRPC en utilisant des jetons de porteur JWT comme informations d’identification d’appel. Une version de l' [exemple d’application gRPC portefeuille avec l’authentification et l’autorisation ajoutée](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) se trouve sur GitHub.

>[!div class="step-by-step"]
>[Précédent](security.md) 
> [Suivant](channel-credentials.md)
