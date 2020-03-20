---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237613"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="7c2b1-101">Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille</span><span class="sxs-lookup"><span data-stu-id="7c2b1-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7c2b1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7c2b1-102">Details</span></span>|<span data-ttu-id="7c2b1-103">Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="7c2b1-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="7c2b1-104">Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.</span><span class="sxs-lookup"><span data-stu-id="7c2b1-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="7c2b1-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7c2b1-105">Suggestion</span></span>|<span data-ttu-id="7c2b1-106">L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.</span><span class="sxs-lookup"><span data-stu-id="7c2b1-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="7c2b1-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="7c2b1-107">Scope</span></span>|<span data-ttu-id="7c2b1-108">Majeure</span><span class="sxs-lookup"><span data-stu-id="7c2b1-108">Major</span></span>|
|<span data-ttu-id="7c2b1-109">Version</span><span class="sxs-lookup"><span data-stu-id="7c2b1-109">Version</span></span>|<span data-ttu-id="7c2b1-110">4.8</span><span class="sxs-lookup"><span data-stu-id="7c2b1-110">4.8</span></span>|
|<span data-ttu-id="7c2b1-111">Type</span><span class="sxs-lookup"><span data-stu-id="7c2b1-111">Type</span></span>|<span data-ttu-id="7c2b1-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="7c2b1-112">Runtime</span></span>|
