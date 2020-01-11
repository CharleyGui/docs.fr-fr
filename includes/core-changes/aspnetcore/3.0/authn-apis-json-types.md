---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901946"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="37107-101">Authentification : types Newtonsoft. JSON remplacés</span><span class="sxs-lookup"><span data-stu-id="37107-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="37107-102">Dans ASP.NET Core 3,0, les types de `Newtonsoft.Json` utilisés dans les API d’authentification ont été remplacés par des types de `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="37107-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="37107-103">Sauf dans les cas suivants, l’utilisation de base des packages d’authentification reste inchangée :</span><span class="sxs-lookup"><span data-stu-id="37107-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="37107-104">Classes dérivées des fournisseurs OAuth, telles que celles de l’exemple [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="37107-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="37107-105">Implémentations de manipulation de revendication avancées.</span><span class="sxs-lookup"><span data-stu-id="37107-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="37107-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="37107-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="37107-107">Pour plus d’informations, consultez [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="37107-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="37107-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="37107-108">Version introduced</span></span>

<span data-ttu-id="37107-109">3.0</span><span class="sxs-lookup"><span data-stu-id="37107-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37107-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="37107-110">Recommended action</span></span>

<span data-ttu-id="37107-111">Pour les implémentations OAuth dérivées, la modification la plus courante consiste à remplacer `JObject.Parse` par `JsonDocument.Parse` dans le `CreateTicketAsync` remplacement comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="37107-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="37107-112">L'objet `JsonDocument` implémente l'objet `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="37107-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="37107-113">La liste suivante présente les modifications connues :</span><span class="sxs-lookup"><span data-stu-id="37107-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="37107-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="37107-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="37107-115">Toutes les implémentations dérivées de `ClaimAction` sont affectées de la même façon.</span><span class="sxs-lookup"><span data-stu-id="37107-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="37107-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="37107-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="37107-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="37107-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="37107-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> a eu un ancien constructeur supprimé et l’autre `JObject` remplacé par `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="37107-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="37107-119">La propriété `User` et la méthode `RunClaimActions` ont été mises à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="37107-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="37107-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> accepte désormais un paramètre de type `JsonDocument` au lieu de `JObject`.</span><span class="sxs-lookup"><span data-stu-id="37107-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="37107-121">La propriété `Response` a été mise à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="37107-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="37107-122">`OAuthTokenResponse` est désormais jetable et sera supprimée par `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="37107-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="37107-123">Les implémentations OAuth dérivées substituent `ExchangeCodeAsync` n’ont pas besoin de supprimer le `JsonDocument` ou `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="37107-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="37107-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> modifié de `JObject` en `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="37107-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="37107-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> modifié de `JObject` en `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="37107-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="37107-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> a été remplacé par l’acceptation des `JObject` à `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="37107-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="37107-127">Catégorie</span><span class="sxs-lookup"><span data-stu-id="37107-127">Category</span></span>

<span data-ttu-id="37107-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37107-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37107-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="37107-129">Affected APIs</span></span>

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
