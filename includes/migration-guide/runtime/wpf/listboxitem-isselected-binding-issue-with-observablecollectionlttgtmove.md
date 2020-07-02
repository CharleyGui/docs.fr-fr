---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620452"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="279c7-101">Problème de liaison ListBoxItem IsSelected avec ObservableCollection&lt;T&gt;.Move</span><span class="sxs-lookup"><span data-stu-id="279c7-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="279c7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="279c7-102">Details</span></span>

<span data-ttu-id="279c7-103">L’appel de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou de <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> sur une collection liée à un <xref:System.Windows.Controls.ListBox?displayProperty=fullName> avec des éléments sélectionnés peut entraîner un comportement imprévisible avec une sélection ultérieure ou la désélection d’éléments de <xref:System.Windows.Controls.ListBox?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="279c7-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="279c7-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="279c7-104">Suggestion</span></span>

<span data-ttu-id="279c7-105">L’appel de <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> et de <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> au lieu de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> permet de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="279c7-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="279c7-106">Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="279c7-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="279c7-107">Nom</span><span class="sxs-lookup"><span data-stu-id="279c7-107">Name</span></span>    | <span data-ttu-id="279c7-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="279c7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="279c7-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="279c7-109">Scope</span></span>   |<span data-ttu-id="279c7-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="279c7-110">Minor</span></span>|
|<span data-ttu-id="279c7-111">Version</span><span class="sxs-lookup"><span data-stu-id="279c7-111">Version</span></span>|<span data-ttu-id="279c7-112">4,5</span><span class="sxs-lookup"><span data-stu-id="279c7-112">4.5</span></span>|
|<span data-ttu-id="279c7-113">Type</span><span class="sxs-lookup"><span data-stu-id="279c7-113">Type</span></span>|<span data-ttu-id="279c7-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="279c7-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="279c7-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="279c7-115">Affected APIs</span></span>

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
