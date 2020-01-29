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
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms
Toutes les données ne sont pas censées être modifiées. Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété de la colonne <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> détermine si les utilisateurs peuvent modifier des cellules dans cette colonne. Pour plus d’informations sur la façon de rendre le contrôle entièrement en lecture seule, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](prevent-row-addition-and-deletion-datagridview.md).  
  
 Cette tâche est prise en charge dans Visual Studio.  Consultez également [Comment : définir des colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur](make-columns-read-only-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Pour configurer une colonne en lecture seule par programmation  
  
- Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` avec une colonne nommée `CompanyName` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Guide pratique pour empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](prevent-row-addition-and-deletion-datagridview.md)
