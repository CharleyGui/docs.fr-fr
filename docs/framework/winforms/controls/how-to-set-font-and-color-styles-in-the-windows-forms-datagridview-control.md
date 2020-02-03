---
title: Définir des styles de police et de couleur dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746759"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Comment : définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms
Vous pouvez spécifier l'apparence visuelle des cellules dans un contrôle <xref:System.Windows.Forms.DataGridView> en définissant les propriétés de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>. Vous pouvez récupérer des instances de cette classe à partir de différentes propriétés de la classe <xref:System.Windows.Forms.DataGridView> et de ses classes auxiliaires ou vous pouvez instancier des objets <xref:System.Windows.Forms.DataGridViewCellStyle> à assigner à ces propriétés.  
  
 Les procédures suivantes illustrent la personnalisation de base de l'apparence des cellules à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Chaque cellule du contrôle hérite des styles spécifiés via cette propriété, sauf s'ils sont substitués au niveau de la cellule, de la ligne ou de la colonne. Pour obtenir un exemple d’héritage de style, consultez [Comment : définir des styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Pour plus d'informations sur les autres utilisations de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>, consultez les rubriques répertoriées dans la section Voir aussi.  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  Consultez également [Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l’aide du concepteur](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>Pour spécifier la police utilisée par les cellules DataGridView  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> pour définir la police pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>Pour spécifier les couleurs de premier plan et d'arrière-plan des cellules DataGridView  
  
- Définissez les propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> pour définir ces styles pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Pour spécifier les couleurs de premier plan et d'arrière-plan des cellules DataGridView sélectionnées  
  
- Définissez les propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> pour définir ces styles pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour bénéficier d'une extensibilité maximale, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour chaque élément séparément. Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
