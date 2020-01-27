---
title: Définir les styles de cellules par défaut pour le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744871"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms
Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des styles de cellules par défaut pour le contrôle entier et pour des colonnes et des lignes spécifiques. Ces valeurs par défaut sont propagées du niveau contrôle au niveau colonne, puis au niveau ligne, et enfin au niveau cellule. Si une propriété <xref:System.Windows.Forms.DataGridViewCellStyle> spécifique n'est pas définie au niveau de la cellule, le paramètre de propriété par défaut au niveau de la ligne est utilisé. Si la propriété n'est pas définie non plus au niveau de la ligne, le paramètre de colonne par défaut est utilisé. Pour finir, si la propriété n'est pas non plus définie au niveau de la colonne, le paramètre <xref:System.Windows.Forms.DataGridView> par défaut est utilisé. Avec ce paramètre, vous pouvez éviter de devoir dupliquer les paramètres de propriétés à plusieurs niveaux. À chaque niveau, il vous suffit de spécifier les styles qui diffèrent des niveaux au-dessus de lui. Pour plus d’informations, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  Consultez également [Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l’aide du concepteur](default-cell-styles-datagridview.md).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Pour définir les styles de cellules par défaut par programmation  
  
1. Définissez les propriétés du <xref:System.Windows.Forms.DataGridViewCellStyle> récupéré via la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. Créez et initialisez de nouveaux objets <xref:System.Windows.Forms.DataGridViewCellStyle> pour une utilisation par plusieurs lignes et colonnes.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. Définissez la propriété `DefaultCellStyle` de lignes et de colonnes spécifiques.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour bénéficier d'une extensibilité maximale quand vous travaillez avec des jeux de données très volumineux, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour les différents éléments. En outre, vous devez créer des lignes partagées et y accéder à l'aide de la propriété <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Guide pratique pour définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
