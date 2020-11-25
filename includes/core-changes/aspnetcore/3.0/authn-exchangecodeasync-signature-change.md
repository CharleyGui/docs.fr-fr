---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032330"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="f9d03-101">Authentification : OAuthHandler ExchangeCodeAsync signature a changé</span><span class="sxs-lookup"><span data-stu-id="f9d03-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="f9d03-102">Dans ASP.NET Core 3,0, la signature de `OAuthHandler.ExchangeCodeAsync` a été remplacée par :</span><span class="sxs-lookup"><span data-stu-id="f9d03-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="f9d03-103">Par :</span><span class="sxs-lookup"><span data-stu-id="f9d03-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="f9d03-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f9d03-104">Version introduced</span></span>

<span data-ttu-id="f9d03-105">3.0</span><span class="sxs-lookup"><span data-stu-id="f9d03-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f9d03-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f9d03-106">Old behavior</span></span>

<span data-ttu-id="f9d03-107">Les `code` `redirectUri` chaînes et ont été passées en tant qu’arguments distincts.</span><span class="sxs-lookup"><span data-stu-id="f9d03-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f9d03-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f9d03-108">New behavior</span></span>

<span data-ttu-id="f9d03-109">`Code` et `RedirectUri` sont des propriétés `OAuthCodeExchangeContext` qui peuvent être définies via le `OAuthCodeExchangeContext` constructeur.</span><span class="sxs-lookup"><span data-stu-id="f9d03-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="f9d03-110">Le nouveau `OAuthCodeExchangeContext` type est le seul argument passé à `OAuthHandler.ExchangeCodeAsync` .</span><span class="sxs-lookup"><span data-stu-id="f9d03-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f9d03-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f9d03-111">Reason for change</span></span>

<span data-ttu-id="f9d03-112">Cette modification permet de fournir des paramètres supplémentaires de manière sans rupture.</span><span class="sxs-lookup"><span data-stu-id="f9d03-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="f9d03-113">Il n’est pas nécessaire de créer de nouvelles `ExchangeCodeAsync` surcharges.</span><span class="sxs-lookup"><span data-stu-id="f9d03-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9d03-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f9d03-114">Recommended action</span></span>

<span data-ttu-id="f9d03-115">Construisez un `OAuthCodeExchangeContext` avec les `code` valeurs et appropriées `redirectUri` .</span><span class="sxs-lookup"><span data-stu-id="f9d03-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="f9d03-116">Une <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="f9d03-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="f9d03-117">Cette `OAuthCodeExchangeContext` instance unique peut être passée au `OAuthHandler.ExchangeCodeAsync` au lieu de plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="f9d03-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="f9d03-118">Category</span><span class="sxs-lookup"><span data-stu-id="f9d03-118">Category</span></span>

<span data-ttu-id="f9d03-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9d03-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9d03-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="f9d03-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
