---
ms.openlocfilehash: 4b87fb0161059eb9df919a64a9966c00177caf89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858436"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="fa53c-101">L’accès aux éléments sélectionnés d’un DataGrid WPF à partir d’un gestionnaire de l’événement UnloadingRow du DataGrid peut provoquer une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="fa53c-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fa53c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fa53c-102">Details</span></span>|<span data-ttu-id="fa53c-103">En raison d’un bogue dans .NET Framework 4.5, les gestionnaires d’événements pour les événements <xref:System.Windows.Controls.DataGrid> impliquant la suppression d’une ligne peuvent entraîner la levée d’une <xref:System.NullReferenceException?displayProperty=name> s’ils accèdent aux propriétés <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> de <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="fa53c-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="fa53c-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fa53c-104">Suggestion</span></span>|<span data-ttu-id="fa53c-105">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant une mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa53c-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="fa53c-106">Portée</span><span class="sxs-lookup"><span data-stu-id="fa53c-106">Scope</span></span>|<span data-ttu-id="fa53c-107">Mineur</span><span class="sxs-lookup"><span data-stu-id="fa53c-107">Minor</span></span>|
|<span data-ttu-id="fa53c-108">Version</span><span class="sxs-lookup"><span data-stu-id="fa53c-108">Version</span></span>|<span data-ttu-id="fa53c-109">4.5</span><span class="sxs-lookup"><span data-stu-id="fa53c-109">4.5</span></span>|
|<span data-ttu-id="fa53c-110">Type</span><span class="sxs-lookup"><span data-stu-id="fa53c-110">Type</span></span>|<span data-ttu-id="fa53c-111">Runtime</span><span class="sxs-lookup"><span data-stu-id="fa53c-111">Runtime</span></span>|
|<span data-ttu-id="fa53c-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="fa53c-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

