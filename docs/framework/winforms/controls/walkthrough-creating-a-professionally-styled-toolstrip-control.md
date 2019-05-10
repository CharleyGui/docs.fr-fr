---
title: 'Procédure pas à pas : création d’un contrôle ToolStrip de style professionnel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211772"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Procédure pas à pas : création d’un contrôle ToolStrip de style professionnel

Vous pouvez donner à votre application <xref:System.Windows.Forms.ToolStrip> un aspect professionnel et un comportement de contrôles en écrivant votre propre classe dérivée de la <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.

Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStrip> contrôles pour créer un contrôle composite qui ressemble à la **volet de Navigation** fourni par Microsoft® Outlook®. Les tâches suivantes sont illustrées dans cette procédure pas à pas :

- Création d’un projet de bibliothèque de contrôles Windows.

- Conception du contrôle StackView.

- Implémentation d’un convertisseur personnalisé.

Lorsque vous avez terminé, avoir un contrôle client personnalisé réutilisable avec l’aspect d’un contrôle Microsoft Office® XP Professionnel.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Créer un contrôle ToolStrip de style professionnel](how-to-create-a-professionally-styled-toolstrip-control.md).

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin de Visual Studio pour effectuer cette procédure pas à pas.

## <a name="create-the-control-library-project"></a>Créer le projet de bibliothèque de contrôles

1. Dans Visual Studio, créez un nouveau projet de bibliothèque de contrôles Windows nommé `StackViewLibrary`.

2. Dans **l’Explorateur de solutions**, supprimer le contrôle du projet par défaut en supprimant le fichier source nommé « UserControl1.cs » ou « UserControl1.vb », en fonction de la langue de votre choix.

     Pour plus d'informations, voir [Procédure : Supprimer, suppression et exclure des éléments](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).

3. Ajouter un nouveau <xref:System.Windows.Forms.UserControl> d’élément à la **StackViewLibrary** projet. Nommez le nouveau fichier source une base de `StackView`.

## <a name="design-the-stackview-control"></a>Concevoir le contrôle StackView

Le `StackView` contrôle est un contrôle composite avec un seul enfant <xref:System.Windows.Forms.ToolStrip> contrôle. Pour plus d’informations sur les contrôles composites, consultez [variétés de contrôles personnalisés](varieties-of-custom-controls.md).

1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à l’aire de conception.

2. Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.ToolStrip> propriétés de contrôle conformément au tableau suivant.

    |Propriété|Value|
    |--------------|-----------|
    |Nom|`stackStrip`|
    |CanOverflow|`false`|
    |Station d' accueil|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |Police|`Tahoma, 10pt, style=Bold`|
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |Padding|`0, 7, 0, 0`|
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. Dans le Concepteur de formulaires Windows, cliquez sur le <xref:System.Windows.Forms.ToolStrip> du contrôle **ajouter** bouton et ajoutez un <xref:System.Windows.Forms.ToolStripButton> à la `stackStrip` contrôle.

4. Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.ToolStripButton> propriétés de contrôle conformément au tableau suivant.

    |Propriété|Value|
    |--------------|-----------|
    |Nom|`mailStackButton`|
    |CheckOnClick|true|
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|
    |Propriété DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |ImageTransparentColor|`238, 238, 238`|
    |Marge|`0, 0, 0, 0`|
    |Padding|`3, 3, 3, 3`|
    |Texte|**Messagerie**|
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. Répétez l’étape 7 pour les trois autres <xref:System.Windows.Forms.ToolStripButton> contrôles.

     Nommez les contrôles `calendarStackButton`, `contactsStackButton`, et `tasksStackButton`. Définissez la valeur de la <xref:System.Windows.Forms.Control.Text%2A> propriété **calendrier**, **Contacts**, et **tâches**, respectivement.

## <a name="handle-events"></a>Gérer les événements

Deux événements sont importantes pour rendre le `StackView` contrôle se comporte correctement. Gérer le <xref:System.Windows.Forms.UserControl.Load> événement pour positionner le contrôle correctement. Gérer le <xref:System.Windows.Forms.ToolStripItem.Click> événement pour chaque <xref:System.Windows.Forms.ToolStripButton> pour donner le `StackView` contrôler le comportement d’état semblable à la <xref:System.Windows.Forms.RadioButton> contrôle.

1. Dans le Concepteur Windows Forms, sélectionnez le `StackView` contrôle.

2. Dans la fenêtre **Propriétés**, cliquez sur **Événements**.

3. Double-cliquez sur l’événement Load pour générer le `StackView_Load` Gestionnaire d’événements.

4. Dans la méthode de gestionnaire d'événements `StackView_Load`, copiez et collez le code suivant.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. Dans le Concepteur Windows Forms, sélectionnez le `mailStackButton` contrôle.

6. Dans la fenêtre **Propriétés**, cliquez sur **Événements**.

7. Double-cliquez sur l’événement Click.

     Le Concepteur de formulaires Windows génère le `mailStackButton_Click` Gestionnaire d’événements.

8. Renommer le `mailStackButton_Click` Gestionnaire d’événements à `stackButton_Click`.

     Pour plus d’informations, consultez [renommer un symbole de code (refactorisation)](/visualstudio/ide/reference/rename).

9. Insérez le code suivant dans le `stackButton_Click` Gestionnaire d’événements.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. Dans le Concepteur Windows Forms, sélectionnez le `calendarStackButton` contrôle.

11. Dans le **propriétés** , configurez l’événement Click pour le `stackButton_Click` Gestionnaire d’événements.

12. Répétez les étapes 10 et 11 pour les `contactsStackButton` et `tasksStackButton` contrôles.

## <a name="define-icons"></a>Définir des icônes

Chaque `StackView` bouton a une icône associée. Pour plus de commodité, chaque icône est représentée sous forme de chaîne codée en Base64, qui est désérialisé avant un <xref:System.Drawing.Bitmap> est créé à partir de celui-ci. Dans un environnement de production, vous stockez des données bitmap en tant que ressource et vos icônes s’affichent dans le Concepteur de formulaires Windows. Pour plus d'informations, voir [Procédure : Ajouter des Images d’arrière-plan à Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).

1. Dans l’éditeur de Code, insérez le code suivant dans le `StackView` définition de classe. Ce code initialise les bitmaps pour les <xref:System.Windows.Forms.ToolStripButton> icônes.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. Ajoutez un appel à la `InitializeImages` méthode dans le `StackView` constructeur de classe.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a>Implémenter un convertisseur personnalisé

Vous pouvez personnaliser la plupart des éléments de la `StackView` contrôler en implémentant une classe qui dérive de la <xref:System.Windows.Forms.ToolStripRenderer> classe. Dans cette procédure, vous allez implémenter un <xref:System.Windows.Forms.ToolStripProfessionalRenderer> classe qui personnalise la poignée et dessine des arrière-plans de dégradé pour le <xref:System.Windows.Forms.ToolStripButton> contrôles.

1. Insérez le code suivant dans le `StackView` définition du contrôle.

     La définition de la `StackRenderer` classe, qui remplace le <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, et <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> méthodes pour produire une apparence personnalisée.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. Dans le `StackView` constructeur du contrôle, créer une nouvelle instance de la `StackRenderer` classe et assignez-la à la `stackStrip` du contrôle <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriété.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a>Tester le contrôle StackView

Le `StackView` contrôle dérive le <xref:System.Windows.Forms.UserControl> classe. Par conséquent, vous pouvez tester le contrôle avec le **conteneur de Test UserControl**. Pour plus d'informations, voir [Procédure : Tester le comportement au moment de l’exécution d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

1. Appuyez sur **F5** pour générer le projet et démarrer le **conteneur de Test UserControl**.

2. Déplacez le pointeur sur les boutons de la `StackView` contrôler, puis cliquez sur un bouton pour visualiser l’apparence de son état sélectionné.

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez créé un contrôle client personnalisé réutilisable avec l’apparence professionnelle d’un contrôle Office XP. Vous pouvez utiliser le <xref:System.Windows.Forms.ToolStrip> famille de contrôles à de nombreuses autres fins :

- Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).

- Créer un formulaire avec un menu standard automatiquement rempli. Pour plus d’informations, consultez [Procédure pas à pas : En fournissant des éléments de Menu Standard à un formulaire](walkthrough-providing-standard-menu-items-to-a-form.md).

- Créer un formulaire d’interface (multidocument MDI) document avec l’ancrage <xref:System.Windows.Forms.ToolStrip> contrôles. Pour plus d'informations, voir [Procédure : Créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
- [Guide pratique pour Fournir des éléments de Menu Standard à un formulaire](how-to-provide-standard-menu-items-to-a-form.md)
