---
title: 'Procédure : définir une icône pour un bouton de barre d’outils à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 5de7645ecbf2123df849046a152643cd629b4898
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038237"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Procédure : définir une icône pour un bouton de barre d’outils à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.

<xref:System.Windows.Forms.ToolBar>les boutons peuvent afficher des icônes pour faciliter leur identification par les utilisateurs. Pour ce faire, vous pouvez ajouter des <xref:System.Windows.Forms.ImageList> images au composant et les <xref:System.Windows.Forms.ToolBar> associer au contrôle.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ToolBar> un contrôle et <xref:System.Windows.Forms.ImageList> un composant. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.


### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Pour définir une icône pour un bouton de barre d’outils au moment du design

1. Ajoutez des <xref:System.Windows.Forms.ImageList> images au composant. Pour plus d'informations, voir [Procédure : Ajoutez ou supprimez des images ImageList avec](how-to-add-or-remove-imagelist-images-with-the-designer.md)le concepteur.

2. Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle sur votre formulaire.

3. Dans la fenêtre **Propriétés** , définissez la <xref:System.Windows.Forms.ToolBar> propriété du <xref:System.Windows.Forms.ToolBar.ImageList%2A> contrôle sur le <xref:System.Windows.Forms.ImageList> composant.

4. Cliquez sur <xref:System.Windows.Forms.ToolBar> la propriété <xref:System.Windows.Forms.ToolBar.Buttons%2A> du contrôle pour le sélectionner,![puis cliquez sur le bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png).) pour ouvrir l' **éditeur de collections ToolBarButton**.

5. Utilisez le bouton **Ajouter** pour ajouter des <xref:System.Windows.Forms.ToolBar> boutons au contrôle.

6. Dans la fenêtre **Propriétés** qui s’affiche dans le volet situé à droite de l' **éditeur de collections ToolBarButton**, affectez à la <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de la barre d’outils l’une des valeurs de la liste, qui est tirée des images que vous avez ajoutées au <xref:System.Windows.Forms.ImageList> composant.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolBar>
- [Guide pratique pour Déclencher des événements de menu pour les boutons de barre d’outils](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar, contrôle](toolbar-control-windows-forms.md)
- [ImageList, composant](imagelist-component-windows-forms.md)
