---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497245"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="1c4b0-101">DataGridCellsPanel.BringIndexIntoView lève une exception ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="1c4b0-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="1c4b0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1c4b0-102">Details</span></span>

<span data-ttu-id="1c4b0-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> fonctionne de façon asynchrone quand la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas encore été déterminées.</span><span class="sxs-lookup"><span data-stu-id="1c4b0-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="1c4b0-104">Si des colonnes sont supprimées avant le travail asynchrone, une <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> peut se produire.</span><span class="sxs-lookup"><span data-stu-id="1c4b0-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1c4b0-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1c4b0-105">Suggestion</span></span>

<span data-ttu-id="1c4b0-106">Effectuez une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c4b0-106">Any one of the following:</span></span><ol><li><span data-ttu-id="1c4b0-107">Mise à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1c4b0-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="1c4b0-108">Installation du dernier correctif pour .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c4b0-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="1c4b0-109">Évitez de supprimer des colonnes jusqu’à ce que la réponse asynchrone à <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> soit effective.</span><span class="sxs-lookup"><span data-stu-id="1c4b0-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="1c4b0-110">Name</span><span class="sxs-lookup"><span data-stu-id="1c4b0-110">Name</span></span>    | <span data-ttu-id="1c4b0-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="1c4b0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1c4b0-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="1c4b0-112">Scope</span></span>   |<span data-ttu-id="1c4b0-113">Edge</span><span class="sxs-lookup"><span data-stu-id="1c4b0-113">Edge</span></span>|
|<span data-ttu-id="1c4b0-114">Version</span><span class="sxs-lookup"><span data-stu-id="1c4b0-114">Version</span></span>|<span data-ttu-id="1c4b0-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c4b0-115">4.6.2</span></span>|
|<span data-ttu-id="1c4b0-116">Type</span><span class="sxs-lookup"><span data-stu-id="1c4b0-116">Type</span></span>|<span data-ttu-id="1c4b0-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="1c4b0-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1c4b0-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="1c4b0-118">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->
