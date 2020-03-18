---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394281"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="6a55f-101">Authentification : La signature OAuthHandler ExchangeCodeAsync modifiée</span><span class="sxs-lookup"><span data-stu-id="6a55f-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="6a55f-102">Dans ASP.NET Core 3.0, la `OAuthHandler.ExchangeCodeAsync` signature de a été changée de:</span><span class="sxs-lookup"><span data-stu-id="6a55f-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="6a55f-103">Par :</span><span class="sxs-lookup"><span data-stu-id="6a55f-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="6a55f-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6a55f-104">Version introduced</span></span>

<span data-ttu-id="6a55f-105">3.0</span><span class="sxs-lookup"><span data-stu-id="6a55f-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6a55f-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6a55f-106">Old behavior</span></span>

<span data-ttu-id="6a55f-107">Les `code` `redirectUri` et les ficelles ont été adoptées comme des arguments distincts.</span><span class="sxs-lookup"><span data-stu-id="6a55f-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6a55f-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6a55f-108">New behavior</span></span>

<span data-ttu-id="6a55f-109">`Code`et `RedirectUri` sont `OAuthCodeExchangeContext` des propriétés sur `OAuthCodeExchangeContext` qui peuvent être définis via le constructeur.</span><span class="sxs-lookup"><span data-stu-id="6a55f-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="6a55f-110">Le `OAuthCodeExchangeContext` nouveau type est le `OAuthHandler.ExchangeCodeAsync`seul argument passé à .</span><span class="sxs-lookup"><span data-stu-id="6a55f-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6a55f-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="6a55f-111">Reason for change</span></span>

<span data-ttu-id="6a55f-112">Cette modification permet de fournir des paramètres supplémentaires d’une manière non-rupture.</span><span class="sxs-lookup"><span data-stu-id="6a55f-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="6a55f-113">Il n’est pas `ExchangeCodeAsync` nécessaire de créer de nouvelles surcharges.</span><span class="sxs-lookup"><span data-stu-id="6a55f-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6a55f-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6a55f-114">Recommended action</span></span>

<span data-ttu-id="6a55f-115">Construire `OAuthCodeExchangeContext` un avec `code` `redirectUri` le approprié et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="6a55f-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="6a55f-116">Une <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="6a55f-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="6a55f-117">Cette `OAuthCodeExchangeContext` seule instance peut `OAuthHandler.ExchangeCodeAsync` être adoptée au lieu de multiples arguments.</span><span class="sxs-lookup"><span data-stu-id="6a55f-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="6a55f-118">Category</span><span class="sxs-lookup"><span data-stu-id="6a55f-118">Category</span></span>

<span data-ttu-id="6a55f-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6a55f-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6a55f-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6a55f-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
