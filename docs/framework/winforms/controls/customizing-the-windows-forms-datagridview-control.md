---
title: Personnaliser le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744025"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="c86c6-102">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c86c6-103">Le contrôle `DataGridView` fournit plusieurs propriétés que vous pouvez utiliser pour ajuster l’apparence et le comportement de base (apparence) de ses cellules, lignes et colonnes.</span><span class="sxs-lookup"><span data-stu-id="c86c6-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="c86c6-104">Toutefois, si vous avez des besoins spécifiques qui vont au-delà des capacités de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>, vous pouvez également implémenter le dessin owner-drawn pour le contrôle ou étendre ses fonctionnalités en créant des cellules, des colonnes et des lignes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c86c6-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="c86c6-105">Pour peindre vous-même des cellules et des lignes, vous pouvez gérer plusieurs événements de dessin `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="c86c6-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="c86c6-106">Pour modifier des fonctionnalités existantes ou fournir de nouvelles fonctionnalités, vous pouvez créer vos propres types dérivés des types `DataGridViewCell`, `DataGridViewColumn`et `DataGridViewRow` existants.</span><span class="sxs-lookup"><span data-stu-id="c86c6-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="c86c6-107">Vous pouvez également fournir de nouvelles fonctionnalités de modification en créant des types dérivés qui affichent un contrôle de votre choix lorsqu’une cellule est en mode édition.</span><span class="sxs-lookup"><span data-stu-id="c86c6-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c86c6-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c86c6-108">In This Section</span></span>  
 [<span data-ttu-id="c86c6-109">Guide pratique pour personnaliser l’apparence des cellules du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="c86c6-110">Décrit comment gérer l’événement <xref:System.Windows.Forms.DataGridView.CellPainting> pour peindre des cellules manuellement.</span><span class="sxs-lookup"><span data-stu-id="c86c6-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="c86c6-111">Guide pratique pour personnaliser l’apparence des lignes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="c86c6-112">Décrit comment gérer les événements <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> pour peindre des lignes avec un arrière-plan dégradé personnalisé et un contenu qui s’étend sur plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="c86c6-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="c86c6-113">Guide pratique pour personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence</span><span class="sxs-lookup"><span data-stu-id="c86c6-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="c86c6-114">Décrit comment créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin de mettre en surbrillance des cellules lorsque le pointeur de la souris se trouve sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="c86c6-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="c86c6-115">Guide pratique pour désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="c86c6-116">Décrit comment créer des types personnalisés dérivés de <xref:System.Windows.Forms.DataGridViewButtonCell> et <xref:System.Windows.Forms.DataGridViewButtonColumn> afin d’afficher les boutons désactivés dans une colonne de bouton.</span><span class="sxs-lookup"><span data-stu-id="c86c6-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="c86c6-117">Guide pratique pour héberger des contrôles dans des cellules DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="c86c6-118">Décrit comment implémenter l’interface `IDataGridViewEditingControl` et créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin d’afficher un contrôle <xref:System.Windows.Forms.DateTimePicker> quand une cellule est en mode édition.</span><span class="sxs-lookup"><span data-stu-id="c86c6-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c86c6-119">Référence</span><span class="sxs-lookup"><span data-stu-id="c86c6-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c86c6-120">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c86c6-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="c86c6-121">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="c86c6-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="c86c6-122">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="c86c6-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="c86c6-123">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="c86c6-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="c86c6-124">Fournit une documentation de référence pour l’interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="c86c6-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c86c6-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="c86c6-125">Related Sections</span></span>  
 [<span data-ttu-id="c86c6-126">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c86c6-127">Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellules.</span><span class="sxs-lookup"><span data-stu-id="c86c6-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86c6-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c86c6-128">See also</span></span>

- [<span data-ttu-id="c86c6-129">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="c86c6-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="c86c6-130">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c86c6-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
