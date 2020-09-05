---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496777"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="5cddc-101">Problème de liaison ListBoxItem IsSelected avec ObservableCollection&lt;T&gt;.Move</span><span class="sxs-lookup"><span data-stu-id="5cddc-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="5cddc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5cddc-102">Details</span></span>

<span data-ttu-id="5cddc-103">L’appel de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou de <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> sur une collection liée à un <xref:System.Windows.Controls.ListBox?displayProperty=fullName> avec des éléments sélectionnés peut entraîner un comportement imprévisible avec une sélection ultérieure ou la désélection d’éléments de <xref:System.Windows.Controls.ListBox?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5cddc-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5cddc-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5cddc-104">Suggestion</span></span>

<span data-ttu-id="5cddc-105">L’appel de <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> et de <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> au lieu de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> permet de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="5cddc-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="5cddc-106">Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cddc-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="5cddc-107">Name</span><span class="sxs-lookup"><span data-stu-id="5cddc-107">Name</span></span>    | <span data-ttu-id="5cddc-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="5cddc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5cddc-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="5cddc-109">Scope</span></span>   |<span data-ttu-id="5cddc-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5cddc-110">Minor</span></span>|
|<span data-ttu-id="5cddc-111">Version</span><span class="sxs-lookup"><span data-stu-id="5cddc-111">Version</span></span>|<span data-ttu-id="5cddc-112">4,5</span><span class="sxs-lookup"><span data-stu-id="5cddc-112">4.5</span></span>|
|<span data-ttu-id="5cddc-113">Type</span><span class="sxs-lookup"><span data-stu-id="5cddc-113">Type</span></span>|<span data-ttu-id="5cddc-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="5cddc-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5cddc-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="5cddc-115">Affected APIs</span></span>

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->
