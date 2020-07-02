---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622027"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="82e3b-101">L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus</span><span class="sxs-lookup"><span data-stu-id="82e3b-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="82e3b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="82e3b-102">Details</span></span>

<span data-ttu-id="82e3b-103">L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perd le focus.</span><span class="sxs-lookup"><span data-stu-id="82e3b-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="82e3b-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="82e3b-104">Suggestion</span></span>

<span data-ttu-id="82e3b-105">Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82e3b-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="82e3b-106">Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="82e3b-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="82e3b-107">Nom</span><span class="sxs-lookup"><span data-stu-id="82e3b-107">Name</span></span>    | <span data-ttu-id="82e3b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="82e3b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="82e3b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="82e3b-109">Scope</span></span>   |<span data-ttu-id="82e3b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="82e3b-110">Edge</span></span>|
|<span data-ttu-id="82e3b-111">Version</span><span class="sxs-lookup"><span data-stu-id="82e3b-111">Version</span></span>|<span data-ttu-id="82e3b-112">4,5</span><span class="sxs-lookup"><span data-stu-id="82e3b-112">4.5</span></span>|
|<span data-ttu-id="82e3b-113">Type</span><span class="sxs-lookup"><span data-stu-id="82e3b-113">Type</span></span>|<span data-ttu-id="82e3b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="82e3b-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82e3b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="82e3b-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
