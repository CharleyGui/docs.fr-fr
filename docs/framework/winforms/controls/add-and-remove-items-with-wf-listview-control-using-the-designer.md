---
title: Ajouter et supprimer des éléments avec le contrôle ListView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732294"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l'aide du concepteur

Le processus d’ajout d’un élément à un contrôle Windows Forms <xref:System.Windows.Forms.ListView> consiste principalement à spécifier l’élément et à lui assigner des propriétés. L’ajout ou la suppression d’éléments de liste peut être effectué à tout moment.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-items-using-the-designer"></a>Pour ajouter ou supprimer des éléments à l’aide du concepteur

1. Sélectionnez le contrôle <xref:System.Windows.Forms.ListView>.

2. Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.

     L' **éditeur de collections ListViewItem** s’affiche.

3. Pour ajouter un élément, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les propriétés <xref:System.Windows.Forms.ListView.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.

4. Pour supprimer un élément, sélectionnez-le et cliquez sur le bouton **supprimer** .

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Guide pratique pour grouper des éléments dans un contrôle ListView Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
