---
title: Héberger un contrôle composite Windows Forms dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 16c09b4bb393fa830412385b4b405dd1fae9878b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744996"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="7564f-102">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="7564f-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="7564f-103">propose un environnement de création d'applications élaboré.</span><span class="sxs-lookup"><span data-stu-id="7564f-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="7564f-104">Toutefois, lorsque vous investissez dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plutôt que de la réécrire à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="7564f-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="7564f-105">Le scénario le plus courant est lorsque vous avez des contrôles de Windows Forms existants.</span><span class="sxs-lookup"><span data-stu-id="7564f-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="7564f-106">Dans certains cas, il est possible que vous n’ayez même pas accès au code source de ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="7564f-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="7564f-107">fournit une procédure simple pour l’hébergement de ces contrôles dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7564f-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="7564f-108">Par exemple, vous pouvez utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la majeure partie de votre programmation tout en hébergeant vos contrôles de <xref:System.Windows.Forms.DataGridView> spécialisés.</span><span class="sxs-lookup"><span data-stu-id="7564f-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="7564f-109">Cette procédure pas à pas vous guide à travers une application qui héberge un Windows Forms contrôle composite pour effectuer une entrée de données dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7564f-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="7564f-110">Le contrôle composite est empaqueté dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="7564f-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="7564f-111">Cette procédure générale peut être étendue à des applications et des contrôles plus complexes.</span><span class="sxs-lookup"><span data-stu-id="7564f-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="7564f-112">Cette procédure pas à pas est conçue pour être quasiment identique dans l’apparence et les fonctionnalités de la [procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7564f-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="7564f-113">La principale différence est que le scénario d’hébergement est inversé.</span><span class="sxs-lookup"><span data-stu-id="7564f-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="7564f-114">La procédure pas à pas est divisée en deux sections.</span><span class="sxs-lookup"><span data-stu-id="7564f-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="7564f-115">La première section décrit brièvement l’implémentation du contrôle composite Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7564f-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="7564f-116">La deuxième section explique en détail comment héberger le contrôle composite dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="7564f-117">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="7564f-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="7564f-118">Implémentation du contrôle composite Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7564f-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="7564f-119">Implémentation de l’application hôte WPF</span><span class="sxs-lookup"><span data-stu-id="7564f-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="7564f-120">Pour obtenir la liste du code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle composite Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="7564f-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7564f-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7564f-121">Prerequisites</span></span>  

<span data-ttu-id="7564f-122">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7564f-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="7564f-123">Implémentation du contrôle composite Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7564f-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="7564f-124">Le contrôle composite Windows Forms utilisé dans cet exemple est un formulaire de saisie de données simple.</span><span class="sxs-lookup"><span data-stu-id="7564f-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="7564f-125">Ce formulaire prend le nom et l’adresse de l’utilisateur, puis utilise un événement personnalisé pour retourner ces informations à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7564f-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="7564f-126">L’illustration suivante montre le rendu du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="7564f-127">L’illustration suivante montre un contrôle composite Windows Forms :</span><span class="sxs-lookup"><span data-stu-id="7564f-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Capture d’écran montrant un contrôle de Windows Forms simple.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="7564f-129">Création du projet</span><span class="sxs-lookup"><span data-stu-id="7564f-129">Creating the Project</span></span>  
 <span data-ttu-id="7564f-130">Pour démarrer le projet :</span><span class="sxs-lookup"><span data-stu-id="7564f-130">To start the project:</span></span>  
  
1. <span data-ttu-id="7564f-131">Lancez Visual Studio, puis ouvrez la boîte de dialogue **nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="7564f-131">Launch Visual Studio, and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="7564f-132">Dans la catégorie fenêtre, sélectionnez le modèle **bibliothèque de contrôles Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="7564f-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="7564f-133">Nommez le nouveau projet `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="7564f-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="7564f-134">Pour l’emplacement, spécifiez un dossier de niveau supérieur, tel que `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="7564f-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="7564f-135">Plus tard, vous placerez l’application hôte dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="7564f-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="7564f-136">Cliquez sur **OK** pour créer le projet.</span><span class="sxs-lookup"><span data-stu-id="7564f-136">Click **OK** to create the project.</span></span> <span data-ttu-id="7564f-137">Le projet par défaut contient un seul contrôle nommé `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="7564f-138">Dans Explorateur de solutions, renommez `UserControl1` en `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="7564f-139">Votre projet doit comporter des références aux DLL système suivantes.</span><span class="sxs-lookup"><span data-stu-id="7564f-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="7564f-140">Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7564f-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="7564f-141">System</span><span class="sxs-lookup"><span data-stu-id="7564f-141">System</span></span>  
  
- <span data-ttu-id="7564f-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="7564f-142">System.Data</span></span>  
  
- <span data-ttu-id="7564f-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="7564f-143">System.Drawing</span></span>  
  
- <span data-ttu-id="7564f-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="7564f-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="7564f-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="7564f-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="7564f-146">Ajout de contrôles au formulaire</span><span class="sxs-lookup"><span data-stu-id="7564f-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="7564f-147">Pour ajouter des contrôles au formulaire :</span><span class="sxs-lookup"><span data-stu-id="7564f-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="7564f-148">Ouvrez `MyControl1` dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="7564f-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="7564f-149">Ajoutez cinq contrôles <xref:System.Windows.Forms.Label> et leurs contrôles <xref:System.Windows.Forms.TextBox> correspondants, dimensionnés et disposés comme dans l’illustration précédente, sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="7564f-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="7564f-150">Dans l’exemple, les contrôles <xref:System.Windows.Forms.TextBox> sont nommés :</span><span class="sxs-lookup"><span data-stu-id="7564f-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="7564f-151">Ajoutez deux contrôles <xref:System.Windows.Forms.Button> étiquetés **OK** et **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="7564f-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="7564f-152">Dans l’exemple, les noms de bouton sont `btnOK` et `btnCancel`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7564f-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="7564f-153">Implémentation du code de prise en charge</span><span class="sxs-lookup"><span data-stu-id="7564f-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="7564f-154">Ouvrez le formulaire en mode Code.</span><span class="sxs-lookup"><span data-stu-id="7564f-154">Open the form in code view.</span></span> <span data-ttu-id="7564f-155">Le contrôle retourne les données collectées à son hôte en déclenchant l’événement `OnButtonClick` personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7564f-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="7564f-156">Les données sont contenues dans l’objet d’argument d’événement.</span><span class="sxs-lookup"><span data-stu-id="7564f-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="7564f-157">Le code suivant illustre les déclarations event et delegate.</span><span class="sxs-lookup"><span data-stu-id="7564f-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="7564f-158">Ajoutez le code suivant à la classe `MyControl1` .</span><span class="sxs-lookup"><span data-stu-id="7564f-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="7564f-159">La classe `MyControlEventArgs` contient les informations à retourner à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7564f-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="7564f-160">Ajoutez la classe suivante au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7564f-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="7564f-161">Quand l’utilisateur clique sur le bouton **OK** ou **Annuler** , les gestionnaires d’événements <xref:System.Windows.Forms.Control.Click> créent un objet `MyControlEventArgs` qui contient les données et déclenche l’événement `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="7564f-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="7564f-162">La seule différence entre les deux gestionnaires est la propriété `IsOK` de l’argument d’événement.</span><span class="sxs-lookup"><span data-stu-id="7564f-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="7564f-163">Cette propriété permet à l’hôte de déterminer sur quel bouton l’utilisateur a cliqué.</span><span class="sxs-lookup"><span data-stu-id="7564f-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="7564f-164">Elle est définie sur `true` pour le bouton **OK** , et `false` pour le bouton **Annuler** .</span><span class="sxs-lookup"><span data-stu-id="7564f-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="7564f-165">Le code suivant montre les deux gestionnaires de boutons.</span><span class="sxs-lookup"><span data-stu-id="7564f-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="7564f-166">Ajoutez le code suivant à la classe `MyControl1` .</span><span class="sxs-lookup"><span data-stu-id="7564f-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="7564f-167">Attribution d’un nom fort à l’assembly et création de l’assembly</span><span class="sxs-lookup"><span data-stu-id="7564f-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="7564f-168">Pour que cet assembly soit référencé par une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il doit avoir un nom fort.</span><span class="sxs-lookup"><span data-stu-id="7564f-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="7564f-169">Pour créer un nom fort, créez un fichier de clé avec SN. exe et ajoutez-le à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7564f-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="7564f-170">Ouvrez une invite de commandes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7564f-170">Open a Visual Studio command prompt.</span></span> <span data-ttu-id="7564f-171">Pour ce faire, cliquez sur le menu **Démarrer** , puis sélectionnez **tous les programmes/Microsoft Visual Studio 2010/Visual Studio Tools/invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7564f-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="7564f-172">Une fenêtre de console s’affiche alors avec des variables d’environnement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7564f-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="7564f-173">À l’invite de commandes, utilisez la commande `cd` pour accéder au dossier de votre projet.</span><span class="sxs-lookup"><span data-stu-id="7564f-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="7564f-174">Générez un fichier de clé nommé MyControls.snk en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7564f-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="7564f-175">Pour inclure le fichier de clé dans votre projet, cliquez avec le bouton droit sur le nom du projet dans Explorateur de solutions puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7564f-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="7564f-176">Dans le concepteur de projet, cliquez sur l’onglet **signature** , activez la case à cocher **signer l’assembly** , puis accédez à votre fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="7564f-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="7564f-177">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="7564f-177">Build the solution.</span></span> <span data-ttu-id="7564f-178">La génération produira une DLL nommée MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="7564f-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="7564f-179">Implémentation de l’application hôte WPF</span><span class="sxs-lookup"><span data-stu-id="7564f-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="7564f-180">L’application hôte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour héberger des `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="7564f-181">L’application gère l’événement `OnButtonClick` pour recevoir les données du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="7564f-182">Elle contient également une collection de cases d’option qui vous permettent de modifier certaines des propriétés du contrôle à partir de l’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7564f-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="7564f-183">L’illustration suivante montre l’application finale.</span><span class="sxs-lookup"><span data-stu-id="7564f-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="7564f-184">L’illustration suivante montre l’application complète, y compris le contrôle incorporé dans l’application WPF :</span><span class="sxs-lookup"><span data-stu-id="7564f-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Capture d’écran montrant un contrôle incorporé dans une page WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="7564f-186">Création du projet</span><span class="sxs-lookup"><span data-stu-id="7564f-186">Creating the Project</span></span>
 <span data-ttu-id="7564f-187">Pour démarrer le projet :</span><span class="sxs-lookup"><span data-stu-id="7564f-187">To start the project:</span></span>

1. <span data-ttu-id="7564f-188">Ouvrez Visual Studio, puis sélectionnez **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="7564f-188">Open Visual Studio, and select **New Project**.</span></span>

2. <span data-ttu-id="7564f-189">Dans la catégorie fenêtre, sélectionnez le modèle **application WPF** .</span><span class="sxs-lookup"><span data-stu-id="7564f-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="7564f-190">Nommez le nouveau projet `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="7564f-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="7564f-191">Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.</span><span class="sxs-lookup"><span data-stu-id="7564f-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="7564f-192">Cliquez sur **OK** pour créer le projet.</span><span class="sxs-lookup"><span data-stu-id="7564f-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="7564f-193">Vous devez également ajouter des références à la DLL qui contient `MyControl1` et d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="7564f-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="7564f-194">Dans Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7564f-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="7564f-195">Cliquez sur l’onglet **Parcourir** et accédez au dossier qui contient MyControls. dll.</span><span class="sxs-lookup"><span data-stu-id="7564f-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="7564f-196">Pour cette procédure pas à pas, il s’agit du dossier MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="7564f-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="7564f-197">Sélectionnez MyControls. dll, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7564f-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="7564f-198">Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="7564f-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="7564f-199">Implémentation de la disposition de base</span><span class="sxs-lookup"><span data-stu-id="7564f-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="7564f-200">L' [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application hôte est implémentée dans MainWindow. Xaml.</span><span class="sxs-lookup"><span data-stu-id="7564f-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="7564f-201">Ce fichier contient [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage qui définit la disposition et héberge le contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7564f-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="7564f-202">L’application est divisée en trois sections :</span><span class="sxs-lookup"><span data-stu-id="7564f-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="7564f-203">Le panneau **Propriétés du contrôle** , qui contient une collection de cases d’option que vous pouvez utiliser pour modifier diverses propriétés du contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="7564f-204">Les **données du panneau de** configuration, qui contiennent plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="7564f-205">Le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-205">The hosted control itself.</span></span>

 <span data-ttu-id="7564f-206">La disposition de base est indiquée dans le XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="7564f-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="7564f-207">Le balisage nécessaire pour héberger `MyControl1` est omis dans cet exemple, mais il sera abordé plus tard.</span><span class="sxs-lookup"><span data-stu-id="7564f-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="7564f-208">Remplacez le code XAML de MainWindow.xaml par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7564f-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="7564f-209">Si vous utilisez Visual Basic, remplacez la classe par `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="7564f-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="7564f-210">Le premier élément <xref:System.Windows.Controls.StackPanel> contient plusieurs ensembles de contrôles <xref:System.Windows.Controls.RadioButton> qui vous permettent de modifier différentes propriétés par défaut du contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="7564f-211">Qui est suivi d’un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, qui héberge `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="7564f-212">L’élément <xref:System.Windows.Controls.StackPanel> final contient plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="7564f-213">L’ordre des éléments et les paramètres d’attribut <xref:System.Windows.Controls.DockPanel.Dock%2A> et <xref:System.Windows.FrameworkElement.Height%2A> incorporent le contrôle hébergé dans la fenêtre sans espace ni distorsion.</span><span class="sxs-lookup"><span data-stu-id="7564f-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="7564f-214">Hébergement du contrôle</span><span class="sxs-lookup"><span data-stu-id="7564f-214">Hosting the Control</span></span>
 <span data-ttu-id="7564f-215">La version modifiée suivante du XAML précédent se concentre sur les éléments qui sont nécessaires pour héberger des `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="7564f-216">L’attribut de mappage de l’espace de noms `xmlns` crée une référence à l’espace de noms `MyControls` qui contient le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="7564f-217">Ce mappage vous permet de représenter `MyControl1` dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] comme `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="7564f-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="7564f-218">Dans le code XAML, deux éléments gèrent l’hébergement :</span><span class="sxs-lookup"><span data-stu-id="7564f-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="7564f-219">`WindowsFormsHost` représente l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> qui vous permet d’héberger un contrôle Windows Forms dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7564f-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="7564f-220">`mcl:MyControl1`, qui représente `MyControl1`, est ajouté à la collection enfant de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="7564f-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="7564f-221">Par conséquent, ce Windows Forms contrôle est restitué dans le cadre de la fenêtre de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et vous pouvez communiquer avec le contrôle à partir de l’application.</span><span class="sxs-lookup"><span data-stu-id="7564f-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="7564f-222">Implémentation du fichier code-behind</span><span class="sxs-lookup"><span data-stu-id="7564f-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="7564f-223">Le fichier code-behind, MainWindow. Xaml. vb ou MainWindow.xaml.cs, contient le code procédural qui implémente les fonctionnalités du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] abordé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="7564f-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="7564f-224">Les tâches principales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7564f-224">The primary tasks are:</span></span>

- <span data-ttu-id="7564f-225">Attachement d’un gestionnaire d’événements à l’événement `OnButtonClick` de `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="7564f-226">Modification de diverses propriétés de `MyControl1`, en fonction de la façon dont la collection de cases d’option est définie.</span><span class="sxs-lookup"><span data-stu-id="7564f-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="7564f-227">Affichage des données collectées par le contrôle</span><span class="sxs-lookup"><span data-stu-id="7564f-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="7564f-228">Initialisation de l’application</span><span class="sxs-lookup"><span data-stu-id="7564f-228">Initializing the Application</span></span>
 <span data-ttu-id="7564f-229">Le code d’initialisation est contenu dans un gestionnaire d’événements pour l’événement <xref:System.Windows.FrameworkElement.Loaded> de la fenêtre et attache un gestionnaire d’événements à l’événement `OnButtonClick` du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="7564f-230">Dans MainWindow. Xaml. vb ou MainWindow.xaml.cs, ajoutez le code suivant à la classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="7564f-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="7564f-231">Étant donné que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] abordé précédemment a ajouté des `MyControl1` à la collection d’éléments enfants de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, vous pouvez effectuer un cast de la <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour récupérer la référence à `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="7564f-232">Vous pouvez ensuite utiliser cette référence pour attacher un gestionnaire d’événements à `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="7564f-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="7564f-233">En plus de fournir une référence au contrôle lui-même, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose un certain nombre de propriétés du contrôle, que vous pouvez manipuler à partir de l’application.</span><span class="sxs-lookup"><span data-stu-id="7564f-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="7564f-234">Le code d’initialisation affecte ces valeurs aux variables globales privées pour une utilisation ultérieure dans l’application.</span><span class="sxs-lookup"><span data-stu-id="7564f-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="7564f-235">Pour que vous puissiez accéder facilement aux types dans la DLL `MyControls`, ajoutez l’instruction `Imports` ou `using` suivante au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="7564f-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="7564f-236">Gestion de l’événement OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="7564f-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="7564f-237">`MyControl1` déclenche l’événement `OnButtonClick` lorsque l’utilisateur clique sur l’un des boutons du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="7564f-238">Ajoutez le code suivant à la classe `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="7564f-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="7564f-239">Les données dans les zones de texte sont empaquetées dans l’objet `MyControlEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="7564f-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="7564f-240">Si l’utilisateur clique sur le bouton **OK** , le gestionnaire d’événements extrait les données et les affiche dans le panneau ci-dessous `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="7564f-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="7564f-241">Modification des propriétés du contrôle</span><span class="sxs-lookup"><span data-stu-id="7564f-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="7564f-242">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose plusieurs propriétés par défaut du contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="7564f-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="7564f-243">Par conséquent, vous pouvez changer l’apparence du contrôle pour qu’elle corresponde davantage au style de votre application.</span><span class="sxs-lookup"><span data-stu-id="7564f-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="7564f-244">Les ensembles de cases d’option du panneau gauche permettent à l’utilisateur de modifier plusieurs propriétés de couleur et de police.</span><span class="sxs-lookup"><span data-stu-id="7564f-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="7564f-245">Chaque ensemble de boutons a un gestionnaire pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, qui détecte les sélections de cases d’option de l’utilisateur et modifie la propriété correspondante sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="7564f-246">Ajoutez le code suivant à la classe `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="7564f-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="7564f-247">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="7564f-247">Build and run the application.</span></span> <span data-ttu-id="7564f-248">Ajoutez du texte dans le contrôle composite Windows Forms, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7564f-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="7564f-249">Le texte s’affiche dans les étiquettes.</span><span class="sxs-lookup"><span data-stu-id="7564f-249">The text appears in the labels.</span></span> <span data-ttu-id="7564f-250">Cliquez sur les différentes cases d’option pour voir l’effet du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7564f-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7564f-251">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7564f-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7564f-252">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7564f-252">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="7564f-253">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="7564f-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="7564f-254">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7564f-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
