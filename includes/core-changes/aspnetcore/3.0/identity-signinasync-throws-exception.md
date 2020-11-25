---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032554"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="08b1d-101">Identité : SignInAsync lève une exception pour l’identité non authentifiée</span><span class="sxs-lookup"><span data-stu-id="08b1d-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="08b1d-102">Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false` .</span><span class="sxs-lookup"><span data-stu-id="08b1d-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08b1d-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="08b1d-103">Version introduced</span></span>

<span data-ttu-id="08b1d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="08b1d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="08b1d-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="08b1d-105">Old behavior</span></span>

<span data-ttu-id="08b1d-106">`SignInAsync` accepte tous les principaux/identités, y compris les identités dans lesquelles `IsAuthenticated` est `false` .</span><span class="sxs-lookup"><span data-stu-id="08b1d-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="08b1d-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="08b1d-107">New behavior</span></span>

<span data-ttu-id="08b1d-108">Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false` .</span><span class="sxs-lookup"><span data-stu-id="08b1d-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="08b1d-109">Il existe un nouvel indicateur pour supprimer ce comportement, mais le comportement par défaut a changé.</span><span class="sxs-lookup"><span data-stu-id="08b1d-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="08b1d-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="08b1d-110">Reason for change</span></span>

<span data-ttu-id="08b1d-111">L’ancien comportement était problématique parce que, par défaut, ces principaux ont été rejetés par `[Authorize]`  /  `RequireAuthenticatedUser()` .</span><span class="sxs-lookup"><span data-stu-id="08b1d-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08b1d-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="08b1d-112">Recommended action</span></span>

<span data-ttu-id="08b1d-113">Dans ASP.NET Core 3,0 Preview 6, la valeur par `RequireAuthenticatedSignIn` `AuthenticationOptions` défaut est un indicateur `true` .</span><span class="sxs-lookup"><span data-stu-id="08b1d-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="08b1d-114">Affectez à cet indicateur `false` la valeur pour restaurer l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="08b1d-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="08b1d-115">Category</span><span class="sxs-lookup"><span data-stu-id="08b1d-115">Category</span></span>

<span data-ttu-id="08b1d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08b1d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08b1d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="08b1d-117">Affected APIs</span></span>

<span data-ttu-id="08b1d-118">None</span><span class="sxs-lookup"><span data-stu-id="08b1d-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
