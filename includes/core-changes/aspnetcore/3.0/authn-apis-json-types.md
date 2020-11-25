---
ms.openlocfilehash: 9bdfcca2fd03e24a636be3340f5057dc3f39358e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032494"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Authentification : Newtonsoft.Jssur les types remplacés

Dans ASP.NET Core 3,0, `Newtonsoft.Json` les types utilisés dans les API d’authentification ont été remplacés par des `System.Text.Json` types. Sauf dans les cas suivants, l’utilisation de base des packages d’authentification reste inchangée :

* Classes dérivées des fournisseurs OAuth, telles que celles de l’exemple [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Implémentations de manipulation de revendication avancées.

Pour plus d’informations, consultez [dotnet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105). Pour plus d’informations, consultez [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Pour les implémentations OAuth dérivées, la modification la plus courante consiste à remplacer `JObject.Parse` par `JsonDocument.Parse` dans la `CreateTicketAsync` substitution, comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). L'objet `JsonDocument` implémente l'objet `IDisposable`.

La liste suivante présente les modifications connues :

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)` . Toutes les implémentations dérivées de `ClaimAction` sont affectées de la même façon.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> a eu un ancien constructeur supprimé et l’autre remplacé `JObject` par `JsonElement` . La `User` propriété et la `RunClaimActions` méthode ont été mises à jour pour correspondre.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> accepte désormais un paramètre de type `JsonDocument` au lieu de `JObject` . La `Response` propriété a été mise à jour pour correspondre. `OAuthTokenResponse` est désormais jetable et sera supprimé par `OAuthHandler` . Les implémentations OAuth dérivées `ExchangeCodeAsync` qui remplacent n’ont pas besoin de supprimer le `JsonDocument` ou `OAuthTokenResponse` .
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> modification de `JObject` en `JsonDocument` .
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> modification de `JObject` en `JsonElement` .
- Le dernier paramètre de [TwitterHandler. CreateTicketAsync (ClaimsIdentity, AuthenticationProperties, AccessToken, JObject)](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) est passé de `JObject` à `JsonElement` . La méthode de remplacement est <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType> .

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
