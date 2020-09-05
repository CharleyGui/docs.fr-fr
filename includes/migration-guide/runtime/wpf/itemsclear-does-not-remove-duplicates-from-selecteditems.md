---
ms.openlocfilehash: 25ce391f917bd270d4d9a75f608e4a8ec763d15c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497606"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="df21a-101">Items.Clear ne supprime pas les doublons de SelectedItems</span><span class="sxs-lookup"><span data-stu-id="df21a-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="df21a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="df21a-102">Details</span></span>

<span data-ttu-id="df21a-103">Supposons qu’un sélecteur (avec la sélection multiple activée) a des doublons dans sa collection <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> - le même élément apparaît plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="df21a-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="df21a-104">La suppression de ces éléments de la source de données (par exemple en appelant Items.Clear) échoue à les supprimer de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>. Seule la première instance est supprimée.</span><span class="sxs-lookup"><span data-stu-id="df21a-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="df21a-105">De plus, une utilisation ultérieure de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (par exemple SelectedItems.Clear()) peut rencontrer des problèmes comme <xref:System.ArgumentException?displayProperty=fullName>, car <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contient des éléments qui ne sont plus dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="df21a-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df21a-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="df21a-106">Suggestion</span></span>

<span data-ttu-id="df21a-107">Si possible, mettez à niveau vers .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="df21a-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="df21a-108">Name</span><span class="sxs-lookup"><span data-stu-id="df21a-108">Name</span></span>    | <span data-ttu-id="df21a-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="df21a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df21a-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="df21a-110">Scope</span></span>   |<span data-ttu-id="df21a-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="df21a-111">Minor</span></span>|
|<span data-ttu-id="df21a-112">Version</span><span class="sxs-lookup"><span data-stu-id="df21a-112">Version</span></span>|<span data-ttu-id="df21a-113">4,5</span><span class="sxs-lookup"><span data-stu-id="df21a-113">4.5</span></span>|
|<span data-ttu-id="df21a-114">Type</span><span class="sxs-lookup"><span data-stu-id="df21a-114">Type</span></span>|<span data-ttu-id="df21a-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="df21a-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="df21a-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="df21a-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.MultiSelector.SelectedItems`

-->
