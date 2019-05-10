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
ms.openlocfilehash: a5e2a8b0bf982ff112d7930e331456fa69485dfc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665906"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Procédure pas à pas : démonstration de l’héritage visuel
L'héritage visuel vous permet de visualiser les contrôles sur le formulaire de base et d'ajouter de nouveaux contrôles. Dans cette procédure pas à pas, vous allez créer un formulaire de base et le compiler dans une bibliothèque de classes. Vous importerez cette bibliothèque de classes dans un autre projet et créerez un formulaire qui hérite du formulaire de base. Pendant cette procédure pas à pas, vous allez apprendre à :  
  
- créer un projet de bibliothèque de classes contenant un formulaire de base ;  
  
- ajouter un bouton avec des propriétés modifiables par les classes dérivées du formulaire de base ;  
  
- ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base ;  
  
- créer un projet contenant un formulaire qui hérite de `BaseForm`.  
  
 Pour finir, cette procédure pas à pas vous montrera la différence entre les contrôles privés et protégés dans un formulaire hérité.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!CAUTION]
>  Les contrôles ne prennent pas tous en charge l'héritage visuel à partir d'un formulaire de base. Les contrôles suivants ne prennent pas en charge le scénario décrit dans cette procédure pas à pas :  
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
  
## <a name="scenario-steps"></a>Étapes du scénario  
 La première étape consiste à créer le formulaire de base.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Pour créer un projet de bibliothèque de classes contenant un formulaire de base  
  
1. À partir de la **fichier** menu, choisissez **New**, puis **projet** pour ouvrir le **nouveau projet** boîte de dialogue.  
  
2. Créer une application Windows Forms nommée `BaseFormLibrary`.  
  
3. Pour créer une bibliothèque de classes au lieu d’une application Windows Forms standard, dans **l’Explorateur de solutions**, avec le bouton droit le **BaseFormLibrary** nœud de projet, puis sélectionnez **propriétés**.  
  
4. Dans les propriétés du projet, modifiez le **type de sortie** de **Windows Application** à **bibliothèque de classes**.  
  
5. À partir de la **fichier** menu, choisissez **Enregistrer tout** pour enregistrer le projet et les fichiers à l’emplacement par défaut.  
  
 Les deux procédures suivantes ajoutent des boutons au formulaire de base. Pour illustrer l'héritage visuel, donnez aux boutons différents niveaux d'accès en définissant leurs propriétés `Modifiers`.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Pour ajouter un bouton modifiable par les héritiers du formulaire de base  
  
1. Ouvrez **Form1** dans le concepteur.  
  
2. Sur le **tous les Windows Forms** onglet de la **boîte à outils**, double-cliquez sur **bouton** pour ajouter un bouton au formulaire. Utilisez la souris pour positionner et redimensionner le bouton.  
  
3. Dans la fenêtre Propriétés, définissez les propriétés suivantes du bouton :  
  
    - Définir le **texte** propriété **Say Hello**.  
  
    - Définir le **(nom)** propriété **btnProtected**.  
  
    - Définir le **modificateurs** propriété **protégé**. Cela rend possible pour les formulaires qui héritent de **Form1** pour modifier les propriétés de **btnProtected**.  
  
4. Double-cliquez sur le **Say Hello** pour ajouter un gestionnaire d’événements pour le **cliquez sur** événement.  
  
5. Ajoutez la ligne de code suivante au gestionnaire d'événements :  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Pour ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base  
  
1. Passez en mode design en cliquant sur le **Form1.vb [Design], Form1.cs [Design] ou Form1.jsl [Design]** onglet au-dessus de l’éditeur de code, ou en appuyant sur F7.  
  
2. Ajoutez un deuxième bouton et définissez ses propriétés comme suit :  
  
    - Définir le **texte** propriété **Say Goodbye**.  
  
    - Définir le **(nom)** propriété **btnPrivate**.  
  
    - Définir le **modificateurs** propriété **privé**. Cela empêche les formulaires qui héritent **Form1** pour modifier les propriétés de **btnPrivate**.  
  
3. Double-cliquez sur le **Say Goodbye** pour ajouter un gestionnaire d’événements pour le **cliquez sur** événement. Placez la ligne de code suivante dans la procédure d'événement :  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4. À partir de la **Build** menu, choisissez **générer une bibliothèque BaseForm** pour générer la bibliothèque de classes.  
  
     Une fois la bibliothèque générée, vous pouvez créer un projet qui hérite du formulaire que vous venez de créer.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Pour créer un projet contenant un formulaire qui hérite du formulaire de base  
  
1. À partir de la **fichier** menu, choisissez **ajouter** , puis **nouveau projet** pour ouvrir le **ajouter un nouveau projet** boîte de dialogue.  
  
2. Créer une application Windows Forms nommée `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Pour ajouter un formulaire hérité  
  
1. Dans **l’Explorateur de solutions**, avec le bouton droit le **InheritanceTest** projet, sélectionnez **ajouter**, puis sélectionnez **un nouvel élément**.  
  
2. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **Windows Forms** catégorie (si vous avez une liste de catégories), puis sélectionnez le **formulaire hérité** modèle.  
  
3. Laissez le nom par défaut `Form2` puis cliquez sur **ajouter**.  
  
4. Dans le **sélecteur d’héritage** boîte de dialogue, sélectionnez **Form1** à partir de la **BaseFormLibrary** projet en tant que le formulaire hériter et cliquez sur **OK** .  
  
     Cette opération crée un formulaire dans le **InheritanceTest** projet qui dérive du formulaire dans **BaseFormLibrary**.  
  
5. Ouvrez le formulaire hérité (**Form2**) dans le concepteur en double-cliquant dessus, s’il n’est pas déjà ouvert.  
  
     Dans le concepteur, les boutons hérités possèdent un symbole)![Capture d’écran du symbole de l’héritage de Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) dans le coin supérieur, indiquant qu’ils sont hérités.  
  
6. Sélectionnez le **Say Hello** bouton et observez les poignées de redimensionnement. Ce bouton étant protégé, les héritiers peuvent le déplacer, le redimensionner, changer sa légende et apporter d'autres modifications.  
  
7. Sélectionnez privé **Say Goodbye** bouton et notez qu’il n’a pas de poignées de redimensionnement. En outre, dans le **propriétés** fenêtre, les propriétés de ce bouton sont estompées pour indiquer qu’ils ne sont pas modifiables.  
  
8. Si vous utilisez Visual c# :  
  
    1. Dans **l’Explorateur de solutions**, avec le bouton droit **Form1** dans le **InheritanceTest** de projet, puis choisissez **supprimer**. Dans la boîte de message qui s’affiche, cliquez sur **OK** pour confirmer la suppression.  
  
    2. Ouvrez le fichier Program.cs et remplacez la ligne `Application.Run(new Form1());` par `Application.Run(new Form2());`.  
  
9. Dans **l’Explorateur de solutions**, avec le bouton droit le **InheritanceTest** de projet et sélectionnez **définir comme projet de démarrage**.  
  
10. Dans **l’Explorateur de solutions**, avec le bouton droit le **InheritanceTest** de projet et sélectionnez **propriétés**.  
  
11. Dans le **InheritanceTest** pages de propriétés, définissez la **objet de démarrage** soit le formulaire hérité (**Form2**).  
  
12. Appuyez sur F5 pour exécuter l'application et observez le comportement du formulaire hérité.  
  
## <a name="next-steps"></a>Étapes suivantes  
 L'héritage pour les contrôles utilisateur fonctionne de la même façon. Ouvrez un nouveau projet de bibliothèque de classes et ajoutez un contrôle utilisateur. Placez les contrôles constituants dessus et compilez le projet. Ouvrez un autre projet de bibliothèque de classes et ajoutez une référence à la bibliothèque de classes compilée. Essayez également d’ajouter un contrôle hérité (via le **ajouter de nouveaux éléments** boîte de dialogue) au projet et à l’aide de la **sélecteur d’héritage**. Ajoutez un contrôle utilisateur et modifiez le `Inherits` (`:` en Visual c#) instruction. Pour plus d'informations, voir [Procédure : Hériter des Windows Forms](how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Hériter des Windows Forms](how-to-inherit-windows-forms.md)
- [Héritage visuel des Windows Forms](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
