---
title: Ajouter des info-bulles à des cellules individuelles dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732182"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="5cbc1-102">Comment : ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cbc1-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5cbc1-103">Par défaut, les info-bulles sont utilisées pour afficher les valeurs de <xref:System.Windows.Forms.DataGridView> cellules trop petites pour afficher l’intégralité de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="5cbc1-104">Toutefois, vous pouvez remplacer ce comportement pour définir des valeurs de texte info-bulle pour des cellules individuelles.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="5cbc1-105">Cela est utile pour afficher des informations supplémentaires sur une cellule pour les utilisateurs ou pour fournir aux utilisateurs une autre description du contenu des cellules.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="5cbc1-106">Par exemple, si vous avez une ligne qui affiche des icônes d’État, vous souhaiterez peut-être fournir des explications de texte à l’aide d’info-bulles.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="5cbc1-107">Vous pouvez également désactiver l’affichage des info-bulles au niveau de la cellule en affectant à la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="5cbc1-108">Pour ajouter une info-bulle à une cellule</span><span class="sxs-lookup"><span data-stu-id="5cbc1-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="5cbc1-109">définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="5cbc1-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cbc1-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5cbc1-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="5cbc1-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="5cbc1-111">This example requires:</span></span>  
  
- <span data-ttu-id="5cbc1-112">Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Rating` pour afficher les valeurs de chaîne de 1 à 4 symboles d’astérisques (« \* »).</span><span class="sxs-lookup"><span data-stu-id="5cbc1-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="5cbc1-113">L’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> du contrôle doit être associé à la méthode de gestionnaire d’événements illustrée dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="5cbc1-114">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5cbc1-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5cbc1-115">Robust Programming</span></span>  
 <span data-ttu-id="5cbc1-116">Lorsque vous liez le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données externe ou que vous fournissez votre propre source de données en implémentant le mode virtuel, vous pouvez rencontrer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="5cbc1-117">Pour éviter une altération des performances lorsque vous travaillez avec de grandes quantités de données, gérez l’événement <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> plutôt que de définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> de plusieurs cellules.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="5cbc1-118">Lorsque vous gérez cet événement, l’obtention de la valeur d’une cellule <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété déclenche l’événement et retourne la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> telle que spécifiée dans le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5cbc1-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cbc1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cbc1-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5cbc1-120">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cbc1-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
