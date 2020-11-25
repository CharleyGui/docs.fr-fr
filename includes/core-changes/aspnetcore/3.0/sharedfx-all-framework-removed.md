---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032651"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="da605-101">Framework partagé : suppression de Microsoft. AspNetCore. All</span><span class="sxs-lookup"><span data-stu-id="da605-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="da605-102">À partir de ASP.NET Core 3,0, le `Microsoft.AspNetCore.All` reconditionnement et l' `Microsoft.AspNetCore.All` infrastructure partagée correspondante ne sont plus produits.</span><span class="sxs-lookup"><span data-stu-id="da605-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="da605-103">Ce package est disponible dans ASP.NET Core 2,2 et continuera à recevoir des mises à jour de maintenance dans ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="da605-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da605-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="da605-104">Version introduced</span></span>

<span data-ttu-id="da605-105">3.0</span><span class="sxs-lookup"><span data-stu-id="da605-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da605-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="da605-106">Old behavior</span></span>

<span data-ttu-id="da605-107">Les applications peuvent utiliser le `Microsoft.AspNetCore.All` package pour cibler le `Microsoft.AspNetCore.All` Framework partagé sur .net core.</span><span class="sxs-lookup"><span data-stu-id="da605-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da605-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="da605-108">New behavior</span></span>

<span data-ttu-id="da605-109">.NET Core 3,0 n’inclut pas de `Microsoft.AspNetCore.All` Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="da605-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da605-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="da605-110">Reason for change</span></span>

<span data-ttu-id="da605-111">Le `Microsoft.AspNetCore.All` reconditionnement incluait un grand nombre de dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="da605-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da605-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="da605-112">Recommended action</span></span>

<span data-ttu-id="da605-113">Migrez votre projet pour utiliser le `Microsoft.AspNetCore.App` Framework.</span><span class="sxs-lookup"><span data-stu-id="da605-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="da605-114">Les composants qui étaient précédemment disponibles dans `Microsoft.AspNetCore.All` sont toujours disponibles sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="da605-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="da605-115">Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="da605-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="da605-116">Category</span><span class="sxs-lookup"><span data-stu-id="da605-116">Category</span></span>

<span data-ttu-id="da605-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da605-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da605-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="da605-118">Affected APIs</span></span>

<span data-ttu-id="da605-119">None</span><span class="sxs-lookup"><span data-stu-id="da605-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
