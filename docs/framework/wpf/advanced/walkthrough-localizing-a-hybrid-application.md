---
title: "Procédure pas à pas : localisation d'une application hybride"
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b406d539f2446824027e9462c8ecbe20c18cfb27
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794127"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="6c842-102">Procédure pas à pas : localisation d'une application hybride</span><span class="sxs-lookup"><span data-stu-id="6c842-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="6c842-103">Cette procédure pas à pas vous montre comment localiser des éléments de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une application hybride basée sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c842-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="6c842-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c842-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="6c842-105">Création du projet Windows Forms Host.</span><span class="sxs-lookup"><span data-stu-id="6c842-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="6c842-106">Ajout de contenu localisable</span><span class="sxs-lookup"><span data-stu-id="6c842-106">Adding localizable content.</span></span>

- <span data-ttu-id="6c842-107">Activation de la localisation</span><span class="sxs-lookup"><span data-stu-id="6c842-107">Enabling localization.</span></span>

- <span data-ttu-id="6c842-108">Assignation d’identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="6c842-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="6c842-109">Utilisation de l’outil LocBaml pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="6c842-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="6c842-110">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [localisation d’un exemple d’application hybride](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="6c842-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="6c842-111">Quand vous aurez terminé, vous disposerez d’une application hybride localisée.</span><span class="sxs-lookup"><span data-stu-id="6c842-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c842-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6c842-112">Prerequisites</span></span>

<span data-ttu-id="6c842-113">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="6c842-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="6c842-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6c842-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="6c842-115">Création du projet hôte Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c842-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="6c842-116">La première étape consiste à créer le Windows Forms projet d’application et à ajouter un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec le contenu que vous allez localiser.</span><span class="sxs-lookup"><span data-stu-id="6c842-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="6c842-117">Pour créer le projet hôte</span><span class="sxs-lookup"><span data-stu-id="6c842-117">To create the host project</span></span>

1. <span data-ttu-id="6c842-118">Créez un projet d' **application WPF** nommé `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="6c842-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="6c842-119">(**Fichier** > **nouveau** **projet** >  > **Visual C#**  ou **Visual Basic** > **application WPF**de **Bureau classique** > ).</span><span class="sxs-lookup"><span data-stu-id="6c842-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="6c842-120">Ajoutez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]élément <xref:System.Windows.Controls.UserControl> appelé `SimpleControl` au projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="6c842-121">Utilisez le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour placer un élément `SimpleControl` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="6c842-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="6c842-122">Pour plus d’informations, consultez [procédure pas à pas : Hébergement d’un contrôle composite 3D WPF dans Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6c842-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="6c842-123">Ajout de contenu localisable</span><span class="sxs-lookup"><span data-stu-id="6c842-123">Adding Localizable Content</span></span>

<span data-ttu-id="6c842-124">Ensuite, vous allez ajouter un contrôle d’étiquette Windows Forms et définir le contenu de l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur une chaîne localisable.</span><span class="sxs-lookup"><span data-stu-id="6c842-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="6c842-125">Pour ajouter du contenu localisable</span><span class="sxs-lookup"><span data-stu-id="6c842-125">To add localizable content</span></span>

1. <span data-ttu-id="6c842-126">Dans **Explorateur de solutions**, double-cliquez sur **SimpleControl. Xaml** pour l’ouvrir dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="6c842-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="6c842-127">Définissez le contenu du contrôle <xref:System.Windows.Controls.Button> à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="6c842-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="6c842-128">Dans **Explorateur de solutions**, double-cliquez sur **Form1** pour l’ouvrir dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c842-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="6c842-129">Ouvrez la **boîte à outils** et double-cliquez sur **étiquette** pour ajouter un contrôle Label au formulaire.</span><span class="sxs-lookup"><span data-stu-id="6c842-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="6c842-130">Affectez à sa propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="6c842-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="6c842-131">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="6c842-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="6c842-132">L’élément `SimpleControl` et le contrôle Label affichent le texte **« Hello »** .</span><span class="sxs-lookup"><span data-stu-id="6c842-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="6c842-133">Activation de la localisation</span><span class="sxs-lookup"><span data-stu-id="6c842-133">Enabling Localization</span></span>

<span data-ttu-id="6c842-134">Le Concepteur Windows Forms comprend des paramètres permettant d’activer la localisation dans un assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="6c842-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="6c842-135">Pour activer la localisation</span><span class="sxs-lookup"><span data-stu-id="6c842-135">To enable localization</span></span>

1. <span data-ttu-id="6c842-136">Dans **Explorateur de solutions**, double-cliquez sur **Form1.cs** pour l’ouvrir dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c842-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="6c842-137">Dans la fenêtre **Propriétés** , définissez la valeur de la propriété **localisable** du formulaire sur `true`.</span><span class="sxs-lookup"><span data-stu-id="6c842-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="6c842-138">Dans la fenêtre **Propriétés** , définissez la valeur de la propriété **Language** sur **espagnol (Espagne)** .</span><span class="sxs-lookup"><span data-stu-id="6c842-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="6c842-139">Dans le Concepteur Windows Forms, sélectionnez le contrôle d’étiquette.</span><span class="sxs-lookup"><span data-stu-id="6c842-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="6c842-140">Dans la fenêtre **Propriétés** , définissez la valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A> sur `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="6c842-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="6c842-141">Un nouveau fichier de ressources nommé Form1.es-ES.resx est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="6c842-142">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs** , puis cliquez sur **afficher le code** pour l’ouvrir dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="6c842-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="6c842-143">Copiez le code suivant dans le constructeur `Form1`, avant l’appel à `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="6c842-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="6c842-144">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **LocalizingWpfInWf** , puis cliquez sur **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="6c842-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="6c842-145">Le nom du projet est étiqueté **(non disponible)** .</span><span class="sxs-lookup"><span data-stu-id="6c842-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="6c842-146">Cliquez avec le bouton droit sur **LocalizingWpfInWf**, puis cliquez sur **modifier LocalizingWpfInWf. csproj**.</span><span class="sxs-lookup"><span data-stu-id="6c842-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="6c842-147">Le fichier projet s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="6c842-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="6c842-148">Copiez la ligne suivante dans le premier `PropertyGroup` du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="6c842-149">Enregistrez, puis fermez le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="6c842-150">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **LocalizingWpfInWf** , puis cliquez sur **recharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="6c842-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="6c842-151">Assignation d’identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="6c842-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="6c842-152">Vous pouvez mapper votre contenu localisable à des assemblys de ressources en utilisant des identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="6c842-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="6c842-153">L’application MsBuild. exe assigne automatiquement des identificateurs de ressource lorsque vous spécifiez l’option `updateuid`.</span><span class="sxs-lookup"><span data-stu-id="6c842-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="6c842-154">Pour assigner des identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="6c842-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="6c842-155">Dans le menu Démarrer, ouvrez le Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6c842-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="6c842-156">Utilisez la commande suivante pour assigner des identificateurs de ressource à votre contenu localisable.</span><span class="sxs-lookup"><span data-stu-id="6c842-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="6c842-157">Dans **Explorateur de solutions**, double-cliquez sur **SimpleControl. Xaml** pour l’ouvrir dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="6c842-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="6c842-158">Vous verrez que la commande `msbuild` a ajouté l’attribut `Uid` à tous les éléments.</span><span class="sxs-lookup"><span data-stu-id="6c842-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="6c842-159">Cela facilite la localisation par l’assignation des identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="6c842-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="6c842-160">Appuyez sur **F6** pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="6c842-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="6c842-161">Utilisation de LocBaml pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="6c842-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="6c842-162">Votre contenu localisé est stocké dans un *assembly satellite*de ressources uniquement.</span><span class="sxs-lookup"><span data-stu-id="6c842-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="6c842-163">Utilisez l’outil en ligne de commande LocBaml. exe pour produire un assembly localisé pour votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c842-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="6c842-164">Pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="6c842-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="6c842-165">Copiez LocBaml.exe dans le dossier obj\Debug de votre projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="6c842-166">Pour plus d’informations, consultez [localiser une application](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="6c842-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="6c842-167">Dans la fenêtre d’invite de commandes, utilisez la commande suivante pour extraire les chaînes de ressources dans un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="6c842-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="6c842-168">Ouvrez le fichier Temp. csv avec Visual Studio ou un autre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="6c842-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="6c842-169">Remplacez la chaîne `"Hello"` par sa traduction espagnole, `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="6c842-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="6c842-170">Enregistrez le fichier temp.csv.</span><span class="sxs-lookup"><span data-stu-id="6c842-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="6c842-171">Utilisez la commande suivante pour générer le fichier de ressources localisé.</span><span class="sxs-lookup"><span data-stu-id="6c842-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="6c842-172">Le fichier LocalizingWpfInWf.g.es-ES.resources est créé dans le dossier obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="6c842-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="6c842-173">Utilisez la commande suivante pour générer l’assembly satellite localisé.</span><span class="sxs-lookup"><span data-stu-id="6c842-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="6c842-174">Le fichier LocalizingWpfInWf.resources.dll est créé dans le dossier obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="6c842-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="6c842-175">Copiez le fichier LocalizingWpfInWf.resources.dll dans le dossier du projet bin\Debug\es-ES.</span><span class="sxs-lookup"><span data-stu-id="6c842-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="6c842-176">Remplacez le fichier existant.</span><span class="sxs-lookup"><span data-stu-id="6c842-176">Replace the existing file.</span></span>

8. <span data-ttu-id="6c842-177">Exécutez LocalizingWpfInWf.exe, qui se trouve dans le dossier bin\Debug de votre projet.</span><span class="sxs-lookup"><span data-stu-id="6c842-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="6c842-178">Ne regénérez pas l’application, car cela aura pour effet de remplacer l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="6c842-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="6c842-179">L’application affiche les chaînes localisées au lieu des chaînes en anglais.</span><span class="sxs-lookup"><span data-stu-id="6c842-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c842-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c842-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6c842-181">Localiser une application</span><span class="sxs-lookup"><span data-stu-id="6c842-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="6c842-182">[Procédure pas à pas : localisation de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6c842-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="6c842-183">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c842-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
