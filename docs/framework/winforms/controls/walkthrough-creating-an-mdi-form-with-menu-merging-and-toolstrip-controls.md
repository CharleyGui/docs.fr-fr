---
title: "Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628785"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip

L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> prend en charge plusieurs applications MDI (Multiple Document Interface) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus. Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.

Cette procédure pas à pas montre comment utiliser des contrôles <xref:System.Windows.Forms.ToolStripPanel> avec un formulaire MDI. Le formulaire prend également en charge la fusion de menus avec les menus enfants. Les tâches suivantes sont illustrées dans cette procédure pas à pas :

- Création d’un projet de Windows Forms.

- Création du menu principal de votre formulaire. Le nom réel du menu varie.

- Ajout du contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils**.

- Création d’un formulaire enfant.

- Réorganisation des contrôles de <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan.

Lorsque vous avez terminé, vous disposez d’un formulaire MDI qui prend en charge la fusion de menus et les contrôles <xref:System.Windows.Forms.ToolStrip> mobiles.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : créer un formulaire MDI avec la fusion de menus et les contrôles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Conditions préalables requises

Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’application Windows nommé **MDIForm** (**fichier** > nouveau **projet** >  ** > C# visuel** ou **Visual Basic** > **application** > **de** **Bureau classique** ).

2. Dans le Concepteur Windows Forms, sélectionnez le formulaire.

3. Dans le Fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> sur `true`.

## <a name="create-the-main-menu"></a>Créer le menu principal

Le formulaire MDI parent contient le menu principal. Le menu principal contient un élément de menu nommé **fenêtre**. Avec l’élément de menu **fenêtre** , vous pouvez créer des formulaires enfants. Les éléments de menu des formulaires enfants sont fusionnés dans le menu principal.

1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire.

2. Ajoutez une <xref:System.Windows.Forms.ToolStripMenuItem> au contrôle <xref:System.Windows.Forms.MenuStrip> et nommez-la **fenêtre**.

3. Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.

4. Dans le Fenêtre Propriétés, définissez la valeur de la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> sur `ToolStripMenuItem1`.

5. Ajoutez un sous-élément à l’élément de menu **fenêtre** , puis nommez le sous-élément **nouveau**.

6. Dans le Fenêtre Propriétés, cliquez sur **événements**.

7. Double-cliquez sur l’événement <xref:System.Windows.Forms.ToolStripItem.Click>.

     Le Concepteur Windows Forms génère un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click>.

8. Insérez le code suivant dans le gestionnaire d’événements.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Ajouter le contrôle ToolStripPanel à la boîte à outils

Lorsque vous utilisez des contrôles <xref:System.Windows.Forms.MenuStrip> avec un formulaire MDI, vous devez disposer du contrôle <xref:System.Windows.Forms.ToolStripPanel>. Vous devez ajouter le contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur Windows Forms.

1. Ouvrez la **boîte à outils**, puis cliquez sur l’onglet **tous les Windows Forms** pour afficher les contrôles Windows Forms disponibles.

2. Cliquez avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **choisir les éléments**.

3. Dans la boîte de dialogue **choisir des éléments de boîte à outils** , faites défiler la colonne **nom** jusqu’à ce que vous trouviez **ToolStripPanel**.

4. Activez la case à cocher par **ToolStripPanel**, puis cliquez sur **OK**.

     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> s’affiche dans la **boîte à outils**.

## <a name="create-a-child-form"></a>Créer un formulaire enfant

Dans cette procédure, vous allez définir une classe de formulaire enfant distincte qui possède son propre contrôle <xref:System.Windows.Forms.MenuStrip>. Les éléments de menu de ce formulaire sont fusionnés avec ceux du formulaire parent.

1. Ajoutez un nouveau formulaire nommé `ChildForm` au projet.

     Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire enfant.

3. Cliquez sur le glyphe actions du concepteur du contrôle <xref:System.Windows.Forms.MenuStrip> (![petite flèche noire](./media/designer-actions-glyph.gif)), puis sélectionnez **modifier les éléments**.

4. Dans la boîte de dialogue **éditeur de collections Items** , ajoutez une nouvelle <xref:System.Windows.Forms.ToolStripMenuItem> nommée **ChildMenuItem** au menu enfant.

     Pour plus d’informations, consultez [éditeur de collections d’éléments ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Tester le formulaire

1. Appuyez sur **F5** pour compiler et exécuter votre formulaire.

2. Cliquez sur l’élément de menu **fenêtre** pour ouvrir le menu, puis cliquez sur **nouveau**.

     Un nouveau formulaire enfant est créé dans la zone cliente MDI du formulaire. Le menu du formulaire enfant est fusionné avec le menu principal.

3. Fermez le formulaire enfant.

     Le menu du formulaire enfant est supprimé du menu principal.

4. Cliquez sur **nouveau** plusieurs fois.

     Les formulaires enfants sont automatiquement répertoriés sous l’élément de menu **fenêtre** , car la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> du contrôle <xref:System.Windows.Forms.MenuStrip> est assignée.

## <a name="add-toolstrip-support"></a>Ajouter la prise en charge ToolStrip

Dans cette procédure, vous allez ajouter quatre <xref:System.Windows.Forms.ToolStrip> contrôles au formulaire parent MDI. Chaque contrôle <xref:System.Windows.Forms.ToolStrip> est ajouté à l’intérieur d’un contrôle <xref:System.Windows.Forms.ToolStripPanel>, qui est ancré au bord du formulaire.

1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ToolStripPanel> sur le formulaire.

2. Après avoir sélectionné le contrôle <xref:System.Windows.Forms.ToolStripPanel>, double-cliquez sur le contrôle <xref:System.Windows.Forms.ToolStrip> dans la **boîte à outils**.

     Un contrôle <xref:System.Windows.Forms.ToolStrip> est créé dans le contrôle <xref:System.Windows.Forms.ToolStripPanel>.

3. Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.

4. Dans le Fenêtre Propriétés, remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle par <xref:System.Windows.Forms.DockStyle.Left>.

     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> s’ancre sur le côté gauche du formulaire, sous le menu principal. La zone cliente MDI se redimensionne en fonction du contrôle <xref:System.Windows.Forms.ToolStripPanel>.

5. Répétez les étapes 1 à 4.

     Ancrez le nouveau contrôle <xref:System.Windows.Forms.ToolStripPanel> en haut du formulaire.

     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> est ancré sous le menu principal, mais à droite du premier contrôle <xref:System.Windows.Forms.ToolStripPanel>. Cette étape illustre l’importance de l’ordre de plan pour positionner correctement les contrôles <xref:System.Windows.Forms.ToolStripPanel>.

6. Répétez les étapes 1 à 4 pour deux autres contrôles de <xref:System.Windows.Forms.ToolStripPanel>.

     Ancrez les nouveaux contrôles de <xref:System.Windows.Forms.ToolStripPanel> à droite et en bas du formulaire.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>Organiser les contrôles ToolStripPanel selon l’ordre de plan

La position d’un contrôle <xref:System.Windows.Forms.ToolStripPanel> ancré sur votre formulaire MDI est déterminée par la position du contrôle dans l’ordre de plan. Vous pouvez facilement organiser l’ordre de plan de vos contrôles dans la fenêtre structure du document.

1. Dans le menu **affichage** , cliquez sur **autres fenêtres**, puis sur **structure du document**.

     La disposition de vos contrôles <xref:System.Windows.Forms.ToolStripPanel> de la procédure précédente est non standard. Cela est dû au fait que l’ordre de plan n’est pas correct. Utilisez la fenêtre structure du document pour modifier l’ordre de plan des contrôles.

2. Dans la fenêtre structure du document, sélectionnez **ToolStripPanel4**.

3. Cliquez sur le bouton fléché vers le bas à plusieurs reprises, jusqu’à ce que **ToolStripPanel4** se trouve en bas de la liste.

     Le contrôle **ToolStripPanel4** est ancré au bas du formulaire, sous les autres contrôles.

4. Sélectionnez **ToolStripPanel2**.

5. Cliquez sur le bouton fléché vers le bas une fois pour positionner le troisième contrôle dans la liste.

     Le contrôle **ToolStripPanel2** est ancré en haut du formulaire, sous le menu principal et au-dessus des autres contrôles.

6. Sélectionnez différents contrôles dans la fenêtre **structure du document** et déplacez-les vers différentes positions dans l’ordre de plan. Notez l’effet de l’ordre de plan sur l’emplacement des contrôles ancrés. Utilisez CTRL + Z ou **Annuler** dans le menu **Edition** pour annuler vos modifications.

## <a name="checkpoint---test-your-form"></a>Point de contrôle-tester votre formulaire

1. Appuyez sur **F5** pour compiler et exécuter votre formulaire.

2. Cliquez sur la poignée d’un contrôle <xref:System.Windows.Forms.ToolStrip> et faites glisser le contrôle vers différentes positions sur le formulaire.

     Vous pouvez faire glisser un contrôle <xref:System.Windows.Forms.ToolStrip> d’un contrôle <xref:System.Windows.Forms.ToolStripPanel> vers un autre.

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez créé un formulaire MDI parent avec des contrôles de <xref:System.Windows.Forms.ToolStrip> et la fusion de menus. Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à de nombreuses autres fins :

- Créez des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).

- Créé un formulaire avec un menu standard rempli automatiquement. Pour plus d’informations, consultez [procédure pas à pas : ajout d’éléments de menu standard à un formulaire](walkthrough-providing-standard-menu-items-to-a-form.md).

- Donnez à vos <xref:System.Windows.Forms.ToolStrip> un aspect professionnel. Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Guide pratique pour créer des formulaires MDI parents](../advanced/how-to-create-mdi-parent-forms.md)
- [Guide pratique pour créer des formulaires MDI enfants](../advanced/how-to-create-mdi-child-forms.md)
- [Guide pratique pour insérer un MenuStrip dans un menu déroulant MDI](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
