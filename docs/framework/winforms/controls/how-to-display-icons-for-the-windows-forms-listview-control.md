---
title: Afficher les icônes pour le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744508"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Comment : afficher des icônes pour le contrôle ListView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.ListView> peut afficher des icônes de trois listes d’images. Les vues List, Details et SmallIcon affichent les images de la liste d’images spécifiée dans la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A>. La vue LargeIcon affiche les images de la liste d’images spécifiée dans la propriété <xref:System.Windows.Forms.ListView.LargeImageList%2A>. Un affichage de liste peut également afficher un ensemble d’icônes supplémentaire, défini dans la propriété <xref:System.Windows.Forms.ListView.StateImageList%2A>, en regard des grandes ou petites icônes. Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Pour afficher des images en mode liste  
  
1. Définissez la propriété appropriée (<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>ou <xref:System.Windows.Forms.ListView.StateImageList%2A>) sur le composant <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.  
  
     Ces propriétés peuvent être définies dans le concepteur avec l’Fenêtre Propriétés, ou dans le code.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Définissez la propriété <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> pour chaque élément de liste associé à une icône.  
  
     Ces propriétés peuvent être définies dans le code ou dans l' **éditeur de collections ListViewItem**. Pour ouvrir l' **éditeur de collections ListViewItem**, cliquez sur le bouton de sélection (![le bouton de sélection (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A> dans la fenêtre **Propriétés** .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList, composant](imagelist-component-windows-forms.md)
