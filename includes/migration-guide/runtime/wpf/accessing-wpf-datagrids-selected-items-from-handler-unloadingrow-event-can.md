---
ms.openlocfilehash: 1487e32ffca7b4bbebb5edac7efc8961ac05723b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497231"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="75de9-101">L’accès aux éléments sélectionnés d’un DataGrid WPF à partir d’un gestionnaire de l’événement UnloadingRow du DataGrid peut provoquer une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="75de9-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="75de9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="75de9-102">Details</span></span>

<span data-ttu-id="75de9-103">En raison d’un bogue dans .NET Framework 4.5, les gestionnaires d’événements pour les événements <xref:System.Windows.Controls.DataGrid> impliquant la suppression d’une ligne peuvent entraîner la levée d’une <xref:System.NullReferenceException?displayProperty=fullName> s’ils accèdent aux propriétés <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="75de9-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75de9-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="75de9-104">Suggestion</span></span>

<span data-ttu-id="75de9-105">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75de9-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="75de9-106">Name</span><span class="sxs-lookup"><span data-stu-id="75de9-106">Name</span></span>    | <span data-ttu-id="75de9-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="75de9-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75de9-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="75de9-108">Scope</span></span>   |<span data-ttu-id="75de9-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="75de9-109">Minor</span></span>|
|<span data-ttu-id="75de9-110">Version</span><span class="sxs-lookup"><span data-stu-id="75de9-110">Version</span></span>|<span data-ttu-id="75de9-111">4,5</span><span class="sxs-lookup"><span data-stu-id="75de9-111">4.5</span></span>|
|<span data-ttu-id="75de9-112">Type</span><span class="sxs-lookup"><span data-stu-id="75de9-112">Type</span></span>|<span data-ttu-id="75de9-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="75de9-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="75de9-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="75de9-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.Controls.DataGrid.UnloadingRow`
- `E:System.Windows.Controls.DataGrid.UnloadingRowDetails`

-->
