---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394143"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Authentification : GoogleMD déprécié et remplacé

Google commence à [fermer](https://developers.google.com/+/api-shutdown) Googlemd Connect-in pour les applications dès le 28 janvier 2019.

#### <a name="change-description"></a>Description de la modification

ASP.NET 4.x et ASP.NET Core utilisent les API De connexion Google POUR authentifier les utilisateurs de comptes Google dans les applications Web. Les forfaits NuGet concernés sont [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pour ASP.NET Core et [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pour `Microsoft.Owin` avec ASP.NET Web Forms et MVC.

Les API de remplacement de Google utilisent une source et un format de données différents. Les mesures d’atténuation et les solutions fournies ci-dessous tiennent compte des changements structurels. Les applications doivent vérifier que les données elles-mêmes satisfont toujours à leurs exigences. Par exemple, les noms, adresses e-mail, liens de profil et photos de profil peuvent fournir des valeurs subtilement différentes de ce qu’auparavant.

#### <a name="version-introduced"></a>Version introduite

Toutes les versions. Ce changement est externe à ASP.NET Core.

#### <a name="recommended-action"></a>Action recommandée

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin avec ASP.NET Web Forms et MVC

Pour `Microsoft.Owin` 3.1.0 et plus tard, une atténuation temporaire est décrite [ici](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635). Les applications doivent effectuer des tests avec l’atténuation pour vérifier les changements dans le format de données. Il est prévu `Microsoft.Owin` de libérer 4.0.1 avec un correctif. Les applications utilisant n’importe quelle version précédente doivent mettre à jour à la version 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

L’atténuation [d’Owin avec ASP.NET Web Forms et MVC](#owin-with-aspnet-web-forms-and-mvc) peut être adaptée à ASP.NET Core 1.x. Les correctifs de paquets NuGet ne sont pas prévus parce que 1.x a atteint le statut [de fin de vie.](https://dotnet.microsoft.com/platform/support-policy)

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2.x

Pour `Microsoft.AspNetCore.Authentication.Google` la version 2.x, `AddGoogle` remplacez votre appel existant `Startup.ConfigureServices` avec le code suivant :

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

Les patchs 2.1 et 2.2 de février ont incorporé la reconfiguration précédente comme le nouveau défaut. Aucun patch n’est prévu pour ASP.NET Core 2.0 depuis qu’il a atteint [la fin de la vie](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>ASP.NET Noyau 3.0

L’atténuation donnée pour ASP.NET Core 2.x peut également être utilisée pour ASP.NET Core 3.0. Dans les aperçus futurs de `Microsoft.AspNetCore.Authentication.Google` 3.0, le paquet peut être supprimé. Les utilisateurs seraient `Microsoft.AspNetCore.Authentication.OpenIdConnect` dirigés vers la place. Le code suivant montre `AddGoogle` `AddOpenIdConnect` comment `Startup.ConfigureServices`remplacer par in . Ce remplacement peut être utilisé avec ASP.NET Core 2.0 et plus tard et peut être adapté pour ASP.NET Core 1.x au besoin.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
