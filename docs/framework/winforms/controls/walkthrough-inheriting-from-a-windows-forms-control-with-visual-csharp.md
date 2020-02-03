---
title: Hériter d’un contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 713ccf97a73ce9684b9124a121369f22751861d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740141"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a><span data-ttu-id="7441d-102">Procédure pas à pas : hériter d’un contrôle Windows Forms avec C\#</span><span class="sxs-lookup"><span data-stu-id="7441d-102">Walkthrough: Inherit from a Windows Forms Control with C\#</span></span>

<span data-ttu-id="7441d-103">Avec C#, vous pouvez créer des contrôles personnalisés puissants par le biais de *l’héritage*.</span><span class="sxs-lookup"><span data-stu-id="7441d-103">With C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="7441d-104">L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7441d-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="7441d-105">Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7441d-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="7441d-106">Ce bouton hérite des fonctionnalités du contrôle de <xref:System.Windows.Forms.Button> Windows Forms standard et expose une propriété personnalisée appelée `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7441d-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7441d-107">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="7441d-107">Create the Project</span></span>

<span data-ttu-id="7441d-108">Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="7441d-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="7441d-109">Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton</span><span class="sxs-lookup"><span data-stu-id="7441d-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="7441d-110">Dans Visual Studio, créez un projet de **bibliothèque de contrôles Windows Forms** , puis nommez-le **ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="7441d-110">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ValueButtonLib**.</span></span>

     <span data-ttu-id="7441d-111">Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="7441d-111">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="7441d-112">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7441d-112">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="7441d-113">Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7441d-113">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="7441d-114">Pour plus d’informations, consultez l’article [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="7441d-114">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

2. <span data-ttu-id="7441d-115">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.cs**, puis sélectionnez **Renommer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7441d-115">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="7441d-116">Remplacez le nom de fichier par **ValueButton.cs**.</span><span class="sxs-lookup"><span data-stu-id="7441d-116">Change the file name to **ValueButton.cs**.</span></span> <span data-ttu-id="7441d-117">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « `UserControl1` ».</span><span class="sxs-lookup"><span data-stu-id="7441d-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

3. <span data-ttu-id="7441d-118">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis sélectionnez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="7441d-118">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

4. <span data-ttu-id="7441d-119">Localisez la ligne d’instruction `class`, `public partial class ValueButton`et remplacez le type dont hérite ce contrôle <xref:System.Windows.Forms.UserControl> par <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="7441d-119">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="7441d-120">Cela permet à votre contrôle hérité d’hériter de toutes les fonctionnalités du contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="7441d-120">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

5. <span data-ttu-id="7441d-121">Dans **l’Explorateur de solutions**, ouvrez le nœud **ValueButton.cs** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="7441d-121">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="7441d-122">Ouvrez ce fichier dans **l’éditeur de code**.</span><span class="sxs-lookup"><span data-stu-id="7441d-122">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="7441d-123">Recherchez la méthode `InitializeComponent` et supprimez la ligne qui affecte la propriété <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="7441d-123">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="7441d-124">Cette propriété n’existe pas dans le contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="7441d-124">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="7441d-125">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="7441d-125">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7441d-126">Plus aucun concepteur visuel n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="7441d-126">A visual designer is no longer available.</span></span> <span data-ttu-id="7441d-127">Étant donné que le contrôle <xref:System.Windows.Forms.Button> effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="7441d-127">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="7441d-128">Sa représentation visuelle sera exactement la même que celle de la classe dont elle hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si elle est modifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="7441d-128">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="7441d-129">Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7441d-129">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="add-a-property-to-your-inherited-control"></a><span data-ttu-id="7441d-130">Ajouter une propriété à votre contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="7441d-130">Add a Property to Your Inherited Control</span></span>

<span data-ttu-id="7441d-131">Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant le même aspect que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7441d-131">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="7441d-132">Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="7441d-132">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="7441d-133">Pour ajouter la propriété Valeur</span><span class="sxs-lookup"><span data-stu-id="7441d-133">To add the Value property</span></span>

1. <span data-ttu-id="7441d-134">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7441d-134">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="7441d-135">Recherchez l’instruction `class`.</span><span class="sxs-lookup"><span data-stu-id="7441d-135">Locate the `class` statement.</span></span> <span data-ttu-id="7441d-136">Saisissez le code suivant immédiatement après `{` :</span><span class="sxs-lookup"><span data-stu-id="7441d-136">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="7441d-137">Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7441d-137">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="7441d-138">L’instruction `get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `set` définit la valeur de la variable privée à l’aide du mot clé `value`.</span><span class="sxs-lookup"><span data-stu-id="7441d-138">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="7441d-139">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="7441d-139">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="7441d-140">Tester le contrôle</span><span class="sxs-lookup"><span data-stu-id="7441d-140">Test the control</span></span>

<span data-ttu-id="7441d-141">Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="7441d-141">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="7441d-142">Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="7441d-142">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="7441d-143">Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant).</span><span class="sxs-lookup"><span data-stu-id="7441d-143">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="7441d-144">Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.</span><span class="sxs-lookup"><span data-stu-id="7441d-144">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="7441d-145">Pour générer votre contrôle</span><span class="sxs-lookup"><span data-stu-id="7441d-145">To build your control</span></span>

<span data-ttu-id="7441d-146">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="7441d-146">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="7441d-147">L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="7441d-147">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="7441d-148">Pour créer un projet de test</span><span class="sxs-lookup"><span data-stu-id="7441d-148">To create a test project</span></span>

1. <span data-ttu-id="7441d-149">Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="7441d-149">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="7441d-150">Sélectionnez le nœud **Windows** sous le nœud **Visual C#** , puis cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="7441d-150">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="7441d-151">Dans la zone **nom** , entrez **test**.</span><span class="sxs-lookup"><span data-stu-id="7441d-151">In the **Name** box, enter **Test**.</span></span>

4. <span data-ttu-id="7441d-152">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7441d-152">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="7441d-153">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="7441d-153">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="7441d-154">Votre projet ValueButtonLib sera listé sous **nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="7441d-154">Your ValueButtonLib project will be listed under **Project Name**.</span></span> <span data-ttu-id="7441d-155">Double-cliquez sur le projet pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="7441d-155">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="7441d-156">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.</span><span class="sxs-lookup"><span data-stu-id="7441d-156">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="7441d-157">Pour ajouter votre contrôle au formulaire</span><span class="sxs-lookup"><span data-stu-id="7441d-157">To add your control to the form</span></span>

1. <span data-ttu-id="7441d-158">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs** et sélectionnez **Concepteur de vues** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7441d-158">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="7441d-159">Dans la **boîte à outils**, sélectionnez **composants ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="7441d-159">In the **Toolbox**, select **ValueButtonLib Components**.</span></span> <span data-ttu-id="7441d-160">Double-cliquez sur **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="7441d-160">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="7441d-161">Un élément **ValueButton** apparaît sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="7441d-161">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="7441d-162">Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7441d-162">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="7441d-163">Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="7441d-163">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="7441d-164">Notez qu’ils sont identiques aux propriétés exposées par un bouton standard, à ceci près qu’il existe une propriété supplémentaire, ButtonValue.</span><span class="sxs-lookup"><span data-stu-id="7441d-164">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, ButtonValue.</span></span>

5. <span data-ttu-id="7441d-165">Affectez à la propriété **ButtonValue** la valeur **5**.</span><span class="sxs-lookup"><span data-stu-id="7441d-165">Set the **ButtonValue** property to **5**.</span></span>

6. <span data-ttu-id="7441d-166">Dans l’onglet **tous les Windows Forms** de la **boîte à outils**, double-cliquez sur **étiquette** pour ajouter un contrôle de <xref:System.Windows.Forms.Label> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7441d-166">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="7441d-167">Déplacez l’étiquette au centre du formulaire.</span><span class="sxs-lookup"><span data-stu-id="7441d-167">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="7441d-168">Double-cliquez sur `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7441d-168">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="7441d-169">**L’éditeur de code** s’ouvre à l’événement `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="7441d-169">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="7441d-170">Saisissez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="7441d-170">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="7441d-171">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7441d-171">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="7441d-172">Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="7441d-172">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="7441d-173">`Form1` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7441d-173">`Form1` appears.</span></span>

12. <span data-ttu-id="7441d-174">Cliquez sur `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7441d-174">Click `valueButton1`.</span></span>

     <span data-ttu-id="7441d-175">Le chiffre « 5 » s’affiche dans `label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `label1` via la méthode `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="7441d-175">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="7441d-176">Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="7441d-176">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="7441d-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7441d-177">See also</span></span>

- [<span data-ttu-id="7441d-178">Guide pratique pour afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="7441d-178">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="7441d-179">Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="7441d-179">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
