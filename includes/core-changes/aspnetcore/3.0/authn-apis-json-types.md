---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393899"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="95e20-101">Authentification : types Newtonsoft. JSON remplacés</span><span class="sxs-lookup"><span data-stu-id="95e20-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="95e20-102">Dans ASP.NET Core 3,0, les types `Newtonsoft.Json` utilisés dans les API d’authentification ont été remplacés par les types `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="95e20-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="95e20-103">Sauf dans les cas suivants, l’utilisation de base des packages d’authentification reste inchangée :</span><span class="sxs-lookup"><span data-stu-id="95e20-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="95e20-104">Classes dérivées des fournisseurs OAuth, telles que celles de l’exemple [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="95e20-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="95e20-105">Implémentations de manipulation de revendication avancées.</span><span class="sxs-lookup"><span data-stu-id="95e20-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="95e20-106">Pour plus d’informations, consultez [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="95e20-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="95e20-107">Pour plus d’informations, consultez [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="95e20-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="95e20-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="95e20-108">Version introduced</span></span>

<span data-ttu-id="95e20-109">3,0</span><span class="sxs-lookup"><span data-stu-id="95e20-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="95e20-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="95e20-110">Recommended action</span></span>

<span data-ttu-id="95e20-111">Pour les implémentations OAuth dérivées, la modification la plus courante consiste à remplacer `JObject.Parse` par `JsonDocument.Parse` dans la substitution `CreateTicketAsync`, comme indiqué [ici](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="95e20-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="95e20-112">L'objet `JsonDocument` implémente l'objet `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="95e20-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="95e20-113">La liste suivante présente les modifications connues :</span><span class="sxs-lookup"><span data-stu-id="95e20-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="95e20-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="95e20-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="95e20-115">Toutes les implémentations dérivées de `ClaimAction` sont affectées de la même façon.</span><span class="sxs-lookup"><span data-stu-id="95e20-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="95e20-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="95e20-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="95e20-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="95e20-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="95e20-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> a eu un ancien constructeur supprimé et l’autre a remplacé `JObject` par `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="95e20-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="95e20-119">La propriété `User` et la méthode `RunClaimActions` ont été mises à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="95e20-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="95e20-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> accepte désormais un paramètre de type `JsonDocument` au lieu de `JObject`.</span><span class="sxs-lookup"><span data-stu-id="95e20-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="95e20-121">La propriété `Response` a été mise à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="95e20-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="95e20-122">`OAuthTokenResponse` est désormais jetable et sera supprimé par `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="95e20-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="95e20-123">Les implémentations OAuth dérivées substituent `ExchangeCodeAsync` n’ont pas besoin de supprimer la `JsonDocument` ou `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="95e20-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="95e20-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> a été modifié de `JObject` à `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="95e20-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="95e20-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> a été modifié de `JObject` à `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="95e20-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="95e20-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> a été remplacé par l’acceptation de `JObject` à `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="95e20-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="95e20-127">Category</span><span class="sxs-lookup"><span data-stu-id="95e20-127">Category</span></span>

<span data-ttu-id="95e20-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="95e20-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="95e20-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="95e20-129">Affected APIs</span></span>

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
