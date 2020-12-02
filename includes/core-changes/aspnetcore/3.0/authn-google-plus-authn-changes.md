---
ms.openlocfilehash: 14d80f25c34465caa6dec10e5704fe0a3cbccc71
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477598"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Authentification : Google + déconseillé et remplacé

Google commence à arrêter Google + Connect pour les applications dès [le](https://developers.google.com/+/api-shutdown) 28 janvier 2019.

#### <a name="change-description"></a>Description de la modification

ASP.NET 4. x et ASP.NET Core utilisent les API de connexion Google + pour authentifier les utilisateurs de compte Google dans Web Apps. Les packages NuGet affectés sont [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pour ASP.net Core et [Microsoft. Owin. Security. google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pour `Microsoft.Owin` avec ASP.NET Web Forms et MVC.

Les API de remplacement de Google utilisent une source de données et un format différents. Les solutions de contournement et les solutions proposées ci-dessous comportent des modifications structurelles. Les applications doivent vérifier que les données elles-mêmes satisfont toujours à leurs exigences. Par exemple, les noms, les adresses de messagerie, les liens de profil et les photos de profil peuvent fournir des valeurs légèrement différentes de celles antérieures à.

#### <a name="version-introduced"></a>Version introduite

Toutes les versions. Cette modification est externe à ASP.NET Core.

#### <a name="recommended-action"></a>Action recommandée

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin avec ASP.NET Web Forms et MVC

Pour `Microsoft.Owin` 3.1.0 et versions ultérieures, une atténuation temporaire est décrite [ici](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635). Les applications doivent effectuer des tests avec l’atténuation pour vérifier les modifications apportées au format de données. Il est prévu de publier `Microsoft.Owin` 4.0.1 avec un correctif. Les applications qui utilisent une version antérieure doivent être mises à jour vers la version 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

L’atténuation dans [Owin avec ASP.NET Web Forms et MVC](#owin-with-aspnet-web-forms-and-mvc) peut être adaptée à ASP.net Core 1. x. Les correctifs de package NuGet ne sont pas planifiés, car 1. x a atteint l’état [de fin de vie](https://dotnet.microsoft.com/platform/support-policy) .

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2.x

Pour `Microsoft.AspNetCore.Authentication.Google` la version 2. x, remplacez votre appel existant à `AddGoogle` dans `Startup.ConfigureServices` par le code suivant :

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

Les correctifs de février 2,1 et 2,2 incorporaient la reconfiguration précédente comme nouvelle valeur par défaut. Aucun correctif n’est prévu pour ASP.NET Core 2,0, car il a atteint la [fin de vie](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>ASP.NET Core 3,0

L’atténuation donnée pour ASP.NET Core 2. x peut également être utilisée pour ASP.NET Core 3,0. Dans les prochaines versions préliminaires de 3,0, le `Microsoft.AspNetCore.Authentication.Google` package peut être supprimé. Les utilisateurs sont dirigés vers à la `Microsoft.AspNetCore.Authentication.OpenIdConnect` place. Le code suivant montre comment remplacer `AddGoogle` par `AddOpenIdConnect` dans `Startup.ConfigureServices` . Ce remplacement peut être utilisé avec ASP.NET Core 2,0 et versions ultérieures et peut être adapté pour ASP.NET Core 1. x si nécessaire.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/signin-oidc"
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
