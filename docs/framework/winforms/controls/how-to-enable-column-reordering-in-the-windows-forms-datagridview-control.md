---
title: 'Procédure : activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: c4c92a51f2e209f814ac34b39a0c6ba35f0bf56b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651728"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Procédure : activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms
Quand vous activez la réorganisation des colonnes dans le contrôle <xref:System.Windows.Forms.DataGridView>, les utilisateurs peuvent déplacer une colonne vers une nouvelle position en faisant glisser l'en-tête de colonne avec la souris. Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> détermine si les utilisateurs peuvent déplacer des colonnes vers d'autres positions.  
  
 Cette tâche est prise en charge dans Visual Studio.  Voir également [Guide pratique pour Activer la réorganisation des colonnes dans les Windows Forms DataGridView Control à l’aide du concepteur](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Pour activer la réorganisation des colonnes par programmation  
  
- Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Guide pratique pour Figer des colonnes dans le contrôle de DataGridView Windows Forms](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
