---
title: 'Procédure pas à pas : création d’un formulaire MDI avec la fusion des menus et des contrôles ToolStrip'
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
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211557"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Procédure pas à pas : création d’un formulaire MDI avec la fusion des menus et des contrôles ToolStrip

L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> prend en charge plusieurs applications MDI (Multiple Document Interface) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus. Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.

Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStripPanel> contrôles avec un formulaire MDI. Le formulaire prend également en charge la fusion de menus avec les menus enfants. Les tâches suivantes sont illustrées dans cette procédure pas à pas :

- Création d’un projet Windows Forms.

- Création du menu principal pour votre formulaire. Le nom réel du menu varient.

- Ajout de la <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils**.

- Création d’un formulaire enfant.

- Réorganisation <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan des contrôles.

Lorsque vous avez terminé, avoir un formulaire MDI qui prend en charge la fusion de menus et movable <xref:System.Windows.Forms.ToolStrip> contrôles.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin de Visual Studio pour effectuer cette procédure pas à pas.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’Application de Windows appelé **MdiForm** (**fichier** > **New** > **projet**  >  **Visual C#**  ou **Visual Basic** > **bureau classique**  >   **Windows Forms Application**).

2. Dans le Concepteur Windows Forms, sélectionnez le formulaire.

3. Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à `true`.

## <a name="create-the-main-menu"></a>Créer le menu principal

Le formulaire MDI parent contient le menu principal. Le menu principal possède un élément de menu nommé **fenêtre**. Avec le **fenêtre** élément de menu, vous pouvez créer des formulaires enfants. Éléments de menu à partir de formulaires enfants sont fusionnés dans le menu principal.

1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle vers le formulaire.

2. Ajouter un <xref:System.Windows.Forms.ToolStripMenuItem> à la <xref:System.Windows.Forms.MenuStrip> contrôler et nommez-le **fenêtre**.

3. Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.

4. Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété `ToolStripMenuItem1`.

5. Ajouter un sous-élément à la **fenêtre** élément de menu, puis nommez le sous-élément **New**.

6. Dans la fenêtre Propriétés, cliquez sur **événements**.

7. Double-cliquez sur le <xref:System.Windows.Forms.ToolStripItem.Click> événement.

     Le Concepteur de formulaires Windows génère un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement.

8. Insérez le code suivant dans le Gestionnaire d’événements.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Ajouter le contrôle ToolStripPanel à la boîte à outils

Lorsque vous utilisez <xref:System.Windows.Forms.MenuStrip> contrôles avec un formulaire MDI doit avoir le <xref:System.Windows.Forms.ToolStripPanel> contrôle. Vous devez ajouter le <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur de formulaires Windows.

1. Ouvrez le **boîte à outils**, puis cliquez sur le **tous les Windows Forms** onglet pour afficher les contrôles Windows Forms disponibles.

2. Avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **choisir des éléments de**.

3. Dans le **Choose Toolbox Items** boîte de dialogue, faites défiler vers le bas le **nom** colonne jusqu'à ce que vous trouviez **ToolStripPanel**.

4. Sélectionnez la case à cocher par **ToolStripPanel**, puis cliquez sur **OK**.

     Le <xref:System.Windows.Forms.ToolStripPanel> contrôle s’affiche dans le **boîte à outils**.

## <a name="create-a-child-form"></a>Créer un formulaire enfant

Dans cette procédure, vous allez définir une classe de formulaire enfant distincte qui possède son propre <xref:System.Windows.Forms.MenuStrip> contrôle. Les éléments de menu pour ce formulaire sont fusionnés avec ceux du formulaire parent.

1. Ajoutez un nouveau formulaire nommé `ChildForm` au projet.

     Pour plus d'informations, voir [Procédure : Ajouter des Windows Forms à un projet](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle vers le formulaire enfant.

3. Cliquez sur le <xref:System.Windows.Forms.MenuStrip> glyphe de balise active du contrôle (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), puis sélectionnez **modifier les éléments**.

4. Dans le **éditeur de collections Items** boîte de dialogue zone, ajoutez une nouvelle <xref:System.Windows.Forms.ToolStripMenuItem> nommé **ChildMenuItem** au menu enfant.

     Pour plus d’informations, consultez [éditeur de collections d’éléments ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Le formulaire de test

1. Appuyez sur **F5** pour compiler et exécuter votre formulaire.

2. Cliquez sur le **fenêtre** élément de menu pour ouvrir le menu, puis cliquez sur **New**.

     Un nouveau formulaire enfant est créé dans la zone du formulaire MDI client. Les menus du formulaire enfant sont fusionné avec le menu principal.

3. Fermez le formulaire enfant.

     Les menus du formulaire enfant sont supprimé dans le menu principal.

4. Cliquez sur **New** plusieurs fois.

     Les formulaires enfants sont automatiquement répertoriés sous la **fenêtre** élément de menu, car le <xref:System.Windows.Forms.MenuStrip> du contrôle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété est affectée.

## <a name="add-toolstrip-support"></a>Ajouter la prise en charge de ToolStrip

Dans cette procédure, vous allez ajouter quatre <xref:System.Windows.Forms.ToolStrip> contrôles au formulaire parent MDI. Chaque <xref:System.Windows.Forms.ToolStrip> contrôle est ajouté à l’intérieur d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle, qui est ancré au bord du formulaire.

1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStripPanel> contrôle vers le formulaire.

2. Avec le <xref:System.Windows.Forms.ToolStripPanel> contrôle sélectionné, double-cliquez sur le <xref:System.Windows.Forms.ToolStrip> dans contrôler le **boîte à outils**.

     Un <xref:System.Windows.Forms.ToolStrip> contrôle est créé dans le <xref:System.Windows.Forms.ToolStripPanel> contrôle.

3. Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.

4. Dans la fenêtre Propriétés, modifiez la valeur du contrôle <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Left>.

     Le <xref:System.Windows.Forms.ToolStripPanel> contrôler s’ancre sur le côté gauche du formulaire, sous le menu principal. La zone cliente MDI est redimensionné pour s’ajuster à la <xref:System.Windows.Forms.ToolStripPanel> contrôle.

5. Répétez les étapes 1 à 4.

     Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôle vers le haut du formulaire.

     Le <xref:System.Windows.Forms.ToolStripPanel> contrôle est ancré sous le menu principal, mais à droite de la première <xref:System.Windows.Forms.ToolStripPanel> contrôle. Cette étape illustre l’importance de l’ordre de plan positionner correctement <xref:System.Windows.Forms.ToolStripPanel> contrôles.

6. Répétez les étapes 1 à 4 pour deux autres <xref:System.Windows.Forms.ToolStripPanel> contrôles.

     Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôles vers la droite et le bas du formulaire.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>Organiser par ordre de plan des contrôles ToolStripPanel

La position d’une fenêtre fixe <xref:System.Windows.Forms.ToolStripPanel> contrôle sur votre formulaire MDI est déterminée par la position du contrôle dans l’ordre de plan. Vous pouvez facilement réorganiser l’ordre de plan de vos contrôles dans la fenêtre Structure du Document.

1. Dans le **vue** menu, cliquez sur **Windows autres**, puis cliquez sur **structure du Document**.

     La disposition de votre <xref:System.Windows.Forms.ToolStripPanel> contrôles à partir de la procédure précédente n’est pas standard. Il s’agit, car l’ordre de plan n’est pas correct. Utilisez la fenêtre Structure du Document pour modifier l’ordre de plan des contrôles.

2. Dans la fenêtre Structure du Document, sélectionnez **ToolStripPanel4**.

3. Cliquez sur le bouton de flèche vers le bas à plusieurs reprises, jusqu'à ce que **ToolStripPanel4** figure au bas de la liste.

     Le **ToolStripPanel4** contrôle est ancré en bas du formulaire, sous les autres contrôles.

4. Sélectionnez **ToolStripPanel2**.

5. Cliquez sur le bouton de flèche vers le bas une fois pour positionner le troisième contrôle dans la liste.

     Le **ToolStripPanel2** contrôle est ancré en haut du formulaire, sous le menu principal et au-dessus des autres contrôles.

6. Sélectionnez différents contrôles dans le **structure du Document** fenêtre et de les déplacer à différents endroits dans l’ordre de plan. Notez l’effet de l’ordre de plan sur la position des contrôles ancrés. Utilisez CTRL + Z ou **Annuler** sur le **modifier** menu Annuler vos modifications.

## <a name="checkpoint---test-your-form"></a>Point de contrôle - tester votre formulaire

1. Appuyez sur **F5** pour compiler et exécuter votre formulaire.

2. Cliquez sur la poignée d’un <xref:System.Windows.Forms.ToolStrip> contrôler et faites glisser le contrôle à des positions différentes dans le formulaire.

     Vous pouvez faire glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à partir d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle vers un autre.

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez créé un formulaire MDI parent avec <xref:System.Windows.Forms.ToolStrip> de contrôles et de fusion de menus. Vous pouvez utiliser le <xref:System.Windows.Forms.ToolStrip> famille de contrôles à de nombreuses autres fins :

- Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).

- Créé un formulaire avec un menu standard automatiquement rempli. Pour plus d’informations, consultez [Procédure pas à pas : En fournissant des éléments de Menu Standard à un formulaire](walkthrough-providing-standard-menu-items-to-a-form.md).

- Donnez à votre <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel. Pour plus d'informations, voir [Procédure : Définir le convertisseur ToolStrip pour une Application](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Guide pratique pour Créer des formulaires MDI parents](../advanced/how-to-create-mdi-parent-forms.md)
- [Guide pratique pour Créer des formulaires MDI enfants](../advanced/how-to-create-mdi-child-forms.md)
- [Guide pratique pour Insérer un MenuStrip dans un Menu du menu déroulant MDI](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
