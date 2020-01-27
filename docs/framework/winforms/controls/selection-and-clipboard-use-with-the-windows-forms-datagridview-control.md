---
title: Sélection et utilisation du presse-papiers avec le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 6993f77e8ce532d8df1bdc7e6b6abc1cc3268e49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743065"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="26eda-102">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="26eda-103">Le contrôle `DataGridView` vous fournit diverses options pour configurer la façon dont les utilisateurs peuvent sélectionner des cellules, des lignes et des colonnes.</span><span class="sxs-lookup"><span data-stu-id="26eda-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="26eda-104">Par exemple, vous pouvez activer une sélection unique ou multiple, sélectionner des lignes ou des colonnes entières lorsque les utilisateurs cliquent sur des cellules, ou sélectionner des lignes ou des colonnes entières uniquement quand les utilisateurs cliquent sur leurs en-têtes, ce qui active également la sélection de cellules.</span><span class="sxs-lookup"><span data-stu-id="26eda-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="26eda-105">Si vous souhaitez fournir votre propre interface utilisateur pour la sélection, vous pouvez désactiver la sélection ordinaire et gérer toutes les sélections par programmation.</span><span class="sxs-lookup"><span data-stu-id="26eda-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="26eda-106">En outre, vous pouvez permettre aux utilisateurs de copier les valeurs sélectionnées dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="26eda-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26eda-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="26eda-107">In This Section</span></span>  
 [<span data-ttu-id="26eda-108">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="26eda-109">Décrit les options pour l’utilisateur et la sélection par programmation dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="26eda-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="26eda-110">Guide pratique pour définir le mode de sélection du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="26eda-111">Décrit comment configurer le contrôle pour la sélection d’une seule ligne lorsqu’un utilisateur clique sur une cellule.</span><span class="sxs-lookup"><span data-stu-id="26eda-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="26eda-112">Guide pratique pour obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="26eda-113">Décrit comment utiliser les collections de cellules, de lignes et de colonnes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="26eda-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="26eda-114">Guide pratique pour permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers à partir du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="26eda-115">Décrit comment activer la prise en charge du presse-papiers dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="26eda-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="26eda-116">Reference</span><span class="sxs-lookup"><span data-stu-id="26eda-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="26eda-117">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="26eda-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="26eda-118">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="26eda-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="26eda-119">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="26eda-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="26eda-120">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>.</span><span class="sxs-lookup"><span data-stu-id="26eda-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="26eda-121">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="26eda-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="26eda-122">Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="26eda-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26eda-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26eda-123">See also</span></span>

- [<span data-ttu-id="26eda-124">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="26eda-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="26eda-125">Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26eda-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
