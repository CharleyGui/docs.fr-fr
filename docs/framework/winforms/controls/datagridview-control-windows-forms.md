---
title: DataGridView, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: fc40c0f08c0c11fa9acc94ce12caab8766658f1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746951"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="c6b88-102">DataGridView, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c6b88-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="c6b88-103">Le contrôle `DataGridView` offre un moyen puissant et flexible d'afficher des données sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="c6b88-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="c6b88-104">Vous pouvez utiliser le contrôle `DataGridView` pour afficher des vues en lecture seule d'une petite quantité de données ou vous pouvez le mettre à l'échelle pour afficher des vues modifiables de groupes de données très volumineux.</span><span class="sxs-lookup"><span data-stu-id="c6b88-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="c6b88-105">Vous pouvez étendre le contrôle `DataGridView` de plusieurs façons pour générer des comportements personnalisés dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="c6b88-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="c6b88-106">Par exemple, vous pouvez spécifier par programmation vos propres algorithmes de tri et vous pouvez créer vos propres types de cellules.</span><span class="sxs-lookup"><span data-stu-id="c6b88-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="c6b88-107">Vous pouvez facilement personnaliser l'apparence du contrôle `DataGridView` en choisissant parmi plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="c6b88-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="c6b88-108">Vous pouvez utiliser plusieurs types de magasins de données comme source de données ou utiliser le contrôle `DataGridView` sans le lier à aucune source de données.</span><span class="sxs-lookup"><span data-stu-id="c6b88-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="c6b88-109">Les rubriques de cette section décrivent les concepts et techniques que vous pouvez utiliser pour générer des fonctionnalités `DataGridView` dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="c6b88-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6b88-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c6b88-110">In This Section</span></span>  
 [<span data-ttu-id="c6b88-111">Vue d’ensemble du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c6b88-111">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="c6b88-112">Fournit des rubriques qui décrivent l'architecture et les principaux concepts du contrôle Windows Forms `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="c6b88-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="c6b88-113">Fonctionnalités par défaut du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-114">Décrit l'apparence et le comportement par défaut du contrôle Windows Forms `DataGridView` quand il est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="c6b88-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="c6b88-115">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-115">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-116">Décrit les types de colonnes dans le contrôle Windows Forms `DataGridView`, utilisé pour afficher des données et permettre aux utilisateurs de modifier ou d'ajouter des données.</span><span class="sxs-lookup"><span data-stu-id="c6b88-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="c6b88-117">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="c6b88-118">Fournit des rubriques qui décrivent les propriétés de cellules, de lignes et de colonnes communément utilisées.</span><span class="sxs-lookup"><span data-stu-id="c6b88-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="c6b88-119">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-120">Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellules.</span><span class="sxs-lookup"><span data-stu-id="c6b88-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="c6b88-121">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-122">Fournit des rubriques qui décrivent comment remplir le contrôle de données manuellement ou à partir d'une source de données externe.</span><span class="sxs-lookup"><span data-stu-id="c6b88-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="c6b88-123">Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-124">Fournit des rubriques qui décrivent comment ajuster automatiquement la taille des lignes et des colonnes pour qu'elle corresponde au contenu de la cellule ou à la largeur disponible du contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6b88-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="c6b88-125">Tri des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-126">Fournit des rubriques qui décrivent les fonctionnalités de tri dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6b88-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="c6b88-127">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-127">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-128">Fournit des rubriques qui décrivent comment modifier la façon dont les utilisateurs ajoutent et modifient des données dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6b88-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="c6b88-129">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-130">Fournit des rubriques qui décrivent les fonctionnalités de sélection de cellules, de lignes et de colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6b88-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="c6b88-131">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="c6b88-132">Fournit des rubriques qui expliquent comment programmer avec des objets de colonnes, de lignes et de cellules.</span><span class="sxs-lookup"><span data-stu-id="c6b88-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="c6b88-133">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-133">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-134">Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes `DataGridView` et la création de types de lignes, de colonnes et de cellules dérivés.</span><span class="sxs-lookup"><span data-stu-id="c6b88-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="c6b88-135">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-136">Fournit des rubriques qui expliquent comment utiliser efficacement le contrôle pour éviter les problèmes de performances lors de l'utilisation de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="c6b88-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="c6b88-137">Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c6b88-138">Décrit comment les utilisateurs peuvent interagir avec le contrôle `DataGridView` via un clavier et une souris.</span><span class="sxs-lookup"><span data-stu-id="c6b88-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="c6b88-139">Différences entre les contrôles DataGridView et DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="c6b88-140">Décrit dans quelle mesure le contrôle `DataGridView` améliore et remplace le contrôle <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="c6b88-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="c6b88-141">Consultez également [utilisation du concepteur avec le contrôle Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c6b88-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c6b88-142">Reference</span><span class="sxs-lookup"><span data-stu-id="c6b88-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c6b88-143">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c6b88-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="c6b88-144">Fournit la documentation de référence pour le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="c6b88-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="c6b88-145">Le contrôle <xref:System.Windows.Forms.DataGridView> et le composant <xref:System.Windows.Forms.BindingSource> sont conçus pour fonctionner étroitement ensemble.</span><span class="sxs-lookup"><span data-stu-id="c6b88-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b88-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6b88-146">See also</span></span>

- [<span data-ttu-id="c6b88-147">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6b88-147">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
