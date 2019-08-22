---
title: "Procédure pas à pas : Création d'un contrôle composite à l'aide de Visual C#"
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 12b506e859579a0755c2e9842e792c59968c94a8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666752"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="aadb4-102">Procédure pas à pas : Création d’un contrôle composite à l’aide de Visual C\#</span><span class="sxs-lookup"><span data-stu-id="aadb4-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>

<span data-ttu-id="aadb4-103">Les contrôles composites permettent de créer et de réutiliser des interfaces graphiques personnalisées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="aadb4-104">Un contrôle composite est avant tout un composant doté d’une représentation visuelle.</span><span class="sxs-lookup"><span data-stu-id="aadb4-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="aadb4-105">Par conséquent, il peut comporter un ou plusieurs blocs de code, composants ou contrôles Windows Forms qui peuvent en étendre les fonctionnalités en validant les entrées d’utilisateur, en modifiant les propriétés d’affichage ou en effectuant d’autres tâches requises par l’auteur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="aadb4-106">Les contrôles composites peuvent être insérés dans les Windows Forms de la même manière que les autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="aadb4-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="aadb4-107">Dans la première partie de cette procédure pas à pas, vous allez créer un contrôle composite simple appelé `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="aadb4-108">Dans la seconde partie de la procédure pas à pas, vous allez étendre les fonctionnalités de `ctlClock` via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="aadb4-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="aadb4-109">Création du projet</span><span class="sxs-lookup"><span data-stu-id="aadb4-109">Creating the Project</span></span>

<span data-ttu-id="aadb4-110">Lorsque vous créez un nouveau projet, vous spécifiez son nom pour définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="aadb4-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="aadb4-111">Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock</span><span class="sxs-lookup"><span data-stu-id="aadb4-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="aadb4-112">Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="aadb4-113">Dans la liste des projets C# visuels, sélectionnez le modèle de projet **bibliothèque de contrôles Windows Forms** , tapez `ctlClockLib` dans la zone **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-113">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="aadb4-114">Le nom du projet, `ctlClockLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="aadb4-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="aadb4-115">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="aadb4-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="aadb4-116">Par exemple, si deux assemblies contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l’aide de `ctlClockLib.ctlClock.`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="aadb4-117">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **UserControl1.cs**, puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-117">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="aadb4-118">Remplacez le nom de fichier par `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-118">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="aadb4-119">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».</span><span class="sxs-lookup"><span data-stu-id="aadb4-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="aadb4-120">Par défaut, un contrôle composite hérite de <xref:System.Windows.Forms.UserControl> la classe fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="aadb4-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="aadb4-121">La <xref:System.Windows.Forms.UserControl> classe fournit les fonctionnalités requises par tous les contrôles composites et implémente les méthodes et les propriétés standard.</span><span class="sxs-lookup"><span data-stu-id="aadb4-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="aadb4-122">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="aadb4-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="aadb4-123">Ajout de composants et de contrôles Windows au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-123">Adding Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="aadb4-124">L’interface visuelle est un composant essentiel de votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="aadb4-125">Cette interface visuelle est implémentée par l’ajout d’un ou de plusieurs contrôles Windows sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="aadb4-126">Dans la démonstration suivante, vous allez intégrer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="aadb4-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="aadb4-127">Pour ajouter une étiquette et une minuterie à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="aadb4-128">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.cs**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-128">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="aadb4-129">Dans la **boîte à outils**, développez le nœud **Contrôles communs**, puis double-cliquez sur **Étiquette**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-129">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="aadb4-130">Un <xref:System.Windows.Forms.Label> contrôle nommé `label1` est ajouté à votre contrôle sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-130">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="aadb4-131">Dans le concepteur, cliquez sur **label1**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-131">In the designer, click **label1**.</span></span> <span data-ttu-id="aadb4-132">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="aadb4-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="aadb4-133">Property</span></span>|<span data-ttu-id="aadb4-134">Remplacer par</span><span class="sxs-lookup"><span data-stu-id="aadb4-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="aadb4-135">**Name**</span><span class="sxs-lookup"><span data-stu-id="aadb4-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="aadb4-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="aadb4-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="aadb4-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="aadb4-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="aadb4-138">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="aadb4-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="aadb4-139">Dans la **boîte à outils**, développez le nœud **Composants**, puis double-cliquez sur **Minuterie**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="aadb4-140">Comme un <xref:System.Windows.Forms.Timer> est un composant, il n’a pas de représentation visuelle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="aadb4-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="aadb4-141">Par conséquent, il n’apparaît pas avec les contrôles sur l’aire du concepteur, mais plutôt dans le **Concepteur de composants** (une barre d’état située en bas de l’aire du concepteur).</span><span class="sxs-lookup"><span data-stu-id="aadb4-141">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="aadb4-142">Dans le **Concepteur de composants**, cliquez sur **Timer1**, puis affectez à `1000` la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la <xref:System.Windows.Forms.Timer.Interval%2A> valeur `true`et à la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-142">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="aadb4-143">La <xref:System.Windows.Forms.Timer.Interval%2A> propriété contrôle la fréquence à laquelle le <xref:System.Windows.Forms.Timer> composant est gradué.</span><span class="sxs-lookup"><span data-stu-id="aadb4-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="aadb4-144">À chaque nouvelle graduation du composant `timer1`, le code est exécuté dans l’événement `timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-144">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="aadb4-145">L’intervalle représente le nombre de millisecondes entre les graduations.</span><span class="sxs-lookup"><span data-stu-id="aadb4-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="aadb4-146">Dans le **Concepteur de composants**, double-cliquez sur **timer1** pour accéder à l’événement `timer1_Tick` pour `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-146">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="aadb4-147">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="aadb4-148">Remplacez le paramètre de modificateur d’accès `private` par `protected`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-148">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="aadb4-149">Ce code entraînera l’affichage de l’heure actuelle dans `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="aadb4-150">Étant donné que l’intervalle du composant `timer1` a été défini sur `1000`, cet événement se produira toutes les mille millisecondes, mettant ainsi l’heure à jour toutes les secondes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-150">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="aadb4-151">Modifiez la méthode afin qu’elle soit remplaçable à l’aide du mot clé `virtual`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-151">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="aadb4-152">Pour plus d’informations, consultez la section « Héritage d’un contrôle utilisateur » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="aadb4-152">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="aadb4-153">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="aadb4-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="aadb4-154">Ajout de propriétés au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-154">Adding Properties to the Composite Control</span></span>

<span data-ttu-id="aadb4-155">Votre contrôle Clock encapsule maintenant un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.Timer> composant, chacun avec son propre ensemble de propriétés inhérentes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="aadb4-156">Même si les propriétés individuelles de ces contrôles ne seront pas accessibles aux autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés.</span><span class="sxs-lookup"><span data-stu-id="aadb4-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="aadb4-157">Dans la procédure suivante, vous allez ajouter des propriétés à votre contrôle qui permettent à l’utilisateur de modifier la couleur de l’arrière-plan et du texte.</span><span class="sxs-lookup"><span data-stu-id="aadb4-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="aadb4-158">Pour ajouter une propriété à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="aadb4-159">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.cs**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-159">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="aadb4-160">**L’éditeur de code** de votre contrôle s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="aadb4-160">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="aadb4-161">Recherchez l’instruction `public partial class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-161">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="aadb4-162">Sous l’accolade ouvrante (`{)`, saisissez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-162">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="aadb4-163">Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="aadb4-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="aadb4-164">Saisissez le code suivant sous les déclarations de variable de l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="aadb4-164">Type the following code beneath the variable declarations from step 2.</span></span>

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     <span data-ttu-id="aadb4-165">Le code précédent crée deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, auxquelles les autres utilisateurs du contrôle pourront accéder.</span><span class="sxs-lookup"><span data-stu-id="aadb4-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="aadb4-166">`get` et `set` fournissent des instructions pour le stockage et la récupération de la valeur de propriété, ainsi que le code pour intégrer les fonctionnalités appropriées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="aadb4-166">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="aadb4-167">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="aadb4-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="aadb4-168">Test du contrôle</span><span class="sxs-lookup"><span data-stu-id="aadb4-168">Testing the Control</span></span>

<span data-ttu-id="aadb4-169">Les contrôles ne sont pas des applications autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-169">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="aadb4-170">Testez le comportement de votre contrôle au moment de l’exécution et testez ses propriétés avec le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="aadb4-171">Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="aadb4-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="aadb4-172">Pour tester votre contrôle</span><span class="sxs-lookup"><span data-stu-id="aadb4-172">To test your control</span></span>

1. <span data-ttu-id="aadb4-173">Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="aadb4-174">Dans la grille des propriétés du conteneur de test, recherchez la propriété `ClockBackColor`, puis sélectionnez la propriété pour afficher la palette de couleurs.</span><span class="sxs-lookup"><span data-stu-id="aadb4-174">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="aadb4-175">Choisissez une couleur en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="aadb4-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="aadb4-176">La couleur sélectionnée devient la couleur d’arrière-plan de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="aadb4-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="aadb4-177">Utilisez une séquence d’événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="aadb4-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

     <span data-ttu-id="aadb4-178">Dans cette section et les sections précédentes, vous avez vu comment les composants et contrôles Windows peuvent être combinés avec du code et de l’empaquetage afin d’offrir des fonctionnalités personnalisées sous la forme d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-178">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="aadb4-179">Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester votre contrôle après sa configuration.</span><span class="sxs-lookup"><span data-stu-id="aadb4-179">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="aadb4-180">Dans la section suivante, vous allez apprendre à créer un contrôle composite hérité en utilisant `ctlClock` comme base.</span><span class="sxs-lookup"><span data-stu-id="aadb4-180">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="aadb4-181">Héritage d’un contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-181">Inheriting from a Composite Control</span></span>

<span data-ttu-id="aadb4-182">Dans les sections précédentes, vous avez appris à combiner du code, des composants et des contrôles Windows pour créer des contrôles composites réutilisables.</span><span class="sxs-lookup"><span data-stu-id="aadb4-182">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="aadb4-183">Votre contrôle composite peut maintenant être utilisé comme base pour créer d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="aadb4-183">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="aadb4-184">Le processus qui consiste à créer une classe à partir d’une classe de base est appelé *héritage*.</span><span class="sxs-lookup"><span data-stu-id="aadb4-184">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="aadb4-185">Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-185">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="aadb4-186">Ce contrôle sera créé à partir de son contrôle parent, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-186">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="aadb4-187">Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en remplaçant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.</span><span class="sxs-lookup"><span data-stu-id="aadb4-187">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="aadb4-188">La première étape de la création d’un contrôle hérité consiste à le dériver de son parent.</span><span class="sxs-lookup"><span data-stu-id="aadb4-188">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="aadb4-189">Cette action crée un contrôle qui possède toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également être utilisé comme base pour l’ajout de fonctionnalités nouvelles ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-189">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="aadb4-190">Pour créer le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="aadb4-190">To create the inherited control</span></span>

1. <span data-ttu-id="aadb4-191">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, pointez sur **Ajouter**, puis cliquez sur **Contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-191">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="aadb4-192">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="aadb4-192">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="aadb4-193">Sélectionnez le modèle **Contrôle utilisateur hérité**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-193">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="aadb4-194">Dans le champ **Nom**, saisissez `ctlAlarmClock.cs`, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-194">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="aadb4-195">La boîte de dialogue **Sélecteur d’héritage** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="aadb4-195">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="aadb4-196">Sous **Nom du composant**, double-cliquez sur **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-196">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="aadb4-197">Dans l’Explorateur de solutions, parcourez les projets en cours.</span><span class="sxs-lookup"><span data-stu-id="aadb4-197">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="aadb4-198">Un fichier appelé **ctlAlarmClock.cs** a été ajouté au projet actuel.</span><span class="sxs-lookup"><span data-stu-id="aadb4-198">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="aadb4-199">Ajout de propriétés d’alarme</span><span class="sxs-lookup"><span data-stu-id="aadb4-199">Adding the Alarm Properties</span></span>

<span data-ttu-id="aadb4-200">Les propriétés sont ajoutées à un contrôle hérité de la même façon qu’elles sont ajoutées à un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-200">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="aadb4-201">Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la date et l’heure de désactivation de l’alarme, et `AlarmSet`, qui indique si oui ou non l’alarme est définie.</span><span class="sxs-lookup"><span data-stu-id="aadb4-201">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="aadb4-202">Pour ajouter des propriétés à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="aadb4-202">To add properties to your composite control</span></span>

1. <span data-ttu-id="aadb4-203">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-203">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="aadb4-204">Recherchez l’instruction `public class`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-204">Locate the `public class` statement.</span></span> <span data-ttu-id="aadb4-205">Notez que votre contrôle hérite de `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-205">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="aadb4-206">Sous l’accolade ouvrante (`{)`, saisissez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-206">Beneath the opening brace (`{)` statement, type the following code.</span></span>

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="aadb4-207">Ajout de l’interface graphique du contrôle</span><span class="sxs-lookup"><span data-stu-id="aadb4-207">Adding to the Graphical Interface of the Control</span></span>

<span data-ttu-id="aadb4-208">Votre contrôle hérité possède une interface visuelle qui est identique à celle du contrôle dont il a hérité.</span><span class="sxs-lookup"><span data-stu-id="aadb4-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="aadb4-209">Il possède les mêmes contrôles constitutifs que son contrôle parent, mais les propriétés de ces contrôles ne seront pas disponibles, sauf si elles ont été spécifiquement exposées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="aadb4-210">Vous pouvez ajouter des éléments à l’interface graphique d’un contrôle composite hérité de la même manière que vous ajoutez des éléments à tout autre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="aadb4-211">Pour continuer à ajouter des éléments à l’interface visuelle de votre alarme, vous allez ajouter un contrôle Étiquette qui clignote lorsque l’alarme sonne.</span><span class="sxs-lookup"><span data-stu-id="aadb4-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="aadb4-212">Pour ajouter le contrôle Étiquette</span><span class="sxs-lookup"><span data-stu-id="aadb4-212">To add the label control</span></span>

1. <span data-ttu-id="aadb4-213">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-213">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="aadb4-214">Le concepteur pour `ctlAlarmClock` s’ouvre dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="aadb4-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="aadb4-215">Cliquez sur la partie visible du contrôle et affichez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="aadb4-215">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aadb4-216">Toutes les propriétés qui s’affichent sont grisées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="aadb4-217">Cela indique que ces propriétés sont propres à `lblDisplay` et ne peuvent pas être modifiées ou sélectionnées dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="aadb4-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="aadb4-218">Par défaut, les contrôles contenus dans un contrôle composite sont à l’état `private`, et leurs propriétés ne sont accessibles d’aucune façon.</span><span class="sxs-lookup"><span data-stu-id="aadb4-218">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aadb4-219">Si vous souhaitez que d’autres utilisateurs de votre contrôle composite puissent accéder à ses contrôles internes, définissez leur état sur `public` ou `protected`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="aadb4-220">Cela vous permettra de définir et de modifier les propriétés des contrôles contenus dans votre contrôle composite à l’aide du code approprié.</span><span class="sxs-lookup"><span data-stu-id="aadb4-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="aadb4-221">Ajoutez un <xref:System.Windows.Forms.Label> contrôle à votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="aadb4-222">À l’aide de la souris <xref:System.Windows.Forms.Label> , faites glisser le contrôle immédiatement en dessous de la zone d’affichage.</span><span class="sxs-lookup"><span data-stu-id="aadb4-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="aadb4-223">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="aadb4-224">Propriété</span><span class="sxs-lookup"><span data-stu-id="aadb4-224">Property</span></span>|<span data-ttu-id="aadb4-225">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aadb4-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="aadb4-226">**Name**</span><span class="sxs-lookup"><span data-stu-id="aadb4-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="aadb4-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="aadb4-227">**Text**</span></span>|<span data-ttu-id="aadb4-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="aadb4-228">**Alarm!**</span></span>|
    |<span data-ttu-id="aadb4-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="aadb4-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="aadb4-230">**Visible**</span><span class="sxs-lookup"><span data-stu-id="aadb4-230">**Visible**</span></span>|`false`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="aadb4-231">Ajout de la fonctionnalité d’alarme</span><span class="sxs-lookup"><span data-stu-id="aadb4-231">Adding the Alarm Functionality</span></span>

<span data-ttu-id="aadb4-232">Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle permettant d’activer la fonctionnalité d’alarme dans votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="aadb4-233">Dans cette procédure, vous allez ajouter du code pour comparer l’heure actuelle à l’heure de l’alarme et, si elles sont identiques, déclencher le clignotement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="aadb4-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="aadb4-234">En remplaçant la méthode `timer1_Tick` de `ctlClock` et en lui ajoutant du code, vous allez étendre les capacités de `ctlAlarmClock` tout en conservant les fonctionnalités inhérentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-234">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="aadb4-235">Pour remplacer la méthode timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="aadb4-235">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="aadb4-236">Dans **l’éditeur de code**, recherchez l’instruction `private bool blnAlarmSet;`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-236">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="aadb4-237">Juste en dessous de l’instruction, ajoutez l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="aadb4-237">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="aadb4-238">Dans **l’éditeur de code**, recherchez l’accolade fermante (`})` à la fin de la classe.</span><span class="sxs-lookup"><span data-stu-id="aadb4-238">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="aadb4-239">Juste avant l’accolade, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-239">Just before the brace, add the following code.</span></span>

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     <span data-ttu-id="aadb4-240">L’ajout de ce code permet d’effectuer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="aadb4-240">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="aadb4-241">L’instruction `override` ordonne au contrôle d’utiliser cette méthode à la place de la méthode héritée du contrôle de base.</span><span class="sxs-lookup"><span data-stu-id="aadb4-241">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="aadb4-242">Lorsque cette méthode est appelée, elle appelle la méthode qu’elle remplace en appelant l’instruction `base.timer1_Tick`, ce qui permet de s’assurer que toutes les fonctionnalités intégrées au contrôle d’origine sont également intégrées à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="aadb4-242">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="aadb4-243">Du code supplémentaire est ensuite exécuté pour intégrer la fonctionnalité d’alarme.</span><span class="sxs-lookup"><span data-stu-id="aadb4-243">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="aadb4-244">Lorsque l’alarme se déclenche, un contrôle Étiquette clignotant apparaît.</span><span class="sxs-lookup"><span data-stu-id="aadb4-244">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="aadb4-245">Votre contrôle d’alarme est presque terminé.</span><span class="sxs-lookup"><span data-stu-id="aadb4-245">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="aadb4-246">La seule chose qui reste à faire est de mettre en place un moyen de le désactiver.</span><span class="sxs-lookup"><span data-stu-id="aadb4-246">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="aadb4-247">Pour ce faire, vous allez ajouter du code à la méthode `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-247">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="aadb4-248">Pour implémenter la méthode de désactivation</span><span class="sxs-lookup"><span data-stu-id="aadb4-248">To implement the shutoff method</span></span>

1. <span data-ttu-id="aadb4-249">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.cs**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-249">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="aadb4-250">Le concepteur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="aadb4-250">The designer opens.</span></span>

2. <span data-ttu-id="aadb4-251">Ajoutez un bouton au contrôle.</span><span class="sxs-lookup"><span data-stu-id="aadb4-251">Add a button to the control.</span></span> <span data-ttu-id="aadb4-252">Définissez les propriétés du bouton comme suit.</span><span class="sxs-lookup"><span data-stu-id="aadb4-252">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="aadb4-253">Propriété</span><span class="sxs-lookup"><span data-stu-id="aadb4-253">Property</span></span>|<span data-ttu-id="aadb4-254">Value</span><span class="sxs-lookup"><span data-stu-id="aadb4-254">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="aadb4-255">**Name**</span><span class="sxs-lookup"><span data-stu-id="aadb4-255">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="aadb4-256">**Text**</span><span class="sxs-lookup"><span data-stu-id="aadb4-256">**Text**</span></span>|<span data-ttu-id="aadb4-257">**Désactiver l’alarme**</span><span class="sxs-lookup"><span data-stu-id="aadb4-257">**Disable Alarm**</span></span>|

3. <span data-ttu-id="aadb4-258">Dans le concepteur, double-cliquez sur **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-258">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="aadb4-259">**L’éditeur de code** s’ouvre à la ligne `private void btnAlarmOff_Click`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-259">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="aadb4-260">Modifiez cette méthode afin qu’elle ressemble au code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-260">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="aadb4-261">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="aadb4-261">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="aadb4-262">Utilisation du contrôle hérité sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="aadb4-262">Using the Inherited Control on a Form</span></span>

<span data-ttu-id="aadb4-263">Vous pouvez tester votre contrôle hérité de la même façon que vous avez testé le contrôle `ctlClock`de classe de base,: Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-263">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="aadb4-264">Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="aadb4-264">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="aadb4-265">Pour pouvoir utiliser votre contrôle, vous devrez l’héberger dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="aadb4-265">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="aadb4-266">À l’instar d’un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de manière autonome et doit être hébergé dans un formulaire ou un autre conteneur.</span><span class="sxs-lookup"><span data-stu-id="aadb4-266">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="aadb4-267">Étant donné que `ctlAlarmClock` présente davantage de fonctionnalités, du code supplémentaire est nécessaire pour le tester.</span><span class="sxs-lookup"><span data-stu-id="aadb4-267">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="aadb4-268">Dans cette procédure, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-268">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="aadb4-269">Vous allez écrire du code pour définir et afficher la propriété `AlarmTime` de `ctlAlarmClock`, puis vous testerez ses fonctions inhérentes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-269">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="aadb4-270">Pour générer votre contrôle et l’ajouter à un formulaire de test</span><span class="sxs-lookup"><span data-stu-id="aadb4-270">To build and add your control to a test form</span></span>

1. <span data-ttu-id="aadb4-271">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-271">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="aadb4-272">Ajoutez un nouveau projet **d’application Windows** à la solution et nommez-le `Test`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

3. <span data-ttu-id="aadb4-273">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test.</span><span class="sxs-lookup"><span data-stu-id="aadb4-273">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="aadb4-274">Cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-274">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="aadb4-275">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="aadb4-276">Votre projet `ctlClockLib` s’affiche sous **Nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-276">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="aadb4-277">Double-cliquez sur le projet pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="aadb4-277">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="aadb4-278">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="aadb4-279">Dans la **boîte à outils**, développez le nœud **Composants ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="aadb4-280">Double-cliquez sur **ctlAlarmClock** pour ajouter une copie de `ctlAlarmClock` à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="aadb4-280">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="aadb4-281">Dans la **boîte à outils**, recherchez et double -cliquez sur DateTimePicker <xref:System.Windows.Forms.DateTimePicker> pour ajouter un contrôle à votre formulaire, puis <xref:System.Windows.Forms.Label> ajoutez un contrôle en double-cliquant sur **étiquette**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="aadb4-282">Utilisez la souris pour positionner les contrôles à un endroit approprié sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="aadb4-282">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="aadb4-283">Définissez les propriétés de ces contrôles de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="aadb4-283">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="aadb4-284">Contrôle</span><span class="sxs-lookup"><span data-stu-id="aadb4-284">Control</span></span>|<span data-ttu-id="aadb4-285">Propriété</span><span class="sxs-lookup"><span data-stu-id="aadb4-285">Property</span></span>|<span data-ttu-id="aadb4-286">Value</span><span class="sxs-lookup"><span data-stu-id="aadb4-286">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="aadb4-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="aadb4-287">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="aadb4-288">**Name**</span><span class="sxs-lookup"><span data-stu-id="aadb4-288">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="aadb4-289">**Name**</span><span class="sxs-lookup"><span data-stu-id="aadb4-289">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="aadb4-290">**Format**</span><span class="sxs-lookup"><span data-stu-id="aadb4-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="aadb4-291">Dans le concepteur, double-cliquez sur **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-291">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="aadb4-292">**L’éditeur de code** s’ouvre à la ligne `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-292">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="aadb4-293">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="aadb4-293">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="aadb4-294">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="aadb4-295">Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="aadb4-295">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="aadb4-296">Le programme de test démarre.</span><span class="sxs-lookup"><span data-stu-id="aadb4-296">The test program starts.</span></span> <span data-ttu-id="aadb4-297">Notez que l’heure actuelle est mise à jour `ctlAlarmClock` dans le contrôle et que l’heure de début est affichée <xref:System.Windows.Forms.DateTimePicker> dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="aadb4-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="aadb4-298">Cliquez sur <xref:System.Windows.Forms.DateTimePicker> l’emplacement où les minutes de l’heure sont affichées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="aadb4-299">À l’aide du clavier, définissez une valeur pour les minutes comportant une minute de plus que l’heure actuelle affichée par `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="aadb4-300">L’heure de déclenchement de l’alarme apparaît dans `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="aadb4-301">Attendez que l’heure affichée atteigne l’heure de déclenchement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="aadb4-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="aadb4-302">Lorsque l’heure affichée atteint l’heure sur laquelle l’alarme a été définie, `lblAlarm` se met à clignoter.</span><span class="sxs-lookup"><span data-stu-id="aadb4-302">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="aadb4-303">Désactivez l’alarme en cliquant sur `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="aadb4-303">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="aadb4-304">Vous pouvez maintenant réinitialiser l’alarme.</span><span class="sxs-lookup"><span data-stu-id="aadb4-304">You may now reset the alarm.</span></span>

     <span data-ttu-id="aadb4-305">Cette procédure pas à pas a abordé plusieurs concepts clés.</span><span class="sxs-lookup"><span data-stu-id="aadb4-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="aadb4-306">Vous avez appris à créer un contrôle composite en combinant des contrôles et des composants dans un conteneur de contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="aadb4-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="aadb4-307">Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code pour implémenter des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="aadb4-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="aadb4-308">Dans la dernière section, vous avez appris à étendre les fonctionnalités d’un contrôle composite grâce à l’héritage et à modifier les fonctionnalités des méthodes hôtes en remplaçant ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="aadb4-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="aadb4-309">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aadb4-309">See also</span></span>

- [<span data-ttu-id="aadb4-310">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="aadb4-310">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="aadb4-311">Guide pratique pour Afficher un contrôle dans la boîte de dialogue choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="aadb4-311">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="aadb4-312">Procédure pas à pas : Héritage à partir d’un contrôle Windows Forms avec VisualC#</span><span class="sxs-lookup"><span data-stu-id="aadb4-312">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
