---
title: Définir les colonnes en lecture seule dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736183"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="68531-102">Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68531-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="68531-103">Toutes les données ne sont pas censées être modifiées.</span><span class="sxs-lookup"><span data-stu-id="68531-103">Not all data is meant for editing.</span></span> <span data-ttu-id="68531-104">Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété de la colonne <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> détermine si les utilisateurs peuvent modifier des cellules dans cette colonne.</span><span class="sxs-lookup"><span data-stu-id="68531-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="68531-105">Pour plus d’informations sur la façon de rendre le contrôle entièrement en lecture seule, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="68531-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="68531-106">Cette tâche est prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68531-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="68531-107">Consultez également [Comment : définir des colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="68531-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="68531-108">Pour configurer une colonne en lecture seule par programmation</span><span class="sxs-lookup"><span data-stu-id="68531-108">To make a column read-only programmatically</span></span>  
  
- <span data-ttu-id="68531-109">Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="68531-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68531-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="68531-110">Compiling the Code</span></span>  
 <span data-ttu-id="68531-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="68531-111">This example requires:</span></span>  
  
- <span data-ttu-id="68531-112">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` avec une colonne nommée `CompanyName` ;</span><span class="sxs-lookup"><span data-stu-id="68531-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
- <span data-ttu-id="68531-113">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68531-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68531-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68531-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="68531-115">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68531-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="68531-116">Guide pratique pour empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68531-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
