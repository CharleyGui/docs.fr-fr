---
title: Déboguer des contrôles personnalisés au moment du design
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740185"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="8532d-102">Procédure pas à pas : déboguer des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="8532d-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="8532d-103">Lorsque vous créez un contrôle personnalisé, il est souvent nécessaire de déboguer son comportement au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="8532d-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="8532d-104">Cela est particulièrement vrai si vous créez un concepteur personnalisé pour votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="8532d-105">Pour plus d’informations, consultez [procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="8532d-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="8532d-106">Vous pouvez déboguer vos contrôles personnalisés à l’aide de Visual Studio, tout comme vous le feriez pour tout autre .NET Framework classes.</span><span class="sxs-lookup"><span data-stu-id="8532d-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="8532d-107">La différence réside dans le fait que vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="8532d-108">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="8532d-108">Create the project</span></span>

<span data-ttu-id="8532d-109">La première étape consiste à créer le projet d’application.</span><span class="sxs-lookup"><span data-stu-id="8532d-109">The first step is to create the application project.</span></span> <span data-ttu-id="8532d-110">Vous allez utiliser ce projet pour générer l’application qui héberge le contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="8532d-111">Dans Visual Studio, créez un projet d’application Windows et nommez-le **DebuggingExample**.</span><span class="sxs-lookup"><span data-stu-id="8532d-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="8532d-112">Créer le projet de bibliothèque de contrôles</span><span class="sxs-lookup"><span data-stu-id="8532d-112">Create the control library project</span></span>

1. <span data-ttu-id="8532d-113">Ajoutez un projet de **bibliothèque de contrôles Windows** à la solution.</span><span class="sxs-lookup"><span data-stu-id="8532d-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="8532d-114">Ajoutez un nouvel élément **UserControl** au projet DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="8532d-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="8532d-115">Nommez-le **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="8532d-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="8532d-116">Dans **Explorateur de solutions**, supprimez le contrôle par défaut du projet en supprimant le fichier de code portant le nom de base UserControl1.</span><span class="sxs-lookup"><span data-stu-id="8532d-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="8532d-117">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="8532d-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="8532d-118">Point de contrôle</span><span class="sxs-lookup"><span data-stu-id="8532d-118">Checkpoint</span></span>

<span data-ttu-id="8532d-119">À ce stade, vous serez en mesure de voir votre contrôle personnalisé dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="8532d-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="8532d-120">Pour vérifier votre progression, recherchez le nouvel onglet appelé le **composant DebugControlLibrary** , puis cliquez dessus pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="8532d-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="8532d-121">Lorsqu’il s’ouvre, votre contrôle est affiché en tant que **DebugControl** avec l’icône par défaut en regard.</span><span class="sxs-lookup"><span data-stu-id="8532d-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="8532d-122">Ajouter une propriété à votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="8532d-122">Add a property to your custom control</span></span>

<span data-ttu-id="8532d-123">Pour montrer que le code de votre contrôle personnalisé est en cours d’exécution au moment de la conception, vous allez ajouter une propriété et définir un point d’arrêt dans le code qui implémente la propriété.</span><span class="sxs-lookup"><span data-stu-id="8532d-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="8532d-124">Ouvrez **DebugControl** dans l' **éditeur de code**.</span><span class="sxs-lookup"><span data-stu-id="8532d-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="8532d-125">Ajoutez le code suivant à la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="8532d-125">Add the following code to the class definition:</span></span>

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. <span data-ttu-id="8532d-126">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="8532d-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="8532d-127">Ajouter votre contrôle personnalisé au formulaire hôte</span><span class="sxs-lookup"><span data-stu-id="8532d-127">Add your custom control to the host form</span></span>

<span data-ttu-id="8532d-128">Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous devez placer une instance de la classe de contrôle personnalisé sur un formulaire hôte.</span><span class="sxs-lookup"><span data-stu-id="8532d-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="8532d-129">Dans le projet « DebuggingExample », ouvrez Formulaire1 dans le **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="8532d-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="8532d-130">Dans la **boîte à outils**, ouvrez l’onglet **Composants DebugControlLibrary** et faites glisser une instance **DebugControl** sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8532d-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="8532d-131">Recherchez la propriété personnalisée `DemoString` dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="8532d-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="8532d-132">Notez que vous pouvez modifier sa valeur comme n’importe quelle autre propriété.</span><span class="sxs-lookup"><span data-stu-id="8532d-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="8532d-133">Notez également que lorsque la propriété `DemoString` est sélectionnée, la chaîne de description de la propriété apparaît en bas de la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="8532d-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="8532d-134">Configurer le projet pour le débogage au moment du design</span><span class="sxs-lookup"><span data-stu-id="8532d-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="8532d-135">Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="8532d-136">Cliquez avec le bouton droit sur le projet **DebugControlLibrary** dans le **Explorateur de solutions** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8532d-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="8532d-137">Dans la feuille de propriétés **DebugControlLibrary** , sélectionnez l’onglet **Déboguer** .</span><span class="sxs-lookup"><span data-stu-id="8532d-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="8532d-138">Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe**.</span><span class="sxs-lookup"><span data-stu-id="8532d-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="8532d-139">Vous allez déboguer une instance distincte de Visual Studio. par conséquent, cliquez sur les points de suspension (![le bouton de sélection (...) du bouton Fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour Rechercher l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8532d-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="8532d-140">Le nom du fichier exécutable est **devenv. exe**, et si vous avez installé à l’emplacement par défaut, son chemin d’accès est *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="8532d-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="8532d-141">Sélectionnez **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8532d-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="8532d-142">Cliquez avec le bouton droit sur le projet **DebugControlLibrary** et sélectionnez **définir comme projet de démarrage** pour activer cette configuration de débogage.</span><span class="sxs-lookup"><span data-stu-id="8532d-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="8532d-143">Déboguer votre contrôle personnalisé au moment du design</span><span class="sxs-lookup"><span data-stu-id="8532d-143">Debug your custom control at design time</span></span>

<span data-ttu-id="8532d-144">Vous êtes maintenant prêt à déboguer votre contrôle personnalisé lorsqu’il s’exécute en mode création.</span><span class="sxs-lookup"><span data-stu-id="8532d-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="8532d-145">Quand vous démarrez la session de débogage, une nouvelle instance de Visual Studio est créée. vous l’utiliserez pour charger la solution « DebuggingExample ».</span><span class="sxs-lookup"><span data-stu-id="8532d-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="8532d-146">Quand vous ouvrez Form1 dans le **Concepteur de formulaires**, une instance de votre contrôle personnalisé est créée et commence à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="8532d-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="8532d-147">Ouvrez le fichier source **DebugControl** dans l' **éditeur de code** et placez un point d’arrêt sur l’accesseur `Set` de la propriété `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="8532d-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="8532d-148">Appuyez sur **F5** pour démarrer la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="8532d-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="8532d-149">Une nouvelle instance de Visual Studio est créée.</span><span class="sxs-lookup"><span data-stu-id="8532d-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="8532d-150">Vous pouvez faire la distinction entre les instances de deux manières :</span><span class="sxs-lookup"><span data-stu-id="8532d-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="8532d-151">Le mot est en **cours d’exécution** dans la barre de titre de l’instance de débogage</span><span class="sxs-lookup"><span data-stu-id="8532d-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="8532d-152">Le bouton **Démarrer** de la barre d’outils de **débogage de** l’instance de débogage est désactivé</span><span class="sxs-lookup"><span data-stu-id="8532d-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="8532d-153">Votre point d’arrêt est défini dans l’instance de débogage.</span><span class="sxs-lookup"><span data-stu-id="8532d-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="8532d-154">Dans la nouvelle instance de Visual Studio, ouvrez la solution « DebuggingExample ».</span><span class="sxs-lookup"><span data-stu-id="8532d-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="8532d-155">Vous pouvez facilement trouver la solution en sélectionnant **projets récents** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="8532d-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="8532d-156">Le fichier solution « DebuggingExample. sln » est listé comme le fichier le plus récemment utilisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="8532d-157">Ouvrez Form1 dans le **Concepteur de formulaires** et sélectionnez le contrôle **DebugControl** .</span><span class="sxs-lookup"><span data-stu-id="8532d-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="8532d-158">Modifiez la valeur de la propriété `DemoString` .</span><span class="sxs-lookup"><span data-stu-id="8532d-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="8532d-159">Lorsque vous validez la modification, l’instance de débogage de Visual Studio acquiert le focus et l’exécution s’arrête à votre point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="8532d-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="8532d-160">Vous pouvez effectuer un pas à pas détaillé dans l’accesseur de propriété comme pour tout autre code.</span><span class="sxs-lookup"><span data-stu-id="8532d-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="8532d-161">Pour arrêter le débogage, quittez l’instance hébergée de Visual Studio ou sélectionnez le bouton **arrêter le débogage** dans l’instance de débogage.</span><span class="sxs-lookup"><span data-stu-id="8532d-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8532d-162">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8532d-162">Next steps</span></span>

<span data-ttu-id="8532d-163">Maintenant que vous pouvez déboguer vos contrôles personnalisés au moment de la conception, il existe de nombreuses possibilités pour étendre l’interaction de votre contrôle avec l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8532d-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="8532d-164">Vous pouvez utiliser la propriété <xref:System.ComponentModel.Component.DesignMode%2A> de la classe <xref:System.ComponentModel.Component> pour écrire du code qui s’exécute uniquement au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="8532d-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="8532d-165">Pour plus d'informations, consultez <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8532d-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="8532d-166">Il existe plusieurs attributs que vous pouvez appliquer aux propriétés de votre contrôle pour manipuler l’interaction de votre contrôle personnalisé avec le concepteur.</span><span class="sxs-lookup"><span data-stu-id="8532d-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="8532d-167">Vous pouvez trouver ces attributs dans l’espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8532d-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="8532d-168">Vous pouvez écrire un concepteur personnalisé pour votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8532d-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="8532d-169">Vous bénéficiez ainsi d’un contrôle total sur l’expérience de conception à l’aide de l’infrastructure de concepteur extensible exposée par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8532d-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="8532d-170">Pour plus d’informations, consultez [procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="8532d-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8532d-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8532d-171">See also</span></span>

- [<span data-ttu-id="8532d-172">Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8532d-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
