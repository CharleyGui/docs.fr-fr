---
title: 'Procédure : personnaliser l’aspect des cellules dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 9b07c139689a9776f6f901c0f9fbe9d2d0303d56
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648145"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3ed16-102">Procédure : personnaliser l’aspect des cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ed16-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3ed16-103">Vous pouvez personnaliser l’apparence de n’importe quelle cellule en gérant la <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.CellPainting> événement.</span><span class="sxs-lookup"><span data-stu-id="3ed16-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="3ed16-104">Vous pouvez extraire le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Drawing.Graphics> à partir de la <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> propriété de la <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="3ed16-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="3ed16-105">Avec cette <xref:System.Drawing.Graphics>, vous pouvez affecter l’apparence de tout le <xref:System.Windows.Forms.DataGridView> contrôle, mais vous souhaiterez habituellement affectent uniquement l’apparence de la cellule qui est actuellement peint.</span><span class="sxs-lookup"><span data-stu-id="3ed16-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="3ed16-106">Le <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> propriété de la <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> vous permet de limiter vos opérations de peinture à la cellule qui est actuellement peint.</span><span class="sxs-lookup"><span data-stu-id="3ed16-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="3ed16-107">Dans l’exemple de code suivant, vous sera chargée de peindre toutes les cellules dans un `ContactName` à l’aide de la colonne la <xref:System.Windows.Forms.DataGridView> modèle de couleurs du contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ed16-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="3ed16-108">Contenu de texte de chaque cellule est peint dans <xref:System.Drawing.Color.Crimson%2A>, et un rectangle d’incrustation est dessiné dans la même couleur que le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.GridColor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="3ed16-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed16-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ed16-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ed16-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3ed16-110">Compiling the Code</span></span>  
 <span data-ttu-id="3ed16-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3ed16-111">This example requires:</span></span>  
  
- <span data-ttu-id="3ed16-112">Un <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` avec un `ContactName` colonne tel que celui de la table Customers dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="3ed16-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="3ed16-113">Références aux assemblys System, System.Windows.Form et System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="3ed16-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed16-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ed16-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="3ed16-115">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ed16-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
