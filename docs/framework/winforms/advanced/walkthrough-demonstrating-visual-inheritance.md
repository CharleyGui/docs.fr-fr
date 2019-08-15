---
title: 'Procédure pas à pas : démonstration de l’héritage visuel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040320"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Procédure pas à pas : démonstration de l’héritage visuel

L'héritage visuel vous permet de visualiser les contrôles sur le formulaire de base et d'ajouter de nouveaux contrôles. Dans cette procédure pas à pas, vous allez créer un formulaire de base et le compiler dans une bibliothèque de classes. Vous importerez cette bibliothèque de classes dans un autre projet et créerez un formulaire qui hérite du formulaire de base. Pendant cette procédure pas à pas, vous allez apprendre à :

- créer un projet de bibliothèque de classes contenant un formulaire de base ;

- ajouter un bouton avec des propriétés modifiables par les classes dérivées du formulaire de base ;

- ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base ;

- créer un projet contenant un formulaire qui hérite de `BaseForm`.

Pour finir, cette procédure pas à pas vous montrera la différence entre les contrôles privés et protégés dans un formulaire hérité.

> [!CAUTION]
> Les contrôles ne prennent pas tous en charge l'héritage visuel à partir d'un formulaire de base. Les contrôles suivants ne prennent pas en charge le scénario décrit dans cette procédure pas à pas :
>
>  <xref:System.Windows.Forms.WebBrowser>
>
>  <xref:System.Windows.Forms.ToolStrip>
>
>  <xref:System.Windows.Forms.ToolStripPanel>
>
>  <xref:System.Windows.Forms.TableLayoutPanel>
>
>  <xref:System.Windows.Forms.FlowLayoutPanel>
>
>  <xref:System.Windows.Forms.DataGridView>
>
>  Ces contrôles dans le formulaire hérité sont toujours en lecture seule, quels que soient les modificateurs que vous utilisez (`private`, `protected` ou `public`).

## <a name="create-a-class-library-project-containing-a-base-form"></a>Créer un projet de bibliothèque de classes contenant un formulaire de base

1. Dans Visual Studio, dans le menu **fichier** , choisissez **nouveau** > **projet** pour ouvrir la boîte de dialogue **nouveau projet** .

2. Créez une application Windows Forms nommée `BaseFormLibrary`.

3. Pour créer une bibliothèque de classes au lieu d’une application de Windows Forms standard, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **BaseFormLibrary** , puis sélectionnez **Propriétés**.

4. Dans les propriétés du projet, modifiez le **type de sortie** de l' **application Windows** en **bibliothèque de classes**.

5. Dans le menu **fichier** , choisissez **enregistrer tout** pour enregistrer le projet et les fichiers à l’emplacement par défaut.

 Les deux procédures suivantes ajoutent des boutons au formulaire de base. Pour illustrer l'héritage visuel, donnez aux boutons différents niveaux d'accès en définissant leurs propriétés `Modifiers`.

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Ajouter un bouton qui peut être modifié par les héritiers du formulaire de base

1. Ouvrez **Form1** dans le concepteur.

2. Sous l’onglet **tous les Windows Forms** de la **boîte à outils**, double-cliquez sur le **bouton** pour ajouter un bouton au formulaire. Utilisez la souris pour positionner et redimensionner le bouton.

3. Dans la fenêtre Propriétés, définissez les propriétés suivantes du bouton :

    - Affectez à la propriété **Text** la valeur **Say Hello**.

    - Affectez à la propriété **(Name)** la valeur **btnProtected**.

    - Affectez à la propriété Modifiers la valeur **protected**. Cela permet aux formulaires qui héritent de **Form1** de modifier les propriétés de **btnProtected**.

4. Double-cliquez sur le bouton **Say Hello** pour ajouter un gestionnaire d’événements pour l’événement **Click** .

5. Ajoutez la ligne de code suivante au gestionnaire d'événements :

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base

1. Basculez en mode Design en cliquant sur l’onglet **Form1. vb [Design], Form1.cs [Design] ou Form1. jsl [Design]** au-dessus de l’éditeur de code, ou en appuyant sur F7.

2. Ajoutez un deuxième bouton et définissez ses propriétés comme suit :

    - Affectez à la propriété **Text** la valeur **Say Goodbye**.

    - Affectez à la propriété **(Name)** la valeur **btnPrivate**.

    - Affectez à la propriété Modifiers la valeur **Private**. Cela empêche les formulaires qui héritent de **Form1** de modifier les propriétés de **btnPrivate**.

3. Double-cliquez sur le bouton **Say Goodbye** pour ajouter un gestionnaire d’événements pour l’événement **Click** . Placez la ligne de code suivante dans la procédure d'événement :

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. Dans le menu **générer** , choisissez **générer la bibliothèque BaseForm** pour générer la bibliothèque de classes.

     Une fois la bibliothèque générée, vous pouvez créer un projet qui hérite du formulaire que vous venez de créer.

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Créer un projet contenant un formulaire qui hérite du formulaire de base

1. Dans le menu **fichier** , choisissez **Ajouter** , puis **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

2. Créez une application Windows Forms nommée `InheritanceTest`.

## <a name="add-an-inherited-form"></a>Ajouter un formulaire hérité

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** , sélectionnez **Ajouter**, puis **nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez la catégorie **Windows Forms** (si vous disposez d’une liste de catégories), puis sélectionnez le modèle de **formulaire hérité** .

3. Laissez le nom `Form2` par défaut, puis cliquez sur **Ajouter**.

4. Dans la boîte de dialogue **Sélecteur d’héritage** , sélectionnez **Form1** dans le projet **BaseFormLibrary** comme formulaire à partir duquel hériter, puis cliquez sur **OK**.

     Cela crée un formulaire dans le projet **InheritanceTest** qui dérive du formulaire dans **BaseFormLibrary**.

5. Ouvrez le formulaire hérité (**Form2**) dans le concepteur en double-cliquant dessus, s’il n’est pas déjà ouvert.

     Dans le concepteur, les boutons hérités ont un symbole (![Capture d’écran du symbole d’héritage de Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) dans leur coin supérieur, indiquant qu’ils sont hérités.

6. Sélectionnez le bouton **Say Hello** et observez les poignées de redimensionnement. Ce bouton étant protégé, les héritiers peuvent le déplacer, le redimensionner, changer sa légende et apporter d'autres modifications.

7. Sélectionnez le bouton privé **Say Goodbye** et Notez qu’il n’a pas de poignées de redimensionnement. En outre, dans la fenêtre **Propriétés** , les propriétés de ce bouton sont grisées pour indiquer qu’elles ne peuvent pas être modifiées.

8. Si vous utilisez Visual C#:

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1** dans le projet **InheritanceTest** , puis sélectionnez **supprimer**. Dans la boîte de message qui s’affiche, cliquez sur **OK** pour confirmer la suppression.

    2. Ouvrez le fichier Program.cs et remplacez la ligne `Application.Run(new Form1());` par `Application.Run(new Form2());`.

9. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **définir comme projet de démarrage**.

10. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **Propriétés**.

11. Dans les pages de propriétés de **InheritanceTest** , définissez l' **objet de démarrage** en tant que formulaire hérité (**Form2**).

12. Appuyez sur **F5** pour exécuter l’application et observez le comportement du formulaire hérité.

## <a name="next-steps"></a>Étapes suivantes

L'héritage pour les contrôles utilisateur fonctionne de la même façon. Ouvrez un nouveau projet de bibliothèque de classes et ajoutez un contrôle utilisateur. Placez les contrôles constituants dessus et compilez le projet. Ouvrez un autre projet de bibliothèque de classes et ajoutez une référence à la bibliothèque de classes compilée. Essayez également d’ajouter un contrôle hérité (via la boîte de dialogue **ajouter de nouveaux éléments** ) au projet et d’utiliser le **Sélecteur d’héritage**. Ajoutez un contrôle utilisateur et modifiez l' `Inherits` instruction (`:` en Visual C#). Pour plus d'informations, voir [Procédure : Héritez](how-to-inherit-windows-forms.md)Windows Forms.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Hériter Windows Forms](how-to-inherit-windows-forms.md)
- [Héritage visuel des Windows Forms](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
