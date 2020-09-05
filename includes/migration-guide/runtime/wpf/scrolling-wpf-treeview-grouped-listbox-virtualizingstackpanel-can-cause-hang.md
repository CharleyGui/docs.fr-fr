---
ms.openlocfilehash: 31ada197db36be192317e32a37a353d375d9cc65
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497361"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="ef85f-101">Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut provoquer un blocage</span><span class="sxs-lookup"><span data-stu-id="ef85f-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="ef85f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ef85f-102">Details</span></span>

<span data-ttu-id="ef85f-103">Dans le .NET Framework 4.5, le défilement d’un contrôle <xref:System.Windows.Controls.TreeView?displayProperty=fullName> WPF dans un panneau d’empilement virtualisé peut provoquer un blocage si la fenêtre d’affichage comporte des marges (par exemple entre les éléments du <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou sur un élément ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="ef85f-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="ef85f-104">En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.</span><span class="sxs-lookup"><span data-stu-id="ef85f-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ef85f-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ef85f-105">Suggestion</span></span>

<span data-ttu-id="ef85f-106">Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="ef85f-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="ef85f-107">Vous pouvez également supprimer les marges des collections de vue (comme les <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.</span><span class="sxs-lookup"><span data-stu-id="ef85f-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="ef85f-108">Name</span><span class="sxs-lookup"><span data-stu-id="ef85f-108">Name</span></span>    | <span data-ttu-id="ef85f-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ef85f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef85f-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="ef85f-110">Scope</span></span>   |<span data-ttu-id="ef85f-111">Majeure</span><span class="sxs-lookup"><span data-stu-id="ef85f-111">Major</span></span>|
|<span data-ttu-id="ef85f-112">Version</span><span class="sxs-lookup"><span data-stu-id="ef85f-112">Version</span></span>|<span data-ttu-id="ef85f-113">4,5</span><span class="sxs-lookup"><span data-stu-id="ef85f-113">4.5</span></span>|
|<span data-ttu-id="ef85f-114">Type</span><span class="sxs-lookup"><span data-stu-id="ef85f-114">Type</span></span>|<span data-ttu-id="ef85f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="ef85f-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ef85f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="ef85f-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)`

-->
