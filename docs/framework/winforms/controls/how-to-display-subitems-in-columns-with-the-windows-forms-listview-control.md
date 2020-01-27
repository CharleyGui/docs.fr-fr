---
title: Afficher des sous-éléments en colonnes avec le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745548"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Comment : afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.ListView> peut afficher du texte ou des sous-éléments supplémentaires pour chaque élément en mode Détails. La première colonne affiche le texte de l’élément, par exemple un numéro d’employé. Les colonnes deuxième, troisième et suivante affichent le premier, le deuxième, et les sous-éléments associés suivants.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Pour ajouter des sous-éléments à un élément de liste  
  
1. Ajoutez toutes les colonnes nécessaires. Étant donné que la première colonne affiche la propriété de <xref:System.Windows.Forms.ListView.Text%2A> de l’élément, vous avez besoin d’une colonne de plus qu’il n’y a de sous-éléments. Pour plus d’informations sur l’ajout de colonnes, consultez [Comment : ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Appelez la méthode <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> de la collection retournée par la propriété <xref:System.Windows.Forms.ListViewItem.SubItems%2A> d’un élément. L’exemple de code ci-dessous définit le nom et le département de l’employé pour un élément de liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
