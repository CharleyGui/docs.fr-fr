---
title: Articles de groupe dans le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141989"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Comment : grouper des éléments dans un contrôle ListView Windows Forms
Avec la fonction de <xref:System.Windows.Forms.ListView> regroupement du contrôle, vous pouvez afficher des ensembles d’éléments connexes en groupes. Ces groupes sont séparés à l’écran par des en-têtes de groupe horizontaux qui contiennent les titres de groupe. Vous pouvez <xref:System.Windows.Forms.ListView> utiliser des groupes pour faciliter la navigation sur de grandes listes en groupant les éléments par ordre alphabétique, par date ou par tout autre groupement logique. L’image suivante montre certains éléments groupés.  
  
 ![Capture d’écran de groupes ListView impairs et même.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 Pour permettre le regroupement, vous devez d’abord créer un ou plusieurs groupes soit dans le concepteur ou programmatiquement. Une fois qu’un groupe <xref:System.Windows.Forms.ListView> a été défini, vous pouvez attribuer des éléments à des groupes. Vous pouvez également déplacer des éléments d’un groupe à un autre programmatiquement.  
  
### <a name="to-add-groups"></a>Pour ajouter des groupes  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Supprimer les groupes  
  
1. Utilisez <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode <xref:System.Windows.Forms.ListView.Groups%2A> ou la méthode de la collection.  
  
     La <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode supprime un seul groupe; la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode supprime tous les groupes de la liste.  
  
    > [!NOTE]
    > La suppression d’un groupe ne supprime pas les éléments de ce groupe.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Attribuer des articles à des groupes ou déplacer des éléments entre les groupes  
  
1. Réglez la <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriété des objets individuels.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d'ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
