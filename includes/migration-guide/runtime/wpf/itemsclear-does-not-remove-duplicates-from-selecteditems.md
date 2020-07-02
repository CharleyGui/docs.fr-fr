---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619916"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="75c2f-101">Items.Clear ne supprime pas les doublons de SelectedItems</span><span class="sxs-lookup"><span data-stu-id="75c2f-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="75c2f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="75c2f-102">Details</span></span>

<span data-ttu-id="75c2f-103">Supposons qu’un sélecteur (avec la sélection multiple activée) a des doublons dans sa collection <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> - le même élément apparaît plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="75c2f-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="75c2f-104">La suppression de ces éléments de la source de données (par exemple en appelant Items.Clear) échoue à les supprimer de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>. Seule la première instance est supprimée.</span><span class="sxs-lookup"><span data-stu-id="75c2f-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="75c2f-105">De plus, une utilisation ultérieure de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (par exemple SelectedItems.Clear()) peut rencontrer des problèmes comme <xref:System.ArgumentException?displayProperty=fullName>, car <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contient des éléments qui ne sont plus dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="75c2f-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75c2f-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="75c2f-106">Suggestion</span></span>

<span data-ttu-id="75c2f-107">Si possible, mettez à niveau vers .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="75c2f-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="75c2f-108">Nom</span><span class="sxs-lookup"><span data-stu-id="75c2f-108">Name</span></span>    | <span data-ttu-id="75c2f-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="75c2f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75c2f-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="75c2f-110">Scope</span></span>   |<span data-ttu-id="75c2f-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="75c2f-111">Minor</span></span>|
|<span data-ttu-id="75c2f-112">Version</span><span class="sxs-lookup"><span data-stu-id="75c2f-112">Version</span></span>|<span data-ttu-id="75c2f-113">4,5</span><span class="sxs-lookup"><span data-stu-id="75c2f-113">4.5</span></span>|
|<span data-ttu-id="75c2f-114">Type</span><span class="sxs-lookup"><span data-stu-id="75c2f-114">Type</span></span>|<span data-ttu-id="75c2f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="75c2f-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75c2f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="75c2f-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
