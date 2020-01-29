---
title: Mise en forme et style de base dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731997"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="89d29-102">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="89d29-103">Le contrôle `DataGridView` permet de définir facilement l’apparence de base des cellules et le format d’affichage des valeurs de cellule.</span><span class="sxs-lookup"><span data-stu-id="89d29-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="89d29-104">Vous pouvez définir l’apparence et les styles de mise en forme pour des cellules individuelles, pour des cellules dans des colonnes et des lignes spécifiques, ou pour toutes les cellules du contrôle en définissant les propriétés des objets `DataGridViewCellStyle` accessibles par le biais de différentes propriétés de contrôle `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="89d29-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="89d29-105">En outre, vous pouvez modifier ces styles de manière dynamique en fonction de facteurs tels que la valeur de la cellule en gérant l’événement `CellFormatting`.</span><span class="sxs-lookup"><span data-stu-id="89d29-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89d29-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="89d29-106">In This Section</span></span>  
 [<span data-ttu-id="89d29-107">Guide pratique pour modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="89d29-108">Décrit comment définir des propriétés de `DataGridView` qui définissent l’apparence de la bordure du contrôle et les lignes limites entre les cellules.</span><span class="sxs-lookup"><span data-stu-id="89d29-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="89d29-109">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-110">Décrit la classe `DataGridViewCellStyle` et la manière dont les propriétés de ce type interagissent pour définir le mode d’affichage des cellules dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="89d29-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="89d29-111">Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-112">Décrit comment utiliser des propriétés de `DataGridViewCellStyle` pour définir l’apparence par défaut des cellules dans des lignes et des colonnes spécifiques et dans le contrôle entier.</span><span class="sxs-lookup"><span data-stu-id="89d29-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="89d29-113">Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-114">Décrit comment mettre en forme les valeurs d’affichage des cellules à l’aide de `DataGridViewCellStyle` propriétés.</span><span class="sxs-lookup"><span data-stu-id="89d29-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="89d29-115">Guide pratique pour définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-116">Décrit comment utiliser la propriété `DefaultCellStyle` pour définir les caractéristiques d’affichage de base pour toutes les cellules du contrôle.</span><span class="sxs-lookup"><span data-stu-id="89d29-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="89d29-117">Guide pratique pour définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-118">Décrit comment créer un effet de type comptabilité dans le contrôle à l’aide de lignes en alternance qui s’affichent différemment.</span><span class="sxs-lookup"><span data-stu-id="89d29-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="89d29-119">Guide pratique pour utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="89d29-120">Décrit comment utiliser la propriété `RowTemplate` pour définir les propriétés de ligne qui seront utilisées pour toutes les lignes du contrôle.</span><span class="sxs-lookup"><span data-stu-id="89d29-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="89d29-121">Reference</span><span class="sxs-lookup"><span data-stu-id="89d29-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="89d29-122">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="89d29-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="89d29-123">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="89d29-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="89d29-124">Fournit une documentation de référence pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.</span><span class="sxs-lookup"><span data-stu-id="89d29-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="89d29-125">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="89d29-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="89d29-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="89d29-126">Related Sections</span></span>  
 [<span data-ttu-id="89d29-127">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="89d29-128">Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.</span><span class="sxs-lookup"><span data-stu-id="89d29-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="89d29-129">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89d29-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="89d29-130">Fournit des rubriques qui décrivent les propriétés de cellule, de ligne et de colonne couramment utilisées.</span><span class="sxs-lookup"><span data-stu-id="89d29-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d29-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89d29-131">See also</span></span>

- [<span data-ttu-id="89d29-132">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="89d29-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
