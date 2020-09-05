---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496180"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="06181-101">L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus</span><span class="sxs-lookup"><span data-stu-id="06181-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="06181-102">Détails</span><span class="sxs-lookup"><span data-stu-id="06181-102">Details</span></span>

<span data-ttu-id="06181-103">L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perd le focus.</span><span class="sxs-lookup"><span data-stu-id="06181-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06181-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="06181-104">Suggestion</span></span>

<span data-ttu-id="06181-105">Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06181-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="06181-106">Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="06181-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="06181-107">Name</span><span class="sxs-lookup"><span data-stu-id="06181-107">Name</span></span>    | <span data-ttu-id="06181-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="06181-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06181-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="06181-109">Scope</span></span>   |<span data-ttu-id="06181-110">Edge</span><span class="sxs-lookup"><span data-stu-id="06181-110">Edge</span></span>|
|<span data-ttu-id="06181-111">Version</span><span class="sxs-lookup"><span data-stu-id="06181-111">Version</span></span>|<span data-ttu-id="06181-112">4,5</span><span class="sxs-lookup"><span data-stu-id="06181-112">4.5</span></span>|
|<span data-ttu-id="06181-113">Type</span><span class="sxs-lookup"><span data-stu-id="06181-113">Type</span></span>|<span data-ttu-id="06181-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="06181-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="06181-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="06181-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
