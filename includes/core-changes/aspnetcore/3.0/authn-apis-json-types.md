---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393899"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Authentification : types Newtonsoft. JSON remplacés

Dans ASP.NET Core 3,0, les types `Newtonsoft.Json` utilisés dans les API d’authentification ont été remplacés par les types `System.Text.Json`. Sauf dans les cas suivants, l’utilisation de base des packages d’authentification reste inchangée :

* Classes dérivées des fournisseurs OAuth, telles que celles de l’exemple [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Implémentations de manipulation de revendication avancées.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105). Pour plus d’informations, consultez [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="recommended-action"></a>Action recommandée

Pour les implémentations OAuth dérivées, la modification la plus courante consiste à remplacer `JObject.Parse` par `JsonDocument.Parse` dans la substitution `CreateTicketAsync`, comme indiqué [ici](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). L'objet `JsonDocument` implémente l'objet `IDisposable`.

La liste suivante présente les modifications connues :

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Toutes les implémentations dérivées de `ClaimAction` sont affectées de la même façon.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> a eu un ancien constructeur supprimé et l’autre a remplacé `JObject` par `JsonElement`. La propriété `User` et la méthode `RunClaimActions` ont été mises à jour pour correspondre.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> accepte désormais un paramètre de type `JsonDocument` au lieu de `JObject`. La propriété `Response` a été mise à jour pour correspondre. `OAuthTokenResponse` est désormais jetable et sera supprimé par `OAuthHandler`. Les implémentations OAuth dérivées substituent `ExchangeCodeAsync` n’ont pas besoin de supprimer la `JsonDocument` ou `OAuthTokenResponse`.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> a été modifié de `JObject` à `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> a été modifié de `JObject` à `JsonElement`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> a été remplacé par l’acceptation de `JObject` à `JsonElement`.

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
