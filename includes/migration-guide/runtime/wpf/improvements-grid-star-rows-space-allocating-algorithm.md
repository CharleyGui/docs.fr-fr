---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237613"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="a96ab-101">Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille</span><span class="sxs-lookup"><span data-stu-id="a96ab-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a96ab-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a96ab-102">Details</span></span>|<span data-ttu-id="a96ab-103">Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="a96ab-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="a96ab-104">Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.</span><span class="sxs-lookup"><span data-stu-id="a96ab-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="a96ab-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a96ab-105">Suggestion</span></span>|<span data-ttu-id="a96ab-106">L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.</span><span class="sxs-lookup"><span data-stu-id="a96ab-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="a96ab-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="a96ab-107">Scope</span></span>|<span data-ttu-id="a96ab-108">Majeur</span><span class="sxs-lookup"><span data-stu-id="a96ab-108">Major</span></span>|
|<span data-ttu-id="a96ab-109">Version</span><span class="sxs-lookup"><span data-stu-id="a96ab-109">Version</span></span>|<span data-ttu-id="a96ab-110">4.8</span><span class="sxs-lookup"><span data-stu-id="a96ab-110">4.8</span></span>|
|<span data-ttu-id="a96ab-111">Type</span><span class="sxs-lookup"><span data-stu-id="a96ab-111">Type</span></span>|<span data-ttu-id="a96ab-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="a96ab-112">Runtime</span></span>|
