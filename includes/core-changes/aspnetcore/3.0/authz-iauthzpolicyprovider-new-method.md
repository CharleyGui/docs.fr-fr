---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901884"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="583ee-101">Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="583ee-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="583ee-102">Dans ASP.NET Core 3,0, une nouvelle `GetFallbackPolicyAsync` méthode a été ajoutée `IAuthorizationPolicyProvider`à.</span><span class="sxs-lookup"><span data-stu-id="583ee-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="583ee-103">Cette stratégie de secours est utilisée par l’intergiciel (middleware) d’autorisation quand aucune stratégie n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="583ee-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="583ee-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="583ee-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="583ee-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="583ee-105">Version introduced</span></span>

<span data-ttu-id="583ee-106">3.0</span><span class="sxs-lookup"><span data-stu-id="583ee-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="583ee-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="583ee-107">Old behavior</span></span>

<span data-ttu-id="583ee-108">Les implémentations `IAuthorizationPolicyProvider` de n’ont `GetFallbackPolicyAsync` pas besoin d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="583ee-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="583ee-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="583ee-109">New behavior</span></span>

<span data-ttu-id="583ee-110">Les implémentations `IAuthorizationPolicyProvider` de requièrent une `GetFallbackPolicyAsync` méthode.</span><span class="sxs-lookup"><span data-stu-id="583ee-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="583ee-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="583ee-111">Reason for change</span></span>

<span data-ttu-id="583ee-112">Une nouvelle méthode était nécessaire pour que le `AuthorizationMiddleware` nouveau utilise quand aucune stratégie n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="583ee-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="583ee-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="583ee-113">Recommended action</span></span>

<span data-ttu-id="583ee-114">Ajoutez la `GetFallbackPolicyAsync` méthode à vos implémentations de `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="583ee-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="583ee-115">Category</span><span class="sxs-lookup"><span data-stu-id="583ee-115">Category</span></span>

<span data-ttu-id="583ee-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="583ee-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="583ee-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="583ee-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
