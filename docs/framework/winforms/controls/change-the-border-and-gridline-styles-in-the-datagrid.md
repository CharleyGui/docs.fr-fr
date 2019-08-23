---
title: 'Procédure : modifier les styles de bordure et de quadrillage dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917670"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Procédure : modifier les styles de bordure et de quadrillage dans le contrôle DataGridView Windows Forms
Avec le <xref:System.Windows.Forms.DataGridView> contrôle, vous pouvez personnaliser l’apparence de la bordure et du quadrillage du contrôle pour améliorer l’expérience utilisateur. Vous pouvez modifier la couleur du quadrillage et le style de bordure du contrôle en plus des styles de bordure pour les cellules dans le contrôle. Vous pouvez également appliquer différents styles de bordure de cellule pour les cellules ordinaires, les cellules d’en-tête de ligne et les cellules d’en-tête de colonne.  
  
> [!NOTE]
> La couleur du quadrillage est utilisée uniquement avec <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>les <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>valeurs, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> et de l' <xref:System.Windows.Forms.DataGridViewCellBorderStyle> énumération et <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> la valeur de <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> l’énumération. Les autres valeurs de ces énumérations utilisent des couleurs spécifiées par le système d’exploitation. En outre, lorsque les styles visuels sont activés sur Windows XP et la famille Windows Server 2003 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> par le biais <xref:System.Windows.Forms.DataGridView.GridColor%2A> de la méthode, la valeur de la propriété n’est pas utilisée.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Pour modifier la couleur du quadrillage par programmation  
  
- définir la propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A> ;  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Pour modifier par programmation le style de bordure du contrôle DataGridView entier  
  
- Affectez l'une des valeurs de l'énumération <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> à la propriété <xref:System.Windows.Forms.BorderStyle>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Pour modifier par programme les styles de bordure des cellules DataGridView  
  
- Définissez les <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>propriétés <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, et <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
