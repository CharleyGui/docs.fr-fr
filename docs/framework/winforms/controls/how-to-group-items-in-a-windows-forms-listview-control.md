---
title: Grouper les éléments dans le contrôle ListView
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
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736628"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Comment : grouper des éléments dans un contrôle ListView Windows Forms
Avec la fonctionnalité de regroupement du contrôle <xref:System.Windows.Forms.ListView>, vous pouvez afficher des jeux d’éléments associés dans des groupes. Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes. Vous pouvez utiliser des groupes de <xref:System.Windows.Forms.ListView> pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique. L’illustration suivante montre des éléments groupés.  
  
 ![Capture d’écran des groupes de ListView impaires et pairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Pour activer le regroupement, vous devez d’abord créer un ou plusieurs groupes dans le concepteur ou par programme. Une fois qu’un groupe a été défini, vous pouvez assigner <xref:System.Windows.Forms.ListView> éléments à des groupes. Vous pouvez également déplacer des éléments d’un groupe à un autre par programmation.  
  
### <a name="to-add-groups"></a>Pour ajouter des groupes  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Pour supprimer des groupes  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     La méthode <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> supprime un seul groupe ; la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> supprime tous les groupes de la liste.  
  
    > [!NOTE]
    > La suppression d’un groupe ne supprime pas les éléments de ce groupe.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Pour affecter des éléments à des groupes ou déplacer des éléments entre des groupes  
  
1. Définissez la propriété <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> d’éléments individuels.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
