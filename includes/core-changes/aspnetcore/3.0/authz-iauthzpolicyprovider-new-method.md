---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901884"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="08c1e-101">Autorisation: IAuthorizationPolicyProvider implémentations nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="08c1e-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="08c1e-102">Dans ASP.NET Core 3.0, une `GetFallbackPolicyAsync` nouvelle méthode `IAuthorizationPolicyProvider`a été ajoutée à .</span><span class="sxs-lookup"><span data-stu-id="08c1e-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="08c1e-103">Cette politique de repli est utilisée par l’autorisation middleware lorsqu’aucune politique n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="08c1e-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="08c1e-104">Pour plus d’informations, voir [dotnet/aspnetcore 9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="08c1e-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08c1e-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="08c1e-105">Version introduced</span></span>

<span data-ttu-id="08c1e-106">3.0</span><span class="sxs-lookup"><span data-stu-id="08c1e-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="08c1e-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="08c1e-107">Old behavior</span></span>

<span data-ttu-id="08c1e-108">Les implémentations `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` de n’a pas nécessité de méthode.</span><span class="sxs-lookup"><span data-stu-id="08c1e-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="08c1e-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="08c1e-109">New behavior</span></span>

<span data-ttu-id="08c1e-110">Les implémentations nécessitent `IAuthorizationPolicyProvider` une `GetFallbackPolicyAsync` méthode.</span><span class="sxs-lookup"><span data-stu-id="08c1e-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="08c1e-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="08c1e-111">Reason for change</span></span>

<span data-ttu-id="08c1e-112">Une nouvelle méthode était `AuthorizationMiddleware` nécessaire pour que le nouveau soit utilisé lorsqu’aucune stratégie n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="08c1e-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08c1e-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="08c1e-113">Recommended action</span></span>

<span data-ttu-id="08c1e-114">Ajoutez `GetFallbackPolicyAsync` la méthode à `IAuthorizationPolicyProvider`vos implémentations de .</span><span class="sxs-lookup"><span data-stu-id="08c1e-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="08c1e-115">Category</span><span class="sxs-lookup"><span data-stu-id="08c1e-115">Category</span></span>

<span data-ttu-id="08c1e-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08c1e-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08c1e-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="08c1e-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
