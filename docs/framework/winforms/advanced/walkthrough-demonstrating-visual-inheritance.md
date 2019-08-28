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
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046148"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="5ffc5-102">Procédure pas à pas : démonstration de l’héritage visuel</span><span class="sxs-lookup"><span data-stu-id="5ffc5-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="5ffc5-103">L'héritage visuel vous permet de visualiser les contrôles sur le formulaire de base et d'ajouter de nouveaux contrôles.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="5ffc5-104">Dans cette procédure pas à pas, vous allez créer un formulaire de base et le compiler dans une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="5ffc5-105">Vous importerez cette bibliothèque de classes dans un autre projet et créerez un formulaire qui hérite du formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="5ffc5-106">Pendant cette procédure pas à pas, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="5ffc5-107">créer un projet de bibliothèque de classes contenant un formulaire de base ;</span><span class="sxs-lookup"><span data-stu-id="5ffc5-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="5ffc5-108">ajouter un bouton avec des propriétés modifiables par les classes dérivées du formulaire de base ;</span><span class="sxs-lookup"><span data-stu-id="5ffc5-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="5ffc5-109">ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base ;</span><span class="sxs-lookup"><span data-stu-id="5ffc5-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="5ffc5-110">créer un projet contenant un formulaire qui hérite de `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="5ffc5-111">Pour finir, cette procédure pas à pas vous montrera la différence entre les contrôles privés et protégés dans un formulaire hérité.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="5ffc5-112">Les contrôles ne prennent pas tous en charge l'héritage visuel à partir d'un formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="5ffc5-113">Les contrôles suivants ne prennent pas en charge le scénario décrit dans cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> <span data-ttu-id="5ffc5-114">Ces contrôles dans le formulaire hérité sont toujours en lecture seule, quels que soient les modificateurs que vous utilisez (`private`, `protected` ou `public`).</span><span class="sxs-lookup"><span data-stu-id="5ffc5-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="5ffc5-115">Créer un projet de bibliothèque de classes contenant un formulaire de base</span><span class="sxs-lookup"><span data-stu-id="5ffc5-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="5ffc5-116">Dans Visual Studio, dans le menu **fichier** , choisissez **nouveau** > **projet** pour ouvrir la boîte de dialogue **nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="5ffc5-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="5ffc5-117">Créez une application Windows Forms nommée `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="5ffc5-118">Pour créer une bibliothèque de classes au lieu d’une application de Windows Forms standard, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **BaseFormLibrary** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="5ffc5-119">Dans les propriétés du projet, modifiez le **type de sortie** de l' **application Windows** en **bibliothèque de classes**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="5ffc5-120">Dans le menu **fichier** , choisissez **enregistrer tout** pour enregistrer le projet et les fichiers à l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

<span data-ttu-id="5ffc5-121">Les deux procédures suivantes ajoutent des boutons au formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="5ffc5-122">Pour illustrer l'héritage visuel, donnez aux boutons différents niveaux d'accès en définissant leurs propriétés `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="5ffc5-123">Ajouter un bouton qui peut être modifié par les héritiers du formulaire de base</span><span class="sxs-lookup"><span data-stu-id="5ffc5-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="5ffc5-124">Ouvrez **Form1** dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="5ffc5-125">Sous l’onglet **tous les Windows Forms** de la **boîte à outils**, double-cliquez sur le **bouton** pour ajouter un bouton au formulaire.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="5ffc5-126">Utilisez la souris pour positionner et redimensionner le bouton.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="5ffc5-127">Dans la fenêtre Propriétés, définissez les propriétés suivantes du bouton :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="5ffc5-128">Affectez à la propriété **Text** la valeur **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="5ffc5-129">Affectez à la propriété **(Name)** la valeur **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="5ffc5-130">Affectez à la propriété Modifiers la valeur **protected**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="5ffc5-131">Cela permet aux formulaires qui héritent de **Form1** de modifier les propriétés de **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="5ffc5-132">Double-cliquez sur le bouton **Say Hello** pour ajouter un gestionnaire d’événements pour l’événement **Click** .</span><span class="sxs-lookup"><span data-stu-id="5ffc5-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="5ffc5-133">Ajoutez la ligne de code suivante au gestionnaire d'événements :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="5ffc5-134">Ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base</span><span class="sxs-lookup"><span data-stu-id="5ffc5-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="5ffc5-135">Basculez en mode Design en cliquant sur l’onglet **Form1. vb [Design], Form1.cs [Design] ou Form1. jsl [Design]** au-dessus de l’éditeur de code, ou en appuyant sur F7.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="5ffc5-136">Ajoutez un deuxième bouton et définissez ses propriétés comme suit :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="5ffc5-137">Affectez à la propriété **Text** la valeur **Say Goodbye**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="5ffc5-138">Affectez à la propriété **(Name)** la valeur **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="5ffc5-139">Affectez à la propriété Modifiers la valeur **Private**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="5ffc5-140">Cela empêche les formulaires qui héritent de **Form1** de modifier les propriétés de **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="5ffc5-141">Double-cliquez sur le bouton **Say Goodbye** pour ajouter un gestionnaire d’événements pour l’événement **Click** .</span><span class="sxs-lookup"><span data-stu-id="5ffc5-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="5ffc5-142">Placez la ligne de code suivante dans la procédure d'événement :</span><span class="sxs-lookup"><span data-stu-id="5ffc5-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="5ffc5-143">Dans le menu **générer** , choisissez **générer la bibliothèque BaseForm** pour générer la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="5ffc5-144">Une fois la bibliothèque générée, vous pouvez créer un projet qui hérite du formulaire que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="5ffc5-145">Créer un projet contenant un formulaire qui hérite du formulaire de base</span><span class="sxs-lookup"><span data-stu-id="5ffc5-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="5ffc5-146">Dans le menu **fichier** , choisissez **Ajouter** , puis **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="5ffc5-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="5ffc5-147">Créez une application Windows Forms nommée `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="5ffc5-148">Ajouter un formulaire hérité</span><span class="sxs-lookup"><span data-stu-id="5ffc5-148">Add an inherited form</span></span>

1. <span data-ttu-id="5ffc5-149">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** , sélectionnez **Ajouter**, puis **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="5ffc5-150">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez la catégorie **Windows Forms** (si vous disposez d’une liste de catégories), puis sélectionnez le modèle de **formulaire hérité** .</span><span class="sxs-lookup"><span data-stu-id="5ffc5-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="5ffc5-151">Laissez le nom `Form2` par défaut, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="5ffc5-152">Dans la boîte de dialogue **Sélecteur d’héritage** , sélectionnez **Form1** dans le projet **BaseFormLibrary** comme formulaire à partir duquel hériter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="5ffc5-153">Cela crée un formulaire dans le projet **InheritanceTest** qui dérive du formulaire dans **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="5ffc5-154">Ouvrez le formulaire hérité (**Form2**) dans le concepteur en double-cliquant dessus, s’il n’est pas déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

    <span data-ttu-id="5ffc5-155">Dans le concepteur, les boutons hérités ont un symbole (</span><span class="sxs-lookup"><span data-stu-id="5ffc5-155">In the designer, the inherited buttons have a symbol (</span></span>![Capture d’écran du symbole d’héritage de Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="5ffc5-157">) dans leur coin supérieur, indiquant qu’ils sont hérités.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="5ffc5-158">Sélectionnez le bouton **Say Hello** et observez les poignées de redimensionnement.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="5ffc5-159">Ce bouton étant protégé, les héritiers peuvent le déplacer, le redimensionner, changer sa légende et apporter d'autres modifications.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="5ffc5-160">Sélectionnez le bouton privé **Say Goodbye** et Notez qu’il n’a pas de poignées de redimensionnement.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="5ffc5-161">En outre, dans la fenêtre **Propriétés** , les propriétés de ce bouton sont grisées pour indiquer qu’elles ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="5ffc5-162">Si vous utilisez Visual C#:</span><span class="sxs-lookup"><span data-stu-id="5ffc5-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="5ffc5-163">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1** dans le projet **InheritanceTest** , puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="5ffc5-164">Dans la boîte de message qui s’affiche, cliquez sur **OK** pour confirmer la suppression.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="5ffc5-165">Ouvrez le fichier Program.cs et remplacez la ligne `Application.Run(new Form1());` par `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="5ffc5-166">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="5ffc5-167">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="5ffc5-168">Dans les pages de propriétés de **InheritanceTest** , définissez l' **objet de démarrage** en tant que formulaire hérité (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="5ffc5-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="5ffc5-169">Appuyez sur **F5** pour exécuter l’application et observez le comportement du formulaire hérité.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ffc5-170">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5ffc5-170">Next steps</span></span>

<span data-ttu-id="5ffc5-171">L'héritage pour les contrôles utilisateur fonctionne de la même façon.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="5ffc5-172">Ouvrez un nouveau projet de bibliothèque de classes et ajoutez un contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="5ffc5-173">Placez les contrôles constituants dessus et compilez le projet.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="5ffc5-174">Ouvrez un autre projet de bibliothèque de classes et ajoutez une référence à la bibliothèque de classes compilée.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="5ffc5-175">Essayez également d’ajouter un contrôle hérité (via la boîte de dialogue **ajouter de nouveaux éléments** ) au projet et d’utiliser le **Sélecteur d’héritage**.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="5ffc5-176">Ajoutez un contrôle utilisateur et modifiez l' `Inherits` instruction (`:` en Visual C#).</span><span class="sxs-lookup"><span data-stu-id="5ffc5-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="5ffc5-177">Pour plus d'informations, voir [Procédure : Héritez](how-to-inherit-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5ffc5-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ffc5-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ffc5-178">See also</span></span>

- [<span data-ttu-id="5ffc5-179">Guide pratique pour Hériter Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ffc5-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="5ffc5-180">Héritage visuel des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ffc5-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="5ffc5-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ffc5-181">Windows Forms</span></span>](../index.md)
