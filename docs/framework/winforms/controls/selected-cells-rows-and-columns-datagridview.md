---
title: 'Procédure : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960513"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bbfcb-102">Procédure : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbfcb-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bbfcb-103">Vous pouvez obtenir les cellules, lignes ou colonnes sélectionnées à partir d' <xref:System.Windows.Forms.DataGridView> un contrôle à l’aide des propriétés <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>correspondantes: <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>et.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="bbfcb-104">Dans les procédures suivantes, vous allez obtenir les cellules sélectionnées et afficher leurs index de lignes et de colonnes dans <xref:System.Windows.Forms.MessageBox>un.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="bbfcb-105">Pour obtenir les cellules sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="bbfcb-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="bbfcb-106">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bbfcb-107">Utilisez la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> méthode pour éviter d’avoir un nombre potentiellement important de cellules.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="bbfcb-108">Pour obtenir les lignes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="bbfcb-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="bbfcb-109">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="bbfcb-110">Pour permettre aux utilisateurs de sélectionner des lignes, vous devez <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> affecter à <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> la <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>propriété la valeur ou.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="bbfcb-111">Pour obtenir les colonnes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="bbfcb-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="bbfcb-112">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="bbfcb-113">Pour permettre aux utilisateurs de sélectionner des colonnes, vous devez <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> affecter à <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> la <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>propriété la valeur ou.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbfcb-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bbfcb-114">Compiling the Code</span></span>  
 <span data-ttu-id="bbfcb-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="bbfcb-115">This example requires:</span></span>  
  
- <span data-ttu-id="bbfcb-116"><xref:System.Windows.Forms.Button>les contrôles `selectedCellsButton`nommés `selectedRowsButton`, et `selectedColumnsButton`, chacun avec des gestionnaires pour l' <xref:System.Windows.Forms.Control.Click> événement attaché.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="bbfcb-117">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="bbfcb-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="bbfcb-118">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Text?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bbfcb-119">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="bbfcb-119">Robust Programming</span></span>  
 <span data-ttu-id="bbfcb-120">Les collections décrites dans cette rubrique ne s’exécutent pas efficacement quand un grand nombre de cellules, de lignes ou de colonnes est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="bbfcb-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="bbfcb-121">Pour plus d’informations sur l’utilisation de ces collections avec de grandes quantités de données, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bbfcb-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfcb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbfcb-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="bbfcb-123">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbfcb-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
