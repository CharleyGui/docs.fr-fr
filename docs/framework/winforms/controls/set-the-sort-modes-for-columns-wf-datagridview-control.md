---
title: Définir les modes de tri des colonnes dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742998"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e9077-102">Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9077-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e9077-103">Dans le contrôle <xref:System.Windows.Forms.DataGridView>, les colonnes de zone de texte utilisent le tri automatique par défaut, tandis que les autres types de colonnes ne sont pas triés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e9077-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="e9077-104">Il peut arriver que vous souhaitiez remplacer ces valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9077-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="e9077-105">Par exemple, vous pouvez afficher des images à la place de texte, de nombres ou de valeurs de cellules d’énumération.</span><span class="sxs-lookup"><span data-stu-id="e9077-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="e9077-106">Si les images ne peuvent pas être triées, les valeurs sous-jacentes qu’elles représentent peuvent être triées.</span><span class="sxs-lookup"><span data-stu-id="e9077-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="e9077-107">Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> d’une colonne détermine son comportement de tri.</span><span class="sxs-lookup"><span data-stu-id="e9077-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="e9077-108">La procédure suivante montre l' `Priority` colonne de la rubrique [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e9077-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="e9077-109">Cette colonne est une colonne d’image et ne peut pas être triée par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9077-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="e9077-110">Elle contient des valeurs de cellule réelles qui sont des chaînes, mais elle peut donc être triée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e9077-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="e9077-111">Pour définir le mode de tri d’une colonne</span><span class="sxs-lookup"><span data-stu-id="e9077-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="e9077-112">définir la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="e9077-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e9077-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e9077-113">Compiling the Code</span></span>  
 <span data-ttu-id="e9077-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e9077-114">This example requires:</span></span>  
  
- <span data-ttu-id="e9077-115">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Priority` ;</span><span class="sxs-lookup"><span data-stu-id="e9077-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="e9077-116">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9077-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9077-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9077-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e9077-118">Tri des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9077-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e9077-119">Modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9077-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e9077-120">Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9077-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
