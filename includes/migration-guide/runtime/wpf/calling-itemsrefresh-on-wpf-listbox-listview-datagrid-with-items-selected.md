---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620419"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="36451-101">L’appel d’Items.Refresh dans un contrôle WPF ListBox, ListView ou DataGrid contenant des éléments sélectionnés peut provoquer l’apparition d’éléments en double.</span><span class="sxs-lookup"><span data-stu-id="36451-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

#### <a name="details"></a><span data-ttu-id="36451-102">Détails</span><span class="sxs-lookup"><span data-stu-id="36451-102">Details</span></span>

<span data-ttu-id="36451-103">Dans le .NET Framework 4.5, si vous appelez ListBox.Items.Refresh à partir du code alors que des éléments sont sélectionnés dans une <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, les éléments en question peuvent apparaître deux fois dans la liste.</span><span class="sxs-lookup"><span data-stu-id="36451-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="36451-104">Un problème similaire se produit avec <xref:System.Windows.Controls.ListView?displayProperty=fullName> et <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="36451-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=fullName> and <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span></span> <span data-ttu-id="36451-105">Ce problème a été résolu dans le .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="36451-105">This is fixed in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="36451-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="36451-106">Suggestion</span></span>

<span data-ttu-id="36451-107">Pour contourner ce problème, vous pouvez désélectionner programmatiquement les éléments avant d’appeler <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>, puis les resélectionner une fois l’appel effectué.</span><span class="sxs-lookup"><span data-stu-id="36451-107">This issue may be worked around by programmatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="36451-108">Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36451-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="36451-109">Nom</span><span class="sxs-lookup"><span data-stu-id="36451-109">Name</span></span>    | <span data-ttu-id="36451-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="36451-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="36451-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="36451-111">Scope</span></span>   |<span data-ttu-id="36451-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="36451-112">Minor</span></span>|
|<span data-ttu-id="36451-113">Version</span><span class="sxs-lookup"><span data-stu-id="36451-113">Version</span></span>|<span data-ttu-id="36451-114">4,5</span><span class="sxs-lookup"><span data-stu-id="36451-114">4.5</span></span>|
|<span data-ttu-id="36451-115">Type</span><span class="sxs-lookup"><span data-stu-id="36451-115">Type</span></span>|<span data-ttu-id="36451-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="36451-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36451-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="36451-117">Affected APIs</span></span>

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
