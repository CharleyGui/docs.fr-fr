---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394219"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="d47b2-101">Identité: SignInAsync jette l’exception pour l’identité non authentique</span><span class="sxs-lookup"><span data-stu-id="d47b2-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="d47b2-102">Par défaut, `SignInAsync` jette une exception pour les `IsAuthenticated` `false`directeurs / identités dans lequel est .</span><span class="sxs-lookup"><span data-stu-id="d47b2-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d47b2-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d47b2-103">Version introduced</span></span>

<span data-ttu-id="d47b2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d47b2-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d47b2-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d47b2-105">Old behavior</span></span>

<span data-ttu-id="d47b2-106">`SignInAsync`accepte tous les principes / identités, y compris les identités dans lesquelles `IsAuthenticated` est `false`.</span><span class="sxs-lookup"><span data-stu-id="d47b2-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d47b2-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d47b2-107">New behavior</span></span>

<span data-ttu-id="d47b2-108">Par défaut, `SignInAsync` jette une exception pour les `IsAuthenticated` `false`directeurs / identités dans lequel est .</span><span class="sxs-lookup"><span data-stu-id="d47b2-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="d47b2-109">Il ya un nouveau drapeau pour supprimer ce comportement, mais le comportement par défaut a changé.</span><span class="sxs-lookup"><span data-stu-id="d47b2-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d47b2-110">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="d47b2-110">Reason for change</span></span>

<span data-ttu-id="d47b2-111">Le vieux comportement était problématique parce que, par `[Authorize]`  /  `RequireAuthenticatedUser()`défaut, ces directeurs ont été rejetés par .</span><span class="sxs-lookup"><span data-stu-id="d47b2-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d47b2-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d47b2-112">Recommended action</span></span>

<span data-ttu-id="d47b2-113">Dans ASP.NET Core 3.0 Preview 6, il `RequireAuthenticatedSignIn` y `AuthenticationOptions` a `true` un drapeau qui est par défaut.</span><span class="sxs-lookup"><span data-stu-id="d47b2-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="d47b2-114">Réglez `false` ce drapeau pour restaurer l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="d47b2-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="d47b2-115">Category</span><span class="sxs-lookup"><span data-stu-id="d47b2-115">Category</span></span>

<span data-ttu-id="d47b2-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d47b2-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d47b2-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="d47b2-117">Affected APIs</span></span>

<span data-ttu-id="d47b2-118">None</span><span class="sxs-lookup"><span data-stu-id="d47b2-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
