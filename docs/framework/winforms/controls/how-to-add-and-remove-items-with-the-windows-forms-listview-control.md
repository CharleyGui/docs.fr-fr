---
title: Ajouter et supprimer des éléments avec le contrôle ListView
description: Découvrez comment ajouter et supprimer un élément avec le contrôle Windows Forms ListView en spécifiant l’élément et en lui assignant des propriétés.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618088"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms
Le processus d’ajout d’un élément à un <xref:System.Windows.Forms.ListView> contrôle Windows Forms consiste principalement à spécifier l’élément et à lui assigner des propriétés. L’ajout ou la suppression d’éléments de liste peut être effectué à tout moment.  
  
### <a name="to-add-items-programmatically"></a>Pour ajouter des éléments par programmation  
  
1. Utilisez la <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> méthode de la <xref:System.Windows.Forms.ListView.Items%2A> propriété.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Pour supprimer des éléments par programmation  
  
1. Utilisez la <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> méthode ou de la <xref:System.Windows.Forms.ListView.Items%2A> propriété. La <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> méthode supprime un seul élément ; la <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> méthode supprime tous les éléments de la liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d'ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
