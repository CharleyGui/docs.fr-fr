---
title: Obtient les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView
description: Découvrez comment obtenir les cellules, lignes ou colonnes sélectionnées à partir d’un contrôle DataGridView à l’aide des propriétés correspondantes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904167"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="57151-103">Comment : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57151-103">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="57151-104">Vous pouvez obtenir les cellules, lignes ou colonnes sélectionnées à partir d’un <xref:System.Windows.Forms.DataGridView> contrôle à l’aide des propriétés correspondantes : <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> .</span><span class="sxs-lookup"><span data-stu-id="57151-104">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="57151-105">Dans les procédures suivantes, vous allez obtenir les cellules sélectionnées et afficher leurs index de lignes et de colonnes dans un <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="57151-105">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="57151-106">Pour obtenir les cellules sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="57151-106">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="57151-107">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.</span><span class="sxs-lookup"><span data-stu-id="57151-107">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="57151-108">Utilisez la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> méthode pour éviter d’avoir un nombre potentiellement important de cellules.</span><span class="sxs-lookup"><span data-stu-id="57151-108">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="57151-109">Pour obtenir les lignes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="57151-109">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="57151-110">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="57151-110">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="57151-111">Pour permettre aux utilisateurs de sélectionner des lignes, vous devez affecter à la propriété la valeur <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="57151-111">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="57151-112">Pour obtenir les colonnes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="57151-112">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="57151-113">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="57151-113">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="57151-114">Pour permettre aux utilisateurs de sélectionner des colonnes, vous devez affecter à la propriété la valeur <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="57151-114">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57151-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="57151-115">Compiling the Code</span></span>  
 <span data-ttu-id="57151-116">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="57151-116">This example requires:</span></span>  
  
- <span data-ttu-id="57151-117"><xref:System.Windows.Forms.Button>les contrôles nommés `selectedCellsButton` , `selectedRowsButton` et `selectedColumnsButton` , chacun avec des gestionnaires pour l' <xref:System.Windows.Forms.Control.Click> événement attaché.</span><span class="sxs-lookup"><span data-stu-id="57151-117"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="57151-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="57151-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="57151-119">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Text?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="57151-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57151-120">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="57151-120">Robust Programming</span></span>  
 <span data-ttu-id="57151-121">Les collections décrites dans cette rubrique ne s’exécutent pas efficacement quand un grand nombre de cellules, de lignes ou de colonnes est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="57151-121">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="57151-122">Pour plus d’informations sur l’utilisation de ces collections avec de grandes quantités de données, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="57151-122">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57151-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57151-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="57151-124">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57151-124">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
