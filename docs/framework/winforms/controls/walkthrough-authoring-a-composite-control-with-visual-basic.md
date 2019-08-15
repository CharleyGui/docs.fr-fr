---
title: 'Procédure pas à pas : création d’un contrôle composite avec Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: abfb91c61ef72bfc1626b4cc4dcea42b75e2ab35
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040244"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="2c464-102">Procédure pas à pas : création d’un contrôle composite avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c464-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="2c464-103">Les contrôles composites permettent de créer et de réutiliser des interfaces graphiques personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2c464-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="2c464-104">Un contrôle composite est avant tout un composant doté d’une représentation visuelle.</span><span class="sxs-lookup"><span data-stu-id="2c464-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="2c464-105">Par conséquent, il peut comporter un ou plusieurs blocs de code, composants ou contrôles Windows Forms qui peuvent en étendre les fonctionnalités en validant les entrées d’utilisateur, en modifiant les propriétés d’affichage ou en effectuant d’autres tâches requises par l’auteur.</span><span class="sxs-lookup"><span data-stu-id="2c464-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="2c464-106">Les contrôles composites peuvent être insérés dans les Windows Forms de la même manière que les autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="2c464-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="2c464-107">Dans la première partie de cette procédure pas à pas, vous allez créer un contrôle composite simple appelé `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="2c464-108">Dans la seconde partie de la procédure pas à pas, vous allez étendre les fonctionnalités de `ctlClock` via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="2c464-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="2c464-109">Création du projet</span><span class="sxs-lookup"><span data-stu-id="2c464-109">Creating the Project</span></span>
 <span data-ttu-id="2c464-110">Lorsque vous créez un nouveau projet, vous spécifiez son nom pour définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="2c464-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="2c464-111">Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock</span><span class="sxs-lookup"><span data-stu-id="2c464-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="2c464-112">Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="2c464-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="2c464-113">Dans la liste des projets Visual Basic, sélectionnez le modèle de projet **bibliothèque de contrôles Windows** , tapez `ctlClockLib` dans la zone **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2c464-113">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="2c464-114">Le nom du projet, `ctlClockLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="2c464-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="2c464-115">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2c464-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="2c464-116">Par exemple, si deux assemblies contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l’aide de `ctlClockLib.ctlClock.`.</span><span class="sxs-lookup"><span data-stu-id="2c464-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="2c464-117">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **UserControl1.vb**, puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="2c464-117">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="2c464-118">Remplacez le nom de fichier par `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="2c464-118">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="2c464-119">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».</span><span class="sxs-lookup"><span data-stu-id="2c464-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2c464-120">Par défaut, un contrôle composite hérite de <xref:System.Windows.Forms.UserControl> la classe fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="2c464-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="2c464-121">La <xref:System.Windows.Forms.UserControl> classe fournit les fonctionnalités requises par tous les contrôles composites et implémente les méthodes et les propriétés standard.</span><span class="sxs-lookup"><span data-stu-id="2c464-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="2c464-122">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="2c464-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="2c464-123">Ajout de composants et de contrôles Windows au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-123">Adding Windows Controls and Components to the Composite Control</span></span>
 <span data-ttu-id="2c464-124">L’interface visuelle est un composant essentiel de votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="2c464-125">Cette interface visuelle est implémentée par l’ajout d’un ou de plusieurs contrôles Windows sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="2c464-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="2c464-126">Dans la démonstration suivante, vous allez intégrer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="2c464-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="2c464-127">Pour ajouter une étiquette et une minuterie à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="2c464-128">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="2c464-128">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="2c464-129">Dans la boîte à outils, développez le nœud **Contrôles communs**, puis double-cliquez sur **Étiquette**.</span><span class="sxs-lookup"><span data-stu-id="2c464-129">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="2c464-130">Un <xref:System.Windows.Forms.Label> contrôle nommé `Label1` est ajouté à votre contrôle sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="2c464-130">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="2c464-131">Dans le concepteur, cliquez sur **Label1**.</span><span class="sxs-lookup"><span data-stu-id="2c464-131">In the designer, click **Label1**.</span></span> <span data-ttu-id="2c464-132">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="2c464-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="2c464-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="2c464-133">Property</span></span>|<span data-ttu-id="2c464-134">Remplacer par</span><span class="sxs-lookup"><span data-stu-id="2c464-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="2c464-135">**Name**</span><span class="sxs-lookup"><span data-stu-id="2c464-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="2c464-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="2c464-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="2c464-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="2c464-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="2c464-138">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="2c464-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="2c464-139">Dans la **boîte à outils**, développez le nœud **Composants**, puis double-cliquez sur **Minuterie**.</span><span class="sxs-lookup"><span data-stu-id="2c464-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="2c464-140">Comme un <xref:System.Windows.Forms.Timer> est un composant, il n’a pas de représentation visuelle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c464-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="2c464-141">Par conséquent, il n’apparaît pas avec les contrôles sur l’aire du concepteur, mais plutôt dans le Concepteur de composants (une barre d’état située en bas de l’aire du concepteur).</span><span class="sxs-lookup"><span data-stu-id="2c464-141">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="2c464-142">Dans le concepteur de composants, cliquez sur **Timer1**, puis affectez à `1000` la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la <xref:System.Windows.Forms.Timer.Interval%2A> valeur `True`et à la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="2c464-142">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>

     <span data-ttu-id="2c464-143">La <xref:System.Windows.Forms.Timer.Interval%2A> propriété contrôle la fréquence à laquelle le composant Timer est en graduation.</span><span class="sxs-lookup"><span data-stu-id="2c464-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="2c464-144">À chaque nouvelle graduation du composant `Timer1`, le code est exécuté dans l’événement `Timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="2c464-144">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="2c464-145">L’intervalle représente le nombre de millisecondes entre les graduations.</span><span class="sxs-lookup"><span data-stu-id="2c464-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="2c464-146">Dans le Concepteur de composants, double-cliquez sur **Timer1** pour accéder à l’événement `Timer1_Tick` pour `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-146">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="2c464-147">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="2c464-148">Remplacez le paramètre de modificateur d’accès `Private` par `Protected`.</span><span class="sxs-lookup"><span data-stu-id="2c464-148">Be sure to change the access modifier from `Private` to `Protected`.</span></span>

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     <span data-ttu-id="2c464-149">Ce code entraînera l’affichage de l’heure actuelle dans `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="2c464-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="2c464-150">Étant donné que l’intervalle du composant `Timer1` a été défini sur `1000`, cet événement se produira toutes les mille millisecondes, mettant ainsi l’heure à jour toutes les secondes.</span><span class="sxs-lookup"><span data-stu-id="2c464-150">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="2c464-151">Modifiez la méthode afin qu’elle soit remplaçable.</span><span class="sxs-lookup"><span data-stu-id="2c464-151">Modify the method to be overridable.</span></span> <span data-ttu-id="2c464-152">Pour plus d’informations, consultez la section « Héritage d’un contrôle utilisateur » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2c464-152">For more information, see the "Inheriting from a User Control" section below.</span></span>

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. <span data-ttu-id="2c464-153">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="2c464-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="2c464-154">Ajout de propriétés au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-154">Adding Properties to the Composite Control</span></span>
 <span data-ttu-id="2c464-155">Votre contrôle Clock encapsule maintenant un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.Timer> composant, chacun avec son propre ensemble de propriétés inhérentes.</span><span class="sxs-lookup"><span data-stu-id="2c464-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="2c464-156">Même si les propriétés individuelles de ces contrôles ne seront pas accessibles aux autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés.</span><span class="sxs-lookup"><span data-stu-id="2c464-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="2c464-157">Dans la procédure suivante, vous allez ajouter des propriétés à votre contrôle qui permettent à l’utilisateur de modifier la couleur de l’arrière-plan et du texte.</span><span class="sxs-lookup"><span data-stu-id="2c464-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="2c464-158">Pour ajouter une propriété à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="2c464-159">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="2c464-159">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>

     <span data-ttu-id="2c464-160">L’éditeur de code de votre contrôle s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="2c464-160">The Code Editor for your control opens.</span></span>

2. <span data-ttu-id="2c464-161">Recherchez l’instruction `Public Class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-161">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="2c464-162">Sous l’instruction, saisissez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-162">Beneath it, type the following code.</span></span>

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     <span data-ttu-id="2c464-163">Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="2c464-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="2c464-164">Insérez le code suivant sous les déclarations de variable de l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="2c464-164">Insert the following code beneath the variable declarations from step 2.</span></span>

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     <span data-ttu-id="2c464-165">Le code précédent crée deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, auxquelles les autres utilisateurs du contrôle pourront accéder en appelant l’instruction `Property`.</span><span class="sxs-lookup"><span data-stu-id="2c464-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="2c464-166">`Get` et `Set` fournissent des instructions pour le stockage et la récupération de la valeur de propriété, ainsi que le code pour intégrer les fonctionnalités appropriées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="2c464-166">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="2c464-167">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="2c464-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="2c464-168">Test du contrôle</span><span class="sxs-lookup"><span data-stu-id="2c464-168">Testing the Control</span></span>
 <span data-ttu-id="2c464-169">Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="2c464-169">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="2c464-170">Testez le comportement de votre contrôle au moment de l’exécution et testez ses propriétés avec le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="2c464-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="2c464-171">Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c464-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="2c464-172">Pour tester votre contrôle</span><span class="sxs-lookup"><span data-stu-id="2c464-172">To test your control</span></span>

1. <span data-ttu-id="2c464-173">Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="2c464-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="2c464-174">Dans la grille des propriétés du conteneur de test, sélectionnez la propriété `ClockBackColor`, puis cliquez sur la flèche déroulante pour afficher la palette de couleurs.</span><span class="sxs-lookup"><span data-stu-id="2c464-174">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>

3. <span data-ttu-id="2c464-175">Choisissez une couleur en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="2c464-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="2c464-176">La couleur sélectionnée devient la couleur d’arrière-plan de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2c464-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="2c464-177">Utilisez une séquence d’événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="2c464-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

5. <span data-ttu-id="2c464-178">Cliquez sur **Fermer** pour fermer le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="2c464-178">Click **Close** to close the **UserControl Test Container**.</span></span>

     <span data-ttu-id="2c464-179">Dans cette section et les sections précédentes, vous avez vu comment les composants et contrôles Windows peuvent être combinés avec du code et de l’empaquetage afin d’offrir des fonctionnalités personnalisées sous la forme d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-179">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="2c464-180">Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester votre contrôle après sa configuration.</span><span class="sxs-lookup"><span data-stu-id="2c464-180">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="2c464-181">Dans la section suivante, vous allez apprendre à créer un contrôle composite hérité en utilisant `ctlClock` comme base.</span><span class="sxs-lookup"><span data-stu-id="2c464-181">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="2c464-182">Héritage d’un contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-182">Inheriting from a Composite Control</span></span>
 <span data-ttu-id="2c464-183">Dans les sections précédentes, vous avez appris à combiner du code, des composants et des contrôles Windows pour créer des contrôles composites réutilisables.</span><span class="sxs-lookup"><span data-stu-id="2c464-183">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="2c464-184">Votre contrôle composite peut maintenant être utilisé comme base pour créer d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="2c464-184">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="2c464-185">Le processus qui consiste à créer une classe à partir d’une classe de base est appelé *héritage*.</span><span class="sxs-lookup"><span data-stu-id="2c464-185">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="2c464-186">Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-186">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="2c464-187">Ce contrôle sera créé à partir de son contrôle parent, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-187">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="2c464-188">Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en remplaçant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.</span><span class="sxs-lookup"><span data-stu-id="2c464-188">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

 <span data-ttu-id="2c464-189">La première étape de la création d’un contrôle hérité consiste à le dériver de son parent.</span><span class="sxs-lookup"><span data-stu-id="2c464-189">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="2c464-190">Cette action crée un contrôle qui possède toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également être utilisé comme base pour l’ajout de fonctionnalités nouvelles ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="2c464-190">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="2c464-191">Pour créer le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="2c464-191">To create the inherited control</span></span>

1. <span data-ttu-id="2c464-192">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, pointez sur **Ajouter**, puis cliquez sur **Contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="2c464-192">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="2c464-193">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="2c464-193">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="2c464-194">Sélectionnez le modèle **Contrôle utilisateur hérité**.</span><span class="sxs-lookup"><span data-stu-id="2c464-194">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="2c464-195">Dans le champ **Nom**, saisissez `ctlAlarmClock.vb`, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2c464-195">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>

     <span data-ttu-id="2c464-196">La boîte de dialogue **Sélecteur d’héritage** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2c464-196">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="2c464-197">Sous **Nom du composant**, double-cliquez sur **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="2c464-197">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="2c464-198">Dans l’Explorateur de solutions, parcourez les projets en cours.</span><span class="sxs-lookup"><span data-stu-id="2c464-198">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2c464-199">Un fichier appelé **ctlAlarmClock.vb** a été ajouté au projet actuel.</span><span class="sxs-lookup"><span data-stu-id="2c464-199">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="2c464-200">Ajout de propriétés d’alarme</span><span class="sxs-lookup"><span data-stu-id="2c464-200">Adding the Alarm Properties</span></span>
 <span data-ttu-id="2c464-201">Les propriétés sont ajoutées à un contrôle hérité de la même façon qu’elles sont ajoutées à un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-201">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="2c464-202">Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la date et l’heure de désactivation de l’alarme, et `AlarmSet`, qui indique si oui ou non l’alarme est définie.</span><span class="sxs-lookup"><span data-stu-id="2c464-202">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="2c464-203">Pour ajouter des propriétés à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="2c464-203">To add properties to your composite control</span></span>

1. <span data-ttu-id="2c464-204">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="2c464-204">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="2c464-205">Recherchez la déclaration de classe pour le contrôle ctlAlarmClock qui apparaît sous la forme `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-205">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="2c464-206">Dans la déclaration de classe, insérez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-206">In the class declaration, insert the following code.</span></span>

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="2c464-207">Ajout de l’interface graphique du contrôle</span><span class="sxs-lookup"><span data-stu-id="2c464-207">Adding to the Graphical Interface of the Control</span></span>
 <span data-ttu-id="2c464-208">Votre contrôle hérité possède une interface visuelle qui est identique à celle du contrôle dont il a hérité.</span><span class="sxs-lookup"><span data-stu-id="2c464-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="2c464-209">Il possède les mêmes contrôles constitutifs que son contrôle parent, mais les propriétés de ces contrôles ne seront pas disponibles, sauf si elles ont été spécifiquement exposées.</span><span class="sxs-lookup"><span data-stu-id="2c464-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="2c464-210">Vous pouvez ajouter des éléments à l’interface graphique d’un contrôle composite hérité de la même manière que vous ajoutez des éléments à tout autre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="2c464-211">Pour continuer à ajouter des éléments à l’interface visuelle de votre alarme, vous allez ajouter un contrôle Étiquette qui clignote lorsque l’alarme sonne.</span><span class="sxs-lookup"><span data-stu-id="2c464-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="2c464-212">Pour ajouter le contrôle Étiquette</span><span class="sxs-lookup"><span data-stu-id="2c464-212">To add the label control</span></span>

1. <span data-ttu-id="2c464-213">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="2c464-213">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>

     <span data-ttu-id="2c464-214">Le concepteur pour `ctlAlarmClock` s’ouvre dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="2c464-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="2c464-215">Cliquez sur `lblDisplay` (la partie visible du contrôle) et affichez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="2c464-215">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2c464-216">Toutes les propriétés qui s’affichent sont grisées.</span><span class="sxs-lookup"><span data-stu-id="2c464-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="2c464-217">Cela indique que ces propriétés sont propres à `lblDisplay` et ne peuvent pas être modifiées ou sélectionnées dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="2c464-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="2c464-218">Par défaut, les contrôles contenus dans un contrôle composite sont à l’état `Private`, et leurs propriétés ne sont accessibles d’aucune façon.</span><span class="sxs-lookup"><span data-stu-id="2c464-218">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2c464-219">Si vous souhaitez que d’autres utilisateurs de votre contrôle composite puissent accéder à ses contrôles internes, définissez leur état sur `Public` ou `Protected`.</span><span class="sxs-lookup"><span data-stu-id="2c464-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="2c464-220">Cela vous permettra de définir et de modifier les propriétés des contrôles contenus dans votre contrôle composite à l’aide du code approprié.</span><span class="sxs-lookup"><span data-stu-id="2c464-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="2c464-221">Ajoutez un <xref:System.Windows.Forms.Label> contrôle à votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="2c464-222">À l’aide de la souris <xref:System.Windows.Forms.Label> , faites glisser le contrôle immédiatement en dessous de la zone d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2c464-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="2c464-223">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="2c464-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="2c464-224">Propriété</span><span class="sxs-lookup"><span data-stu-id="2c464-224">Property</span></span>|<span data-ttu-id="2c464-225">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2c464-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="2c464-226">**Name**</span><span class="sxs-lookup"><span data-stu-id="2c464-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="2c464-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="2c464-227">**Text**</span></span>|<span data-ttu-id="2c464-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="2c464-228">**Alarm!**</span></span>|
    |<span data-ttu-id="2c464-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="2c464-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="2c464-230">**Visible**</span><span class="sxs-lookup"><span data-stu-id="2c464-230">**Visible**</span></span>|`False`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="2c464-231">Ajout de la fonctionnalité d’alarme</span><span class="sxs-lookup"><span data-stu-id="2c464-231">Adding the Alarm Functionality</span></span>
 <span data-ttu-id="2c464-232">Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle permettant d’activer la fonctionnalité d’alarme dans votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="2c464-233">Dans cette procédure, vous allez ajouter du code pour comparer l’heure actuelle à l’heure de l’alarme et, si elles sont identiques, déclencher le son et le clignotement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="2c464-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="2c464-234">En remplaçant la méthode `Timer1_Tick` de `ctlClock` et en lui ajoutant du code, vous allez étendre les capacités de `ctlAlarmClock` tout en conservant les fonctionnalités inhérentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-234">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="2c464-235">Pour remplacer la méthode Timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="2c464-235">To override the Timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="2c464-236">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="2c464-236">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>

2. <span data-ttu-id="2c464-237">Recherchez l’instruction `Private blnAlarmSet As Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2c464-237">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="2c464-238">Juste en dessous de l’instruction, ajoutez l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="2c464-238">Immediately beneath it, add the following statement.</span></span>

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. <span data-ttu-id="2c464-239">Recherchez l’instruction `End Class` au bas de la page.</span><span class="sxs-lookup"><span data-stu-id="2c464-239">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="2c464-240">Juste avant l’instruction `End Class`, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-240">Just before the `End Class` statement, add the following code.</span></span>

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     <span data-ttu-id="2c464-241">L’ajout de ce code permet d’effectuer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="2c464-241">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="2c464-242">L’instruction `Overrides` ordonne au contrôle d’utiliser cette méthode à la place de la méthode héritée du contrôle de base.</span><span class="sxs-lookup"><span data-stu-id="2c464-242">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="2c464-243">Lorsque cette méthode est appelée, elle appelle la méthode qu’elle remplace en appelant l’instruction `MyBase.Timer1_Tick`, ce qui permet de s’assurer que toutes les fonctionnalités intégrées au contrôle d’origine sont également intégrées à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="2c464-243">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="2c464-244">Du code supplémentaire est ensuite exécuté pour intégrer la fonctionnalité d’alarme.</span><span class="sxs-lookup"><span data-stu-id="2c464-244">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="2c464-245">Lorsque l’alarme se déclenche, un contrôle Étiquette clignotant apparaît et un signal sonore retentit.</span><span class="sxs-lookup"><span data-stu-id="2c464-245">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2c464-246">Comme vous remplacez un gestionnaire d’événements hérité, il n’est pas nécessaire de spécifier l’événement avec le mot clé `Handles`.</span><span class="sxs-lookup"><span data-stu-id="2c464-246">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="2c464-247">L’événement est déjà rattaché.</span><span class="sxs-lookup"><span data-stu-id="2c464-247">The event is already hooked up.</span></span> <span data-ttu-id="2c464-248">Tout ce que vous remplacez est l’implémentation du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="2c464-248">All you are overriding is the implementation of the handler.</span></span>

     <span data-ttu-id="2c464-249">Votre contrôle d’alarme est presque terminé.</span><span class="sxs-lookup"><span data-stu-id="2c464-249">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="2c464-250">La seule chose qui reste à faire est de mettre en place un moyen de le désactiver.</span><span class="sxs-lookup"><span data-stu-id="2c464-250">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="2c464-251">Pour ce faire, vous allez ajouter du code à la méthode `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="2c464-251">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="2c464-252">Pour implémenter la méthode de désactivation</span><span class="sxs-lookup"><span data-stu-id="2c464-252">To implement the shutoff method</span></span>

1. <span data-ttu-id="2c464-253">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="2c464-253">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="2c464-254">Dans le concepteur, double-cliquez sur **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="2c464-254">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="2c464-255">**L’éditeur de code** s’ouvre à la ligne `Private Sub lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="2c464-255">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>

3. <span data-ttu-id="2c464-256">Modifiez cette méthode afin qu’elle ressemble au code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-256">Modify this method so that it resembles the following code.</span></span>

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. <span data-ttu-id="2c464-257">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="2c464-257">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="2c464-258">Utilisation du contrôle hérité sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="2c464-258">Using the Inherited Control on a Form</span></span>
 <span data-ttu-id="2c464-259">Vous pouvez tester votre contrôle hérité de la même façon que vous avez testé le contrôle `ctlClock`de classe de base,: Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="2c464-259">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="2c464-260">Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c464-260">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

 <span data-ttu-id="2c464-261">Pour pouvoir utiliser votre contrôle, vous devrez l’héberger dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="2c464-261">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="2c464-262">À l’instar d’un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de manière autonome et doit être hébergé dans un formulaire ou un autre conteneur.</span><span class="sxs-lookup"><span data-stu-id="2c464-262">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="2c464-263">Étant donné que `ctlAlarmClock` présente davantage de fonctionnalités, du code supplémentaire est nécessaire pour le tester.</span><span class="sxs-lookup"><span data-stu-id="2c464-263">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="2c464-264">Dans cette procédure, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-264">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="2c464-265">Vous allez écrire du code pour définir et afficher la propriété `AlarmTime` de `ctlAlarmClock`, puis vous testerez ses fonctions inhérentes.</span><span class="sxs-lookup"><span data-stu-id="2c464-265">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="2c464-266">Pour générer votre contrôle et l’ajouter à un formulaire de test</span><span class="sxs-lookup"><span data-stu-id="2c464-266">To build and add your control to a test form</span></span>

1. <span data-ttu-id="2c464-267">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="2c464-267">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="2c464-268">Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="2c464-268">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>

3. <span data-ttu-id="2c464-269">Ajoutez un nouveau projet **d’application Windows** à la solution et nommez-le `Test`.</span><span class="sxs-lookup"><span data-stu-id="2c464-269">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

     <span data-ttu-id="2c464-270">Le projet **Test** est ajouté à l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="2c464-270">The **Test** project is added to Solution Explorer.</span></span>

4. <span data-ttu-id="2c464-271">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet `Test`, puis cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="2c464-271">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="2c464-272">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="2c464-272">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="2c464-273">Le projet **ctlClockLib** s’affiche sous **Nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="2c464-273">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="2c464-274">Double-cliquez sur **ctlClockLib** pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="2c464-274">Double-click **ctlClockLib** to add the reference to the test project.</span></span>

6. <span data-ttu-id="2c464-275">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="2c464-275">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

7. <span data-ttu-id="2c464-276">Dans la **boîte à outils**, développez le nœud **Composants ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="2c464-276">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

8. <span data-ttu-id="2c464-277">Double-cliquez sur **ctlAlarmClock** pour ajouter une instance de `ctlAlarmClock` à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="2c464-277">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>

9. <span data-ttu-id="2c464-278">Dans la **boîte à outils**, recherchez et double -cliquez sur DateTimePicker <xref:System.Windows.Forms.DateTimePicker> pour ajouter un contrôle à votre formulaire, puis <xref:System.Windows.Forms.Label> ajoutez un contrôle en double-cliquant sur **étiquette**.</span><span class="sxs-lookup"><span data-stu-id="2c464-278">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

10. <span data-ttu-id="2c464-279">Utilisez la souris pour positionner les contrôles à un endroit approprié sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2c464-279">Use the mouse to position the controls in a convenient place on the form.</span></span>

11. <span data-ttu-id="2c464-280">Définissez les propriétés de ces contrôles de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="2c464-280">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="2c464-281">Contrôle</span><span class="sxs-lookup"><span data-stu-id="2c464-281">Control</span></span>|<span data-ttu-id="2c464-282">Propriété</span><span class="sxs-lookup"><span data-stu-id="2c464-282">Property</span></span>|<span data-ttu-id="2c464-283">Value</span><span class="sxs-lookup"><span data-stu-id="2c464-283">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="2c464-284">**Text**</span><span class="sxs-lookup"><span data-stu-id="2c464-284">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="2c464-285">**Name**</span><span class="sxs-lookup"><span data-stu-id="2c464-285">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="2c464-286">**Name**</span><span class="sxs-lookup"><span data-stu-id="2c464-286">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="2c464-287">**Format**</span><span class="sxs-lookup"><span data-stu-id="2c464-287">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. <span data-ttu-id="2c464-288">Dans le concepteur, double-cliquez sur **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="2c464-288">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="2c464-289">**L’éditeur de code** s’ouvre à la ligne `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="2c464-289">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>

13. <span data-ttu-id="2c464-290">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c464-290">Modify the code so that it resembles the following.</span></span>

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. <span data-ttu-id="2c464-291">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="2c464-291">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

15. <span data-ttu-id="2c464-292">Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="2c464-292">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="2c464-293">Le programme de test démarre.</span><span class="sxs-lookup"><span data-stu-id="2c464-293">The test program starts.</span></span> <span data-ttu-id="2c464-294">Notez que l’heure actuelle est mise à jour `ctlAlarmClock` dans le contrôle et que l’heure de début est affichée <xref:System.Windows.Forms.DateTimePicker> dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2c464-294">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

16. <span data-ttu-id="2c464-295">Cliquez sur <xref:System.Windows.Forms.DateTimePicker> l’emplacement où les minutes de l’heure sont affichées.</span><span class="sxs-lookup"><span data-stu-id="2c464-295">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

17. <span data-ttu-id="2c464-296">À l’aide du clavier, définissez une valeur pour les minutes comportant une minute de plus que l’heure actuelle affichée par `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="2c464-296">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="2c464-297">L’heure de déclenchement de l’alarme apparaît dans `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="2c464-297">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="2c464-298">Attendez que l’heure affichée atteigne l’heure de déclenchement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="2c464-298">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="2c464-299">Lorsque l’heure affichée atteint l’heure sur laquelle l’alarme a été définie, un signal sonore retentit et `lblAlarm` se met à clignoter.</span><span class="sxs-lookup"><span data-stu-id="2c464-299">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>

18. <span data-ttu-id="2c464-300">Désactivez l’alarme en cliquant sur `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="2c464-300">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="2c464-301">Vous pouvez maintenant réinitialiser l’alarme.</span><span class="sxs-lookup"><span data-stu-id="2c464-301">You may now reset the alarm.</span></span>

     <span data-ttu-id="2c464-302">Cette procédure pas à pas a abordé plusieurs concepts clés.</span><span class="sxs-lookup"><span data-stu-id="2c464-302">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="2c464-303">Vous avez appris à créer un contrôle composite en combinant des contrôles et des composants dans un conteneur de contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="2c464-303">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="2c464-304">Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code pour implémenter des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2c464-304">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="2c464-305">Dans la dernière section, vous avez appris à étendre les fonctionnalités d’un contrôle composite grâce à l’héritage et à modifier les fonctionnalités des méthodes hôtes en remplaçant ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="2c464-305">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c464-306">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c464-306">See also</span></span>

- [<span data-ttu-id="2c464-307">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="2c464-307">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="2c464-308">Guide pratique pour Créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="2c464-308">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="2c464-309">Guide pratique pour Afficher un contrôle dans la boîte de dialogue choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="2c464-309">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
