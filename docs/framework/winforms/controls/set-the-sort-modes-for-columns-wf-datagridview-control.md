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
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms
Dans le contrôle <xref:System.Windows.Forms.DataGridView>, les colonnes de zone de texte utilisent le tri automatique par défaut, tandis que les autres types de colonnes ne sont pas triés automatiquement. Il peut arriver que vous souhaitiez remplacer ces valeurs par défaut. Par exemple, vous pouvez afficher des images à la place de texte, de nombres ou de valeurs de cellules d’énumération. Si les images ne peuvent pas être triées, les valeurs sous-jacentes qu’elles représentent peuvent être triées.  
  
 Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> d’une colonne détermine son comportement de tri.  
  
 La procédure suivante montre l' `Priority` colonne de la rubrique [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Cette colonne est une colonne d’image et ne peut pas être triée par défaut. Elle contient des valeurs de cellule réelles qui sont des chaînes, mais elle peut donc être triée automatiquement.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Pour définir le mode de tri d’une colonne  
  
- définir la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> ;  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Priority` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Tri des données dans le contrôle DataGridView Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
