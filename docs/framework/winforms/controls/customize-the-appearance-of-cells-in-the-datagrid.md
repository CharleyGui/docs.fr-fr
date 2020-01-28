---
title: Personnaliser l’apparence des cellules dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744055"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="113f8-102">Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="113f8-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="113f8-103">Vous pouvez personnaliser l’apparence d’une cellule en gérant l’événement <xref:System.Windows.Forms.DataGridView.CellPainting> du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="113f8-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="113f8-104">Vous pouvez extraire le <xref:System.Drawing.Graphics> du contrôle <xref:System.Windows.Forms.DataGridView> à partir de la propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> de l' <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="113f8-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="113f8-105">Avec cette <xref:System.Drawing.Graphics>, vous pouvez affecter l’apparence du contrôle <xref:System.Windows.Forms.DataGridView> entier, mais vous ne souhaitez généralement affecter que l’apparence de la cellule actuellement peinte.</span><span class="sxs-lookup"><span data-stu-id="113f8-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="113f8-106">La propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> du <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> vous permet de limiter vos opérations de peinture à la cellule qui est actuellement peinte.</span><span class="sxs-lookup"><span data-stu-id="113f8-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="113f8-107">Dans l’exemple de code suivant, vous allez peindre toutes les cellules d’une colonne `ContactName` à l’aide du modèle de couleurs du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="113f8-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="113f8-108">Le contenu de texte de chaque cellule est peint dans <xref:System.Drawing.Color.Crimson%2A>, et un rectangle incrusté est dessiné dans la même couleur que la propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="113f8-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="113f8-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="113f8-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="113f8-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="113f8-110">Compiling the Code</span></span>  
 <span data-ttu-id="113f8-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="113f8-111">This example requires:</span></span>  
  
- <span data-ttu-id="113f8-112">Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` avec une colonne `ContactName` telle que celle de la table Customers dans l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="113f8-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="113f8-113">Références aux assemblys System, System.Windows.Form et System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="113f8-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113f8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="113f8-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="113f8-115">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="113f8-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
