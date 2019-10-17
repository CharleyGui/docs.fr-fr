---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394281"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="6b238-101">Authentification : OAuthHandler ExchangeCodeAsync signature a changé</span><span class="sxs-lookup"><span data-stu-id="6b238-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="6b238-102">Dans ASP.NET Core 3,0, la signature de `OAuthHandler.ExchangeCodeAsync` a été remplacée par :</span><span class="sxs-lookup"><span data-stu-id="6b238-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="6b238-103">À :</span><span class="sxs-lookup"><span data-stu-id="6b238-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="6b238-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6b238-104">Version introduced</span></span>

<span data-ttu-id="6b238-105">3,0</span><span class="sxs-lookup"><span data-stu-id="6b238-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6b238-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6b238-106">Old behavior</span></span>

<span data-ttu-id="6b238-107">Les chaînes `code` et `redirectUri` ont été passées en tant qu’arguments distincts.</span><span class="sxs-lookup"><span data-stu-id="6b238-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6b238-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6b238-108">New behavior</span></span>

<span data-ttu-id="6b238-109">`Code` et `RedirectUri` sont des propriétés sur `OAuthCodeExchangeContext` qui peuvent être définies via le constructeur `OAuthCodeExchangeContext`.</span><span class="sxs-lookup"><span data-stu-id="6b238-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="6b238-110">Le nouveau type `OAuthCodeExchangeContext` est le seul argument passé à `OAuthHandler.ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b238-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6b238-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6b238-111">Reason for change</span></span>

<span data-ttu-id="6b238-112">Cette modification permet de fournir des paramètres supplémentaires de manière sans rupture.</span><span class="sxs-lookup"><span data-stu-id="6b238-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="6b238-113">Il n’est pas nécessaire de créer de nouvelles surcharges `ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b238-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b238-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6b238-114">Recommended action</span></span>

<span data-ttu-id="6b238-115">Construisez un `OAuthCodeExchangeContext` avec les valeurs `code` et `redirectUri` appropriées.</span><span class="sxs-lookup"><span data-stu-id="6b238-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="6b238-116">Une instance <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="6b238-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="6b238-117">Cette seule instance `OAuthCodeExchangeContext` peut être passée à `OAuthHandler.ExchangeCodeAsync` au lieu de plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="6b238-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="6b238-118">Category</span><span class="sxs-lookup"><span data-stu-id="6b238-118">Category</span></span>

<span data-ttu-id="6b238-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b238-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b238-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b238-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
