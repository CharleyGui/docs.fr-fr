---
title: 'Procédure : figer des colonnes dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 12c73d7344bba3ca36169c2f46134876295dee00
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651745"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Procédure : figer des colonnes dans le contrôle DataGridView Windows Forms
Quand des utilisateurs consultent des données affichées dans un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>, ils doivent parfois faire fréquemment référence à une même colonne ou un même ensemble de colonnes. Par exemple, lors de l'affichage d'un tableau d'informations sur des clients qui contient de nombreuses colonnes, il est utile d'afficher le nom du client en permanence tout en laissant d'autres colonnes défiler à l'extérieur de la zone visible.  
  
 Pour obtenir ce comportement, vous pouvez figer des colonnes dans le contrôle. Quand vous figez une colonne, toutes les colonnes à sa gauche (ou à sa droite dans les scripts de droite à gauche) sont aussi figées. Les colonnes figées restent en place, tandis que toutes les autres colonnes peuvent défiler.  
  
> [!NOTE]
>  Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées. Les utilisateurs peuvent repositionner des colonnes dans l'un ou l'autre groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.  
  
 La propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> d'une colonne détermine si la colonne est toujours visible dans la grille.  
  
 Cette tâche est prise en charge dans Visual Studio.  Voir également [Guide pratique pour Figer les colonnes dans les Windows Forms DataGridView Control à l’aide du concepteur](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Pour figer une colonne par programmation  
  
- Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `AddToCartButton` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Guide pratique pour Activer la réorganisation des colonnes dans le contrôle de DataGridView Windows Forms](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
