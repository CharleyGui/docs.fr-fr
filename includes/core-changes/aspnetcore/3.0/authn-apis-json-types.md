---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901946"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Authentification: Newtonsoft.Json types remplacés

Dans ASP.NET Core 3.0, `Newtonsoft.Json` les types utilisés dans les `System.Text.Json` API d’authentification ont été remplacés par des types. À l’exception des cas suivants, l’utilisation de base des paquets d’authentification n’est pas affectée :

* Classes dérivées des fournisseurs OAuth, tels que ceux de [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Implémentations avancées de manipulation de réclamation.

Pour plus d’informations, voir [dotnet/aspnetcore 7105](https://github.com/dotnet/aspnetcore/pull/7105). Pour discussion, voir [dotnet/aspnetcore 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Pour les implémentations dérivées d’OAuth, le changement le plus courant est `JObject.Parse` de remplacer par `JsonDocument.Parse` dans la `CreateTicketAsync` dérogation comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). L'objet `JsonDocument` implémente l'objet `IDisposable`.

La liste suivante décrit les changements connus :

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Toutes les implémentations dérivées sont `ClaimAction` également touchées.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>a eu un vieux constructeur enlevé `JObject` et `JsonElement`l’autre remplacé par . La `User` propriété `RunClaimActions` et la méthode ont été mises à jour pour correspondre.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>accepte maintenant un paramètre de type `JsonDocument` au lieu de `JObject`. La `Response` propriété a été mise à jour pour correspondre. `OAuthTokenResponse`est maintenant jetable et `OAuthHandler`sera éliminé par . Les implémentations dérivées d’OAuth qui l’emportent `ExchangeCodeAsync` ne doivent pas disposer du `JsonDocument` ou `OAuthTokenResponse`.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>changé `JObject` de `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>changé `JObject` de `JsonElement`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>changé `JObject` d’accepter `JsonElement`à .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
