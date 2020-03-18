---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901946"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="6487f-101">Authentification: Newtonsoft.Json types remplacés</span><span class="sxs-lookup"><span data-stu-id="6487f-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="6487f-102">Dans ASP.NET Core 3.0, `Newtonsoft.Json` les types utilisés dans les `System.Text.Json` API d’authentification ont été remplacés par des types.</span><span class="sxs-lookup"><span data-stu-id="6487f-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="6487f-103">À l’exception des cas suivants, l’utilisation de base des paquets d’authentification n’est pas affectée :</span><span class="sxs-lookup"><span data-stu-id="6487f-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="6487f-104">Classes dérivées des fournisseurs OAuth, tels que ceux de [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="6487f-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="6487f-105">Implémentations avancées de manipulation de réclamation.</span><span class="sxs-lookup"><span data-stu-id="6487f-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="6487f-106">Pour plus d’informations, voir [dotnet/aspnetcore 7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="6487f-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="6487f-107">Pour discussion, voir [dotnet/aspnetcore 7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="6487f-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6487f-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6487f-108">Version introduced</span></span>

<span data-ttu-id="6487f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6487f-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6487f-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6487f-110">Recommended action</span></span>

<span data-ttu-id="6487f-111">Pour les implémentations dérivées d’OAuth, le changement le plus courant est `JObject.Parse` de remplacer par `JsonDocument.Parse` dans la `CreateTicketAsync` dérogation comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="6487f-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="6487f-112">L'objet `JsonDocument` implémente l'objet `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="6487f-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="6487f-113">La liste suivante décrit les changements connus :</span><span class="sxs-lookup"><span data-stu-id="6487f-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="6487f-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>devient `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="6487f-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="6487f-115">Toutes les implémentations dérivées sont `ClaimAction` également touchées.</span><span class="sxs-lookup"><span data-stu-id="6487f-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="6487f-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="6487f-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="6487f-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> devient `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="6487f-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="6487f-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>a eu un vieux constructeur enlevé `JObject` et `JsonElement`l’autre remplacé par .</span><span class="sxs-lookup"><span data-stu-id="6487f-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="6487f-119">La `User` propriété `RunClaimActions` et la méthode ont été mises à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="6487f-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="6487f-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>accepte maintenant un paramètre de type `JsonDocument` au lieu de `JObject`.</span><span class="sxs-lookup"><span data-stu-id="6487f-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="6487f-121">La `Response` propriété a été mise à jour pour correspondre.</span><span class="sxs-lookup"><span data-stu-id="6487f-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="6487f-122">`OAuthTokenResponse`est maintenant jetable et `OAuthHandler`sera éliminé par .</span><span class="sxs-lookup"><span data-stu-id="6487f-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="6487f-123">Les implémentations dérivées d’OAuth qui l’emportent `ExchangeCodeAsync` ne doivent pas disposer du `JsonDocument` ou `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="6487f-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="6487f-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>changé `JObject` de `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="6487f-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="6487f-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>changé `JObject` de `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="6487f-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="6487f-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>changé `JObject` d’accepter `JsonElement`à .</span><span class="sxs-lookup"><span data-stu-id="6487f-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="6487f-127">Category</span><span class="sxs-lookup"><span data-stu-id="6487f-127">Category</span></span>

<span data-ttu-id="6487f-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6487f-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6487f-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="6487f-129">Affected APIs</span></span>

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
