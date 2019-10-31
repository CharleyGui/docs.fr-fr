---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198419"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="0016d-101">Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="0016d-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="0016d-102">Dans ASP.NET Core 3,0, une nouvelle méthode `GetFallbackPolicyAsync` a été ajoutée à `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="0016d-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="0016d-103">Cette stratégie de secours est utilisée par l’intergiciel (middleware) d’autorisation quand aucune stratégie n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0016d-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="0016d-104">Pour plus d’informations, consultez [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="0016d-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0016d-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0016d-105">Version introduced</span></span>

<span data-ttu-id="0016d-106">3,0</span><span class="sxs-lookup"><span data-stu-id="0016d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0016d-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="0016d-107">Old behavior</span></span>

<span data-ttu-id="0016d-108">Les implémentations de `IAuthorizationPolicyProvider` n’ont pas besoin d’une méthode `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="0016d-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0016d-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="0016d-109">New behavior</span></span>

<span data-ttu-id="0016d-110">Les implémentations de `IAuthorizationPolicyProvider` requièrent une méthode `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="0016d-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0016d-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="0016d-111">Reason for change</span></span>

<span data-ttu-id="0016d-112">Une nouvelle méthode était nécessaire pour la nouvelle `AuthorizationMiddleware` à utiliser quand aucune stratégie n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0016d-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0016d-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0016d-113">Recommended action</span></span>

<span data-ttu-id="0016d-114">Ajoutez la méthode `GetFallbackPolicyAsync` à vos implémentations de `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="0016d-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="0016d-115">Category</span><span class="sxs-lookup"><span data-stu-id="0016d-115">Category</span></span>

<span data-ttu-id="0016d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0016d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0016d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="0016d-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
