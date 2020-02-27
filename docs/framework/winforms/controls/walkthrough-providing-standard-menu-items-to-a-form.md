---
title: "Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628772"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire

Vous pouvez fournir un menu standard pour vos formulaires avec le contrôle <xref:System.Windows.Forms.MenuStrip>.

Cette procédure pas à pas montre comment utiliser un contrôle <xref:System.Windows.Forms.MenuStrip> pour créer un menu standard. Le formulaire répond également lorsqu’un utilisateur sélectionne un élément de menu. Les tâches suivantes sont illustrées dans cette procédure pas à pas :

- Création d’un projet de Windows Forms.

- Création d’un menu standard.

- Création d’un contrôle de <xref:System.Windows.Forms.StatusStrip>.

- Gestion de la sélection des éléments de menu.

Lorsque vous avez terminé, vous disposez d’un formulaire avec un menu standard qui affiche des sélections d’éléments de menu dans un contrôle de <xref:System.Windows.Forms.StatusStrip>.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : fournir des éléments de menu standard à un formulaire](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Conditions préalables requises

Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’application Windows appelé **StandardMenuForm** (**fichier** > nouveau **projet** >  ** > C# visuel** ou **Visual Basic** > **application** > **de** **Bureau classique** ).

2. Dans le Concepteur Windows Forms, sélectionnez le formulaire.

## <a name="create-a-standard-menu"></a>Créer un menu standard

La Concepteur Windows Forms peut remplir automatiquement un contrôle <xref:System.Windows.Forms.MenuStrip> avec des éléments de menu standard.

1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur votre formulaire.

2. Cliquez sur le glyphe actions du concepteur du contrôle <xref:System.Windows.Forms.MenuStrip> (![petite flèche noire](./media/designer-actions-glyph.gif)) et sélectionnez **Insérer les éléments standard**.

     Le contrôle <xref:System.Windows.Forms.MenuStrip> est rempli avec les éléments de menu standard.

3. Cliquez sur l’élément de menu **fichier** pour afficher ses éléments de menu par défaut et les icônes correspondantes.

## <a name="create-a-statusstrip-control"></a>Créer un contrôle StatusStrip

Utilisez le contrôle <xref:System.Windows.Forms.StatusStrip> pour afficher l’état de vos applications Windows Forms. Dans l’exemple actuel, les éléments de menu sélectionnés par l’utilisateur sont affichés dans un contrôle de <xref:System.Windows.Forms.StatusStrip>.

1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.StatusStrip> sur votre formulaire.

     Le contrôle <xref:System.Windows.Forms.StatusStrip> s’ancre automatiquement au bas du formulaire.

2. Cliquez sur le bouton déroulant du contrôle <xref:System.Windows.Forms.StatusStrip> et sélectionnez **StatusLabel** pour ajouter un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> au contrôle <xref:System.Windows.Forms.StatusStrip>.

## <a name="handle-item-selection"></a>Gérer la sélection des éléments

Gérez l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> pour répondre lorsque l’utilisateur sélectionne un élément de menu.

1. Cliquez sur l’élément de menu **fichier** que vous avez créé dans la section création d’un menu standard.

2. Dans la fenêtre **Propriétés**, cliquez sur **Événements**.

3. Double-cliquez sur l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

     Le Concepteur Windows Forms génère un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

4. Insérez le code suivant dans le gestionnaire d’événements.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. Insérez la définition de la méthode de l’utilitaire `UpdateStatus` dans le formulaire.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Point de contrôle-tester votre formulaire

1. Appuyez sur **F5** pour compiler et exécuter votre formulaire.

2. Cliquez sur l’élément de menu **fichier** pour ouvrir le menu.

3. Dans le menu **fichier** , cliquez sur l’un des éléments pour le sélectionner.

     Le contrôle <xref:System.Windows.Forms.StatusStrip> affiche l’élément sélectionné.

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez créé un formulaire avec un menu standard. Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à de nombreuses autres fins :

- Créez des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).

- Créez un formulaire d’interface multidocument (MDI) avec des contrôles d’ancrage <xref:System.Windows.Forms.ToolStrip>. Pour plus d’informations, consultez [procédure pas à pas : création d’un formulaire MDI avec la fusion de menus et les contrôles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Donnez à vos <xref:System.Windows.Forms.ToolStrip> un aspect professionnel. Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
