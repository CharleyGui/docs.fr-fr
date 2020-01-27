---
title: Personnaliser le tri dans un contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743177"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Comment : personnaliser le tri dans le contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> assure le tri automatique mais, selon vos besoins, vous devrez peut-être personnaliser les opérations de tri. Par exemple, vous pouvez utiliser le tri par programmation pour créer une autre interface utilisateur. Vous pouvez également gérer l'événement <xref:System.Windows.Forms.DataGridView.SortCompare> ou appeler la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> pour bénéficier d'une plus grande flexibilité de tri, par exemple pour trier plusieurs colonnes.  
  
 Les exemples de code suivants illustrent ces trois approches de tri personnalisé. Pour plus d’informations, consultez [Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Tri par programmation  
 L'exemple de code suivant illustre un tri par programmation qui fait appel aux propriétés <xref:System.Windows.Forms.DataGridView.SortOrder%2A> et <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> pour déterminer le sens du tri et à la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> pour définir manuellement le glyphe de tri. La surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> sert à trier les données dans une seule colonne.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Tri personnalisé à l'aide de l'événement SortCompare  
 L'exemple de code suivant illustre un tri personnalisé qui fait appel à un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.SortCompare>. Le <xref:System.Windows.Forms.DataGridViewColumn> sélectionné est trié et, si la colonne contient des valeurs en double, l'ID de colonne est utilisé pour déterminer l'ordre final.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Tri personnalisé à l'aide de l'interface IComparer  
 L'exemple de code suivant illustre un tri personnalisé qui fait appel à la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>, qui prend une implémentation de l'interface <xref:System.Collections.IComparer> pour effectuer un tri sur plusieurs colonnes.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples nécessitent :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Tri des données dans le contrôle DataGridView Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
