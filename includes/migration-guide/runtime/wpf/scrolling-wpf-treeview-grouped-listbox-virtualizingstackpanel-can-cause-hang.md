---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622054"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="a7789-101">Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut provoquer un blocage</span><span class="sxs-lookup"><span data-stu-id="a7789-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="a7789-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a7789-102">Details</span></span>

<span data-ttu-id="a7789-103">Dans le .NET Framework 4.5, le défilement d’un contrôle <xref:System.Windows.Controls.TreeView?displayProperty=fullName> WPF dans un panneau d’empilement virtualisé peut provoquer un blocage si la fenêtre d’affichage comporte des marges (par exemple entre les éléments du <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou sur un élément ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="a7789-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="a7789-104">En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.</span><span class="sxs-lookup"><span data-stu-id="a7789-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a7789-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a7789-105">Suggestion</span></span>

<span data-ttu-id="a7789-106">Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="a7789-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="a7789-107">Vous pouvez également supprimer les marges des collections de vue (comme les <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.</span><span class="sxs-lookup"><span data-stu-id="a7789-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="a7789-108">Nom</span><span class="sxs-lookup"><span data-stu-id="a7789-108">Name</span></span>    | <span data-ttu-id="a7789-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="a7789-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a7789-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="a7789-110">Scope</span></span>   |<span data-ttu-id="a7789-111">Majeure</span><span class="sxs-lookup"><span data-stu-id="a7789-111">Major</span></span>|
|<span data-ttu-id="a7789-112">Version</span><span class="sxs-lookup"><span data-stu-id="a7789-112">Version</span></span>|<span data-ttu-id="a7789-113">4,5</span><span class="sxs-lookup"><span data-stu-id="a7789-113">4.5</span></span>|
|<span data-ttu-id="a7789-114">Type</span><span class="sxs-lookup"><span data-stu-id="a7789-114">Type</span></span>|<span data-ttu-id="a7789-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="a7789-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7789-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="a7789-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
