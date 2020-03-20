---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803208"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="61d15-101">L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus</span><span class="sxs-lookup"><span data-stu-id="61d15-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="61d15-102">Détails</span><span class="sxs-lookup"><span data-stu-id="61d15-102">Details</span></span>|<span data-ttu-id="61d15-103">L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> de <xref:System.Windows.Controls.DataGrid?displayProperty=name> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=name> perd le focus.</span><span class="sxs-lookup"><span data-stu-id="61d15-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="61d15-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="61d15-104">Suggestion</span></span>|<span data-ttu-id="61d15-105">Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61d15-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="61d15-106">Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=name> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="61d15-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="61d15-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="61d15-107">Scope</span></span>|<span data-ttu-id="61d15-108">Edge</span><span class="sxs-lookup"><span data-stu-id="61d15-108">Edge</span></span>|
|<span data-ttu-id="61d15-109">Version</span><span class="sxs-lookup"><span data-stu-id="61d15-109">Version</span></span>|<span data-ttu-id="61d15-110">4.5</span><span class="sxs-lookup"><span data-stu-id="61d15-110">4.5</span></span>|
|<span data-ttu-id="61d15-111">Type</span><span class="sxs-lookup"><span data-stu-id="61d15-111">Type</span></span>|<span data-ttu-id="61d15-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="61d15-112">Runtime</span></span>|
|<span data-ttu-id="61d15-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="61d15-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
