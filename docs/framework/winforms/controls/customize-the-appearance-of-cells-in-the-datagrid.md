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
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms
Vous pouvez personnaliser l’apparence d’une cellule en gérant l’événement <xref:System.Windows.Forms.DataGridView.CellPainting> du contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez extraire le <xref:System.Drawing.Graphics> du contrôle <xref:System.Windows.Forms.DataGridView> à partir de la propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> de l' <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Avec cette <xref:System.Drawing.Graphics>, vous pouvez affecter l’apparence du contrôle <xref:System.Windows.Forms.DataGridView> entier, mais vous ne souhaitez généralement affecter que l’apparence de la cellule actuellement peinte. La propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> du <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> vous permet de limiter vos opérations de peinture à la cellule qui est actuellement peinte.  
  
 Dans l’exemple de code suivant, vous allez peindre toutes les cellules d’une colonne `ContactName` à l’aide du modèle de couleurs du contrôle <xref:System.Windows.Forms.DataGridView>. Le contenu de texte de chaque cellule est peint dans <xref:System.Drawing.Color.Crimson%2A>, et un rectangle incrusté est dessiné dans la même couleur que la propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` avec une colonne `ContactName` telle que celle de la table Customers dans l’exemple de base de données Northwind.  
  
- Références aux assemblys System, System.Windows.Form et System.Drawing.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
