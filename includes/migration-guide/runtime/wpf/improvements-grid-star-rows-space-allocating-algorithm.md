---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621996"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="9a1fe-101">Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille</span><span class="sxs-lookup"><span data-stu-id="9a1fe-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="9a1fe-102">Détails</span><span class="sxs-lookup"><span data-stu-id="9a1fe-102">Details</span></span>

<span data-ttu-id="9a1fe-103">Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9a1fe-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="9a1fe-104">Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.</span><span class="sxs-lookup"><span data-stu-id="9a1fe-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9a1fe-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="9a1fe-105">Suggestion</span></span>

<span data-ttu-id="9a1fe-106">L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.</span><span class="sxs-lookup"><span data-stu-id="9a1fe-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="9a1fe-107">Nom</span><span class="sxs-lookup"><span data-stu-id="9a1fe-107">Name</span></span>    | <span data-ttu-id="9a1fe-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="9a1fe-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a1fe-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="9a1fe-109">Scope</span></span>   |<span data-ttu-id="9a1fe-110">Majeure</span><span class="sxs-lookup"><span data-stu-id="9a1fe-110">Major</span></span>|
|<span data-ttu-id="9a1fe-111">Version</span><span class="sxs-lookup"><span data-stu-id="9a1fe-111">Version</span></span>|<span data-ttu-id="9a1fe-112">4.8</span><span class="sxs-lookup"><span data-stu-id="9a1fe-112">4.8</span></span>|
|<span data-ttu-id="9a1fe-113">Type</span><span class="sxs-lookup"><span data-stu-id="9a1fe-113">Type</span></span>|<span data-ttu-id="9a1fe-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="9a1fe-114">Runtime</span></span>|
