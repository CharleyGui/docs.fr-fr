---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394433"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="0cfce-101">Cadre partagé: Supprimé Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="0cfce-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="0cfce-102">À partir de ASP.NET Core 3.0, le `Microsoft.AspNetCore.All` métapackage et le cadre partagé correspondant `Microsoft.AspNetCore.All` ne sont plus produits.</span><span class="sxs-lookup"><span data-stu-id="0cfce-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="0cfce-103">Ce forfait est disponible en ASP.NET Core 2.2 et continuera de recevoir des mises à jour d’entretien dans ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0cfce-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0cfce-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0cfce-104">Version introduced</span></span>

<span data-ttu-id="0cfce-105">3.0</span><span class="sxs-lookup"><span data-stu-id="0cfce-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0cfce-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="0cfce-106">Old behavior</span></span>

<span data-ttu-id="0cfce-107">Les applications `Microsoft.AspNetCore.All` pourraient utiliser le `Microsoft.AspNetCore.All` métapackage pour cibler le cadre partagé sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0cfce-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0cfce-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="0cfce-108">New behavior</span></span>

<span data-ttu-id="0cfce-109">.NET Core 3.0 n’inclut pas de `Microsoft.AspNetCore.All` cadre commun.</span><span class="sxs-lookup"><span data-stu-id="0cfce-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0cfce-110">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="0cfce-110">Reason for change</span></span>

<span data-ttu-id="0cfce-111">Le `Microsoft.AspNetCore.All` métapackage comprenait un grand nombre de dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="0cfce-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0cfce-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0cfce-112">Recommended action</span></span>

<span data-ttu-id="0cfce-113">Migrez votre `Microsoft.AspNetCore.App` projet pour utiliser le cadre.</span><span class="sxs-lookup"><span data-stu-id="0cfce-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="0cfce-114">Les composants qui étaient `Microsoft.AspNetCore.All` auparavant disponibles sont toujours disponibles sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="0cfce-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="0cfce-115">Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le cadre partagé.</span><span class="sxs-lookup"><span data-stu-id="0cfce-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="0cfce-116">Category</span><span class="sxs-lookup"><span data-stu-id="0cfce-116">Category</span></span>

<span data-ttu-id="0cfce-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0cfce-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0cfce-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="0cfce-118">Affected APIs</span></span>

<span data-ttu-id="0cfce-119">None</span><span class="sxs-lookup"><span data-stu-id="0cfce-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
