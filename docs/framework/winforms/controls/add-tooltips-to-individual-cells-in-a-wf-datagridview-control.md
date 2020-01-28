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
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Comment : ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms
Par défaut, les info-bulles sont utilisées pour afficher les valeurs de <xref:System.Windows.Forms.DataGridView> cellules trop petites pour afficher l’intégralité de leur contenu. Toutefois, vous pouvez remplacer ce comportement pour définir des valeurs de texte info-bulle pour des cellules individuelles. Cela est utile pour afficher des informations supplémentaires sur une cellule pour les utilisateurs ou pour fournir aux utilisateurs une autre description du contenu des cellules. Par exemple, si vous avez une ligne qui affiche des icônes d’État, vous souhaiterez peut-être fournir des explications de texte à l’aide d’info-bulles.  
  
 Vous pouvez également désactiver l’affichage des info-bulles au niveau de la cellule en affectant à la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> la valeur `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Pour ajouter une info-bulle à une cellule  
  
- définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> ;  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Cet exemple nécessite :  
  
- Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Rating` pour afficher les valeurs de chaîne de 1 à 4 symboles d’astérisques (« * »). L’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> du contrôle doit être associé à la méthode de gestionnaire d’événements illustrée dans l’exemple.  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Lorsque vous liez le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données externe ou que vous fournissez votre propre source de données en implémentant le mode virtuel, vous pouvez rencontrer des problèmes de performances. Pour éviter une altération des performances lorsque vous travaillez avec de grandes quantités de données, gérez l’événement <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> plutôt que de définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> de plusieurs cellules. Lorsque vous gérez cet événement, l’obtention de la valeur d’une cellule <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété déclenche l’événement et retourne la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> telle que spécifiée dans le gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
