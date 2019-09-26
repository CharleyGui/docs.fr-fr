---
title: 'Procédure : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040083"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Procédure : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l’aide du concepteur

Le processus d’ajout d’un élément à un <xref:System.Windows.Forms.ListView> contrôle Windows Forms consiste principalement à spécifier l’élément et à lui assigner des propriétés. L’ajout ou la suppression d’éléments de liste peut être effectué à tout moment.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure : Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit : Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

### <a name="to-add-or-remove-items-using-the-designer"></a>Pour ajouter ou supprimer des éléments à l’aide du concepteur

1. Sélectionnez le contrôle <xref:System.Windows.Forms.ListView>.

2. Dans la fenêtre **Propriétés** , cliquez sur **le bouton de sélection (** ![...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Items%2A> propriété.

     L' **éditeur de collections ListViewItem** s’affiche.

3. Pour ajouter un élément, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les <xref:System.Windows.Forms.ListView.Text%2A> propriétés <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> et.

4. Pour supprimer un élément, sélectionnez-le et cliquez sur le bouton **supprimer** .

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Guide pratique pour Afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Guide pratique pour Afficher les icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Guide pratique pour Regrouper des éléments dans un contrôle ListView Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
