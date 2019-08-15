---
title: 'Procédure : ajouter des boutons à un contrôle ToolBar à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: e5069dd46a31a65f65a17d750b685d82762e3d11
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038205"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Procédure : ajouter des boutons à un contrôle ToolBar à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.

Les boutons que vous y <xref:System.Windows.Forms.ToolBar> ajoutez sont une partie intégrante du contrôle. Elles peuvent être utilisées pour fournir un accès facile aux commandes de menu ou, autrement, elles peuvent être placées dans une autre zone de l’interface utilisateur de votre application pour exposer à vos utilisateurs des commandes qui ne sont pas disponibles dans la structure de menu.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ToolBar> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.


### <a name="to-add-buttons-at-design-time"></a>Pour ajouter des boutons au moment du design

1. Sélectionnez le contrôle <xref:System.Windows.Forms.ToolBar>.

2. Dans la **fenêtre Propriétés** , cliquez sur <xref:System.Windows.Forms.ToolBar.Buttons%2A> la propriété pour la sélectionner, puis ![cliquez sur le bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual](./media/visual-studio-ellipsis-button.png)Studio.) pour ouvrir le **ToolBarButton Éditeur de collections**.

3. Utilisez les boutons **Ajouter** et **supprimer** pour ajouter et supprimer des <xref:System.Windows.Forms.ToolBar> boutons du contrôle.

4. Configurez les propriétés des boutons individuels dans la fenêtre **Propriétés** qui s’affiche dans le volet situé à droite de l’éditeur. Le tableau suivant présente certaines propriétés importantes à prendre en compte.

    |Propriété|Description|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Définit le menu à afficher dans le bouton déroulant de la barre d’outils. La propriété du bouton <xref:System.Windows.Forms.ToolBarButton.Style%2A> de barre d’outils doit <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>avoir la valeur. Cette propriété prend une instance de la <xref:System.Windows.Forms.ContextMenu> classe en tant que référence.|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Définit si un bouton de barre d’outils de style bascule fait l’objet d’un push partiel. La propriété du bouton <xref:System.Windows.Forms.ToolBarButton.Style%2A> de barre d’outils doit <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>avoir la valeur.|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Définit si un bouton de barre d’outils de style bascule est actuellement à l’État push. La propriété du bouton <xref:System.Windows.Forms.ToolBarButton.Style%2A> de barre d’outils doit <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> avoir <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>la valeur ou.|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Définit le style du bouton de la barre d’outils. Doit être l’une des valeurs de l' <xref:System.Windows.Forms.ToolBarButtonStyle> énumération.|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Chaîne de texte affichée par le bouton.|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Texte qui apparaît sous la forme d’une info-bulle pour le bouton.|

5. Cliquez sur **OK** pour fermer la boîte de dialogue et créer les panneaux que vous avez spécifiés.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolBar>
- [Guide pratique pour Définir une icône pour un bouton de barre d’outils](how-to-define-an-icon-for-a-toolbar-button.md)
- [Guide pratique : Déclencher des événements de menu pour les boutons de barre d’outils](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Vue d’ensemble du contrôle ToolBar](toolbar-control-overview-windows-forms.md)
- [ToolBar, contrôle](toolbar-control-windows-forms.md)
