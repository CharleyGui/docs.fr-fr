---
title: Ajouter et supprimer des éléments avec le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743137"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms
Le processus d’ajout d’un élément à un contrôle Windows Forms <xref:System.Windows.Forms.ListView> consiste principalement à spécifier l’élément et à lui assigner des propriétés. L’ajout ou la suppression d’éléments de liste peut être effectué à tout moment.  
  
### <a name="to-add-items-programmatically"></a>Pour ajouter des éléments par programmation  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Pour supprimer des éléments par programmation  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> de la propriété <xref:System.Windows.Forms.ListView.Items%2A>. La méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> supprime un seul élément ; la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> supprime tous les éléments de la liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- [ListView, contrôle](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
