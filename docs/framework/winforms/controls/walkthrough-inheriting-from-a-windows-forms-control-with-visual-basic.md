---
title: 'Procédure pas à pas : héritage d’un contrôle Windows Forms avec Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: bcd65f231ab0e05da0ec152b05878233558f2cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772064"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="4d830-102">Procédure pas à pas : héritage d’un contrôle Windows Forms avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d830-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="4d830-103">Avec Visual Basic, vous pouvez créer des contrôles personnalisés puissants via *héritage*.</span><span class="sxs-lookup"><span data-stu-id="4d830-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="4d830-104">L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4d830-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="4d830-105">Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="4d830-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="4d830-106">Ce bouton héritera des fonctionnalités des formulaires Windows standard <xref:System.Windows.Forms.Button> contrôler et exposera une propriété personnalisée nommée `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="4d830-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d830-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="4d830-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4d830-108">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="4d830-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4d830-109">Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4d830-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4d830-110">Création du projet</span><span class="sxs-lookup"><span data-stu-id="4d830-110">Creating the Project</span></span>  
 <span data-ttu-id="4d830-111">Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="4d830-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="4d830-112">Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton</span><span class="sxs-lookup"><span data-stu-id="4d830-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1. <span data-ttu-id="4d830-113">Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="4d830-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="4d830-114">Sélectionnez le **bibliothèque de contrôles Windows Forms** modèle de projet à partir de la liste des projets Visual Basic et le type `ValueButtonLib` dans le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="4d830-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="4d830-115">Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="4d830-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="4d830-116">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4d830-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="4d830-117">Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="4d830-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="4d830-118">Pour plus d’informations, consultez l’article [Espaces de noms dans Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4d830-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3. <span data-ttu-id="4d830-119">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.vb**, puis sélectionnez **Renommer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4d830-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="4d830-120">Remplacez le nom de fichier par `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="4d830-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="4d830-121">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».</span><span class="sxs-lookup"><span data-stu-id="4d830-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4. <span data-ttu-id="4d830-122">Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="4d830-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5. <span data-ttu-id="4d830-123">Ouvrez le nœud **ValueButton.vb** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="4d830-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="4d830-124">Ouvrez ce fichier dans **l’éditeur de code**.</span><span class="sxs-lookup"><span data-stu-id="4d830-124">Open this file in the **Code Editor**.</span></span>  
  
6. <span data-ttu-id="4d830-125">Recherchez le `Class` instruction, `Partial Public Class ValueButton`et modifier le type à partir duquel ce contrôle hérite de <xref:System.Windows.Forms.UserControl> à <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="4d830-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="4d830-126">Cela permet à votre contrôle hérité peut hériter de toutes les fonctionnalités de la <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d830-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7. <span data-ttu-id="4d830-127">Recherchez le `InitializeComponent` (méthode) et supprimez la ligne qui assigne la <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4d830-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="4d830-128">Cette propriété n’existe pas dans le <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d830-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8. <span data-ttu-id="4d830-129">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="4d830-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="4d830-130">Notez que plus aucun concepteur visuel n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="4d830-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="4d830-131">Étant donné que le <xref:System.Windows.Forms.Button> contrôle effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="4d830-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="4d830-132">Sa représentation visuelle sera exactement la même que celle de la classe, il hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si la modification du code.</span><span class="sxs-lookup"><span data-stu-id="4d830-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d830-133">Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d830-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="4d830-134">Ajout d’une propriété à votre contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="4d830-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="4d830-135">Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant la même apparence et le même comportement (aspect) que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4d830-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="4d830-136">Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d830-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
### <a name="to-add-the-value-property"></a><span data-ttu-id="4d830-137">Pour ajouter la propriété Valeur</span><span class="sxs-lookup"><span data-stu-id="4d830-137">To add the Value property</span></span>  
  
1. <span data-ttu-id="4d830-138">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.vb**, puis cliquez sur **Afficher le code** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4d830-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="4d830-139">Recherchez l’instruction `Public Class ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="4d830-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="4d830-140">Juste en dessous de cette instruction, saisissez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4d830-140">Immediately beneath this statement, type the following code:</span></span>  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     <span data-ttu-id="4d830-141">Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="4d830-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="4d830-142">L’instruction `Get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `Set` définit la valeur de la variable privée à l’aide du mot clé `Value`.</span><span class="sxs-lookup"><span data-stu-id="4d830-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3. <span data-ttu-id="4d830-143">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="4d830-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="4d830-144">Test de votre contrôle</span><span class="sxs-lookup"><span data-stu-id="4d830-144">Testing Your Control</span></span>  
 <span data-ttu-id="4d830-145">Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="4d830-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="4d830-146">Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="4d830-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="4d830-147">Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant).</span><span class="sxs-lookup"><span data-stu-id="4d830-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="4d830-148">Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.</span><span class="sxs-lookup"><span data-stu-id="4d830-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
### <a name="to-build-your-control"></a><span data-ttu-id="4d830-149">Pour générer votre contrôle</span><span class="sxs-lookup"><span data-stu-id="4d830-149">To build your control</span></span>  
  
1. <span data-ttu-id="4d830-150">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="4d830-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="4d830-151">L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="4d830-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
### <a name="to-create-a-test-project"></a><span data-ttu-id="4d830-152">Pour créer un projet de test</span><span class="sxs-lookup"><span data-stu-id="4d830-152">To create a test project</span></span>  
  
1. <span data-ttu-id="4d830-153">Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="4d830-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="4d830-154">Sélectionnez le nœud de projets Visual Basic, puis cliquez sur **Windows Forms Application**.</span><span class="sxs-lookup"><span data-stu-id="4d830-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="4d830-155">Dans la zone **Nom** , tapez `Test`.</span><span class="sxs-lookup"><span data-stu-id="4d830-155">In the **Name** box, type `Test`.</span></span>  
  
4. <span data-ttu-id="4d830-156">Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="4d830-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5. <span data-ttu-id="4d830-157">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="4d830-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6. <span data-ttu-id="4d830-158">Cliquez sur l’onglet **Projets**.</span><span class="sxs-lookup"><span data-stu-id="4d830-158">Click the **Projects** tab.</span></span>  
  
7. <span data-ttu-id="4d830-159">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="4d830-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="4d830-160">Votre projet `ValueButtonLib` s’affiche sous **Nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="4d830-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="4d830-161">Double-cliquez sur le projet pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="4d830-161">Double-click the project to add the reference to the test project.</span></span>  
  
8. <span data-ttu-id="4d830-162">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.</span><span class="sxs-lookup"><span data-stu-id="4d830-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="4d830-163">Pour ajouter votre contrôle au formulaire</span><span class="sxs-lookup"><span data-stu-id="4d830-163">To add your control to the form</span></span>  
  
1. <span data-ttu-id="4d830-164">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.vb** et sélectionnez **Concepteur de vues** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4d830-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="4d830-165">Dans la **boîte à outils**, cliquez sur **Composants ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="4d830-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="4d830-166">Double-cliquez sur **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="4d830-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="4d830-167">Un élément **ValueButton** apparaît sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4d830-167">A **ValueButton** appears on the form.</span></span>  
  
3. <span data-ttu-id="4d830-168">Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4d830-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4. <span data-ttu-id="4d830-169">Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d830-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="4d830-170">Notez qu’elles sont identiques aux propriétés exposées par un bouton standard, à la différence près qu’il y a une propriété en plus, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="4d830-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5. <span data-ttu-id="4d830-171">Affectez à la propriété `ButtonValue` la valeur `5`.</span><span class="sxs-lookup"><span data-stu-id="4d830-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6. <span data-ttu-id="4d830-172">Sur le **tous les Windows Forms** onglet de la **boîte à outils**, double-cliquez sur **étiquette** pour ajouter un <xref:System.Windows.Forms.Label> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="4d830-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7. <span data-ttu-id="4d830-173">Déplacez l’étiquette au centre du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4d830-173">Relocate the label to the center of the form.</span></span>  
  
8. <span data-ttu-id="4d830-174">Double-cliquez sur `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="4d830-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="4d830-175">**L’éditeur de code** s’ouvre à l’événement `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="4d830-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="4d830-176">Saisissez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="4d830-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="4d830-177">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4d830-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="4d830-178">Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="4d830-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="4d830-179">`Form1` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4d830-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="4d830-180">Cliquez sur `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="4d830-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="4d830-181">Le chiffre « 5 » s’affiche dans `Label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `Label1` via la méthode `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="4d830-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="4d830-182">Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="4d830-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d830-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d830-183">See also</span></span>

- [<span data-ttu-id="4d830-184">Procédure pas à pas : Création d’un contrôle Composite avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d830-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="4d830-185">Guide pratique pour Afficher un contrôle dans la boîte de dialogue de boîte à outils éléments choisir</span><span class="sxs-lookup"><span data-stu-id="4d830-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="4d830-186">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d830-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="4d830-187">Éléments fondamentaux de l’héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d830-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
