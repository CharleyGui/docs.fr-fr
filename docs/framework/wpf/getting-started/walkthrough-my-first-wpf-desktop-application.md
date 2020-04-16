---
title: Créez votre première application WPF dans Visual Studio 2019 - .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: facb9ebebd9ce1904886a946277185ac2c2e4bc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463923"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="5a520-102">Tutorial: Créez votre première application WPF dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5a520-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="5a520-103">Cet article vous montre comment développer une application de bureau de la Windows Presentation Foundation (WPF) qui comprend les éléments qui sont communs à la plupart des applications WPF : Marge de balisage extensible d’application (XAML), code-derrière, définitions d’applications, contrôles, mise en page, liaison de données et styles.</span><span class="sxs-lookup"><span data-stu-id="5a520-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="5a520-104">Pour développer l’application, vous utiliserez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a520-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="5a520-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="5a520-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5a520-106">Créez un projet WPF.</span><span class="sxs-lookup"><span data-stu-id="5a520-106">Create a WPF project.</span></span>
> - <span data-ttu-id="5a520-107">Utilisez XAML pour concevoir l’apparence de l’interface utilisateur de l’application (interface utilisateur).</span><span class="sxs-lookup"><span data-stu-id="5a520-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="5a520-108">Écrivez du code pour construire le comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="5a520-109">Créez une définition d’application pour gérer l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="5a520-110">Ajoutez des commandes et créez la mise en page pour composer l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="5a520-111">Créez des styles pour une apparence cohérente tout au long de l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="5a520-112">Lier l’interface utilisateur aux données, à la fois pour remplir l’interface utilisateur à partir de données et pour garder les données et l’interface utilisateur synchronisées.</span><span class="sxs-lookup"><span data-stu-id="5a520-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="5a520-113">À la fin du tutoriel, vous aurez construit une application Windows autonome qui permet aux utilisateurs de consulter les rapports de dépenses pour certaines personnes.</span><span class="sxs-lookup"><span data-stu-id="5a520-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="5a520-114">L’application est composée de plusieurs pages WPF qui sont hébergées dans une fenêtre de style navigateur.</span><span class="sxs-lookup"><span data-stu-id="5a520-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="5a520-115">L’exemple de code qui est utilisé dans ce tutoriel est disponible à la fois pour Visual Basic et C ' à [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="5a520-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="5a520-116">Vous pouvez basculer le langage de code du code de l’échantillon entre C et Visual Basic en utilisant le sélecteur de langue en haut de cette page.</span><span class="sxs-lookup"><span data-stu-id="5a520-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a520-117">Prérequis</span><span class="sxs-lookup"><span data-stu-id="5a520-117">Prerequisites</span></span>

- <span data-ttu-id="5a520-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **de développement de bureau .NET** installé.</span><span class="sxs-lookup"><span data-stu-id="5a520-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="5a520-119">Pour plus d’informations sur l’installation de la dernière version de Visual Studio, voir [Install Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5a520-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="5a520-120">Créer le projet d’application</span><span class="sxs-lookup"><span data-stu-id="5a520-120">Create the application project</span></span>

<span data-ttu-id="5a520-121">La première étape consiste à créer l’infrastructure d’application, qui comprend une définition d’application, deux pages et une image.</span><span class="sxs-lookup"><span data-stu-id="5a520-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="5a520-122">Créer un nouveau projet d’application WPF **`ExpenseIt`** dans Visual Basic ou Visual C ' nommé :</span><span class="sxs-lookup"><span data-stu-id="5a520-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="5a520-123">Ouvrez Visual Studio et sélectionnez **Créez un nouveau projet** dans le menu Get **started.**</span><span class="sxs-lookup"><span data-stu-id="5a520-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="5a520-124">Le **Dialogue Créer un nouveau projet** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="5a520-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="5a520-125">Dans le **décrocheur de la langue,** sélectionnez soit **C ou** **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="5a520-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="5a520-126">Sélectionnez le modèle **WPF App (.NET Framework)** et sélectionnez **Ensuite**.</span><span class="sxs-lookup"><span data-stu-id="5a520-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Créer un nouveau dialogue de projet](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="5a520-128">Configurez **votre nouveau dialogue de projet.**</span><span class="sxs-lookup"><span data-stu-id="5a520-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="5a520-129">Entrez le **`ExpenseIt`** nom du projet, puis sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="5a520-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Configurer un nouveau dialogue de projet](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="5a520-131">Visual Studio crée le projet et ouvre le concepteur pour la fenêtre d’application par défaut nommée **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="5a520-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="5a520-132">Open *Application.xaml* (Visual Basic) ou *App.xaml* (C).</span><span class="sxs-lookup"><span data-stu-id="5a520-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="5a520-133">Ce fichier XAML définit une application WPF et toutes les ressources d’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="5a520-134">Vous utilisez également ce fichier pour spécifier l’interface utilisateur, dans ce cas *MainWindow.xaml*, qui s’affiche automatiquement lorsque l’application commence.</span><span class="sxs-lookup"><span data-stu-id="5a520-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="5a520-135">Votre XAML devrait ressembler à ce qui suit dans Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5a520-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="5a520-136">Et comme ce qui suit dans C:</span><span class="sxs-lookup"><span data-stu-id="5a520-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="5a520-137">Ouvert *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="5a520-138">Ce fichier XAML est la fenêtre principale de votre application et affiche le contenu créé en pages.</span><span class="sxs-lookup"><span data-stu-id="5a520-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="5a520-139">La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, comme son titre, sa taille ou son icône, et gère des événements tels que la fermeture ou la dissimulation.</span><span class="sxs-lookup"><span data-stu-id="5a520-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="5a520-140">Modifier <xref:System.Windows.Window> l’élément <xref:System.Windows.Navigation.NavigationWindow>à un , comme indiqué dans le XAML suivant:</span><span class="sxs-lookup"><span data-stu-id="5a520-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="5a520-141">Cette application navigue vers différents contenus en fonction de l’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a520-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="5a520-142">C’est pourquoi <xref:System.Windows.Window> le principal doit <xref:System.Windows.Navigation.NavigationWindow>être changé en un .</span><span class="sxs-lookup"><span data-stu-id="5a520-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="5a520-143"><xref:System.Windows.Navigation.NavigationWindow>hérite de toutes <xref:System.Windows.Window>les propriétés de .</span><span class="sxs-lookup"><span data-stu-id="5a520-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5a520-144">L’élément <xref:System.Windows.Navigation.NavigationWindow> dans le fichier XAML <xref:System.Windows.Navigation.NavigationWindow> crée un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="5a520-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="5a520-145">Pour plus d’informations, voir [Aperçu de la navigation](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="5a520-146">Retirez <xref:System.Windows.Controls.Grid> les éléments <xref:System.Windows.Navigation.NavigationWindow> entre les balises.</span><span class="sxs-lookup"><span data-stu-id="5a520-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="5a520-147">Modifier les propriétés suivantes dans le <xref:System.Windows.Navigation.NavigationWindow> code XAML pour l’élément :</span><span class="sxs-lookup"><span data-stu-id="5a520-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="5a520-148">Définissez <xref:System.Windows.Window.Title%2A> la`ExpenseIt`propriété à " " .</span><span class="sxs-lookup"><span data-stu-id="5a520-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="5a520-149">Réglez la <xref:System.Windows.FrameworkElement.Height%2A> propriété à 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="5a520-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="5a520-150">Réglez la <xref:System.Windows.FrameworkElement.Width%2A> propriété à 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="5a520-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="5a520-151">Votre XAML devrait ressembler à ce qui suit pour Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5a520-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="5a520-152">Et comme ce qui suit pour C:</span><span class="sxs-lookup"><span data-stu-id="5a520-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="5a520-153">Ouvrez *MainWindow.xaml.vb* ou *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="5a520-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="5a520-154">Ce fichier est un fichier de code-derrière qui contient du code pour gérer les événements déclarés dans *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="5a520-155">Ce fichier contient une classe partielle pour la fenêtre définie en XAML.</span><span class="sxs-lookup"><span data-stu-id="5a520-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="5a520-156">Si vous utilisez C, changez la `MainWindow` <xref:System.Windows.Navigation.NavigationWindow>classe pour en tirer .</span><span class="sxs-lookup"><span data-stu-id="5a520-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="5a520-157">(Dans Visual Basic, cela se produit automatiquement lorsque vous changez la fenêtre en XAML.) Votre code CMD devrait maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="5a520-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="5a520-158">Ajouter des fichiers à l’application</span><span class="sxs-lookup"><span data-stu-id="5a520-158">Add files to the application</span></span>

<span data-ttu-id="5a520-159">Dans cette section, vous allez ajouter deux pages et une image à l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="5a520-160">Ajoutez une nouvelle page au projet *`ExpenseItHome.xaml`* et nommez-la :</span><span class="sxs-lookup"><span data-stu-id="5a520-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="5a520-161">Dans **Solution Explorer**, cliquez **`ExpenseIt`** à droite sur le nœud du projet et choisissez **Ajouter** > **la page**.</span><span class="sxs-lookup"><span data-stu-id="5a520-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="5a520-162">Dans le dialogue **Add New Item,** le modèle **Page (WPF)** est déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="5a520-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="5a520-163">Entrez **`ExpenseItHome`** le nom , puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5a520-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="5a520-164">Cette page est la première page qui s’affiche lorsque l’application est lancée.</span><span class="sxs-lookup"><span data-stu-id="5a520-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="5a520-165">Il affichera une liste de personnes à choisir, pour afficher un rapport de dépenses pour.</span><span class="sxs-lookup"><span data-stu-id="5a520-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="5a520-166">Ouvrez *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="5a520-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="5a520-167">Réglez <xref:System.Windows.Controls.Page.Title%2A> `ExpenseIt - Home`le à " ".</span><span class="sxs-lookup"><span data-stu-id="5a520-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="5a520-168">Réglez les `DesignHeight` 350 `DesignWidth` pixels et les 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="5a520-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="5a520-169">Le XAML apparaît maintenant comme suit pour Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5a520-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="5a520-170">Et comme ce qui suit pour C:</span><span class="sxs-lookup"><span data-stu-id="5a520-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="5a520-171">Ouvert *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="5a520-172">Ajoutez <xref:System.Windows.Navigation.NavigationWindow.Source%2A> une propriété <xref:System.Windows.Navigation.NavigationWindow> à l’élément`ExpenseItHome.xaml`et définissez-la à " " "</span><span class="sxs-lookup"><span data-stu-id="5a520-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="5a520-173">Cela *`ExpenseItHome.xaml`* s’établit pour être la première page ouverte lorsque l’application commence.</span><span class="sxs-lookup"><span data-stu-id="5a520-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="5a520-174">Exemple XAML dans Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5a520-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="5a520-175">Et dans C:</span><span class="sxs-lookup"><span data-stu-id="5a520-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="5a520-176">Vous pouvez également définir la propriété **Source** dans la catégorie **Divers** de la fenêtre **Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="5a520-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriété source dans la fenêtre de propriétés](./media/properties-source.png)

1. <span data-ttu-id="5a520-178">Ajoutez une autre nouvelle page WPF au projet, et *nommez-le ExpenseReportPage.xaml*:</span><span class="sxs-lookup"><span data-stu-id="5a520-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="5a520-179">Dans **Solution Explorer**, cliquez **`ExpenseIt`** à droite sur le nœud du projet et choisissez **Ajouter** > **la page**.</span><span class="sxs-lookup"><span data-stu-id="5a520-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="5a520-180">Dans le dialogue **Add New Item,** sélectionnez le modèle **De la Page (WPF).**</span><span class="sxs-lookup"><span data-stu-id="5a520-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="5a520-181">Entrez le nom **ExpenseReportPage**, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5a520-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="5a520-182">Cette page affichera le rapport de dépenses **`ExpenseItHome`** pour la personne sélectionnée sur la page.</span><span class="sxs-lookup"><span data-stu-id="5a520-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="5a520-183">Ouvrez *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="5a520-184">Réglez <xref:System.Windows.Controls.Page.Title%2A> `ExpenseIt - View Expense`le à " ".</span><span class="sxs-lookup"><span data-stu-id="5a520-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="5a520-185">Réglez les `DesignHeight` 350 `DesignWidth` pixels et les 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="5a520-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="5a520-186">*ExpenseReportPage.xaml* ressemble maintenant à ce qui suit dans Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5a520-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="5a520-187">Et comme ce qui suit dans C:</span><span class="sxs-lookup"><span data-stu-id="5a520-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="5a520-188">Ouvrez *ExpenseItHome.xaml.vb* et *ExpenseReportPage.xaml.vb*, ou *ExpenseItHome.xaml.cs* et *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="5a520-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="5a520-189">Lorsque vous créez un nouveau fichier Page, Visual Studio crée automatiquement son fichier *de code.*</span><span class="sxs-lookup"><span data-stu-id="5a520-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="5a520-190">Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a520-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="5a520-191">Votre code doit ressembler **`ExpenseItHome`** à ce qui suit pour :</span><span class="sxs-lookup"><span data-stu-id="5a520-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="5a520-192">Et comme ce qui suit pour **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="5a520-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="5a520-193">Ajoutez une image nommée *watermark.png* au projet.</span><span class="sxs-lookup"><span data-stu-id="5a520-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="5a520-194">Vous pouvez créer votre propre image, copier le fichier à partir du code de l’échantillon, ou l’obtenir à partir du référentiel [GitHub microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)</span><span class="sxs-lookup"><span data-stu-id="5a520-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="5a520-195">Cliquez à droite sur le nœud du **Shift**+projet et sélectionnez Ajouter > **l’élément existant**, ou appuyez sur Shift **Add\*\*\*\*Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="5a520-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="5a520-196">Dans le dialogue **Ajouter l’élément existant,** définissez le filtre de fichier à **tous les fichiers** ou fichiers **d’image,** naviguez sur le fichier d’image que vous souhaitez utiliser, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5a520-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="5a520-197">Génération et exécution de l’application</span><span class="sxs-lookup"><span data-stu-id="5a520-197">Build and run the application</span></span>

1. <span data-ttu-id="5a520-198">Pour créer et exécuter l’application, appuyez sur **F5** ou sélectionnez **Start Debugging** dans le menu **Debug.**</span><span class="sxs-lookup"><span data-stu-id="5a520-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="5a520-199">L’illustration suivante montre <xref:System.Windows.Navigation.NavigationWindow> l’application avec les boutons :</span><span class="sxs-lookup"><span data-stu-id="5a520-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Application après que vous l’avez construit et exécuté.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="5a520-201">Fermez l’application pour revenir à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a520-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="5a520-202">Créer la mise en page</span><span class="sxs-lookup"><span data-stu-id="5a520-202">Create the layout</span></span>

<span data-ttu-id="5a520-203">La mise en page fournit un moyen ordonné de placer des éléments d’interface utilisateur, et gère également la taille et la position de ces éléments lorsqu’une interface utilisateur est resized.</span><span class="sxs-lookup"><span data-stu-id="5a520-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="5a520-204">En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :</span><span class="sxs-lookup"><span data-stu-id="5a520-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="5a520-205"><xref:System.Windows.Controls.Canvas>- Définit une zone dans laquelle vous pouvez positionner explicitement les éléments de l’enfant en utilisant des coordonnées relatives à la zone de toile.</span><span class="sxs-lookup"><span data-stu-id="5a520-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="5a520-206"><xref:System.Windows.Controls.DockPanel>- Définit une zone où vous pouvez organiser des éléments d’enfant horizontalement ou verticalement, par rapport à l’autre.</span><span class="sxs-lookup"><span data-stu-id="5a520-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="5a520-207"><xref:System.Windows.Controls.Grid>- Définit une zone flexible de grille qui se compose de colonnes et de rangées.</span><span class="sxs-lookup"><span data-stu-id="5a520-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="5a520-208"><xref:System.Windows.Controls.StackPanel>- Organise des éléments d’enfant en une seule ligne qui peut être orientée horizontalement ou verticalement.</span><span class="sxs-lookup"><span data-stu-id="5a520-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="5a520-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- Organise et virtualise le contenu sur une seule ligne qui est orientée horizontalement ou verticalement.</span><span class="sxs-lookup"><span data-stu-id="5a520-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="5a520-210"><xref:System.Windows.Controls.WrapPanel>- Positionne les éléments de l’enfant en position séquentielle de gauche à droite, brisant le contenu à la ligne suivante au bord de la boîte contenante.</span><span class="sxs-lookup"><span data-stu-id="5a520-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="5a520-211">La commande subséquente se fait séquentiellement de haut en bas ou de droite à gauche, selon la valeur de la propriété Orientation.</span><span class="sxs-lookup"><span data-stu-id="5a520-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="5a520-212">Chacune de ces commandes de mise en page prend en charge un type particulier de mise en page pour ses éléments pour enfants.</span><span class="sxs-lookup"><span data-stu-id="5a520-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="5a520-213">`ExpenseIt`pages peuvent être resized, et chaque page a des éléments qui sont disposés horizontalement et verticalement aux côtés d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="5a520-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="5a520-214">Dans cet exemple, l’est <xref:System.Windows.Controls.Grid> utilisé comme élément de mise en page pour l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="5a520-215">Pour plus <xref:System.Windows.Controls.Panel> d’informations sur les éléments, voir [aperçu des panneaux](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="5a520-216">Pour plus d’informations sur la mise en page, voir [Layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="5a520-217">Dans cette section, vous créez une table à colonne unique avec trois lignes et une marge <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* de 10 pixels en ajoutant des définitions de colonne et de ligne à l’in .</span><span class="sxs-lookup"><span data-stu-id="5a520-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="5a520-218">Dans *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> mettre la <xref:System.Windows.Controls.Grid> propriété sur l’élément à "10,0,10,10", qui correspond à gauche, en haut, à droite et les marges inférieures:</span><span class="sxs-lookup"><span data-stu-id="5a520-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="5a520-219">Vous pouvez également définir les valeurs **de marge** dans la fenêtre **Propriétés,** dans la catégorie **Mise en page** :</span><span class="sxs-lookup"><span data-stu-id="5a520-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valeurs de marge dans la fenêtre Propriétés](./media/properties-margin.png)

2. <span data-ttu-id="5a520-221">Ajoutez le XAML <xref:System.Windows.Controls.Grid> suivant entre les balises pour créer les définitions de la ligne et de la colonne :</span><span class="sxs-lookup"><span data-stu-id="5a520-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="5a520-222">Les <xref:System.Windows.Controls.RowDefinition.Height%2A> deux lignes sont <xref:System.Windows.GridLength.Auto%2A>réglées à , ce qui signifie que les lignes sont dimensionnées en fonction du contenu dans les lignes.</span><span class="sxs-lookup"><span data-stu-id="5a520-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="5a520-223">La <xref:System.Windows.Controls.RowDefinition.Height%2A> valeur <xref:System.Windows.GridUnitType.Star> par défaut est le dimensionnement, ce qui signifie que la hauteur de la rangée est une proportion pondérée de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="5a520-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="5a520-224">Par exemple, si deux <xref:System.Windows.Controls.RowDefinition.Height%2A> rangées ont chacune un de "' , ils ont chacun une hauteur qui est la moitié de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="5a520-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="5a520-225">Votre <xref:System.Windows.Controls.Grid> devrait maintenant contenir le XAML suivant:</span><span class="sxs-lookup"><span data-stu-id="5a520-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="5a520-226">Ajouter des contrôles</span><span class="sxs-lookup"><span data-stu-id="5a520-226">Add controls</span></span>

<span data-ttu-id="5a520-227">Dans cette section, vous mettrez à jour l’interface utilisateur de la page d’accueil pour afficher une liste de personnes, où vous sélectionnez une personne pour afficher son rapport de dépenses.</span><span class="sxs-lookup"><span data-stu-id="5a520-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="5a520-228">Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application.</span><span class="sxs-lookup"><span data-stu-id="5a520-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="5a520-229">Pour plus d’informations, consultez [Contrôles](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="5a520-230">Pour créer cette interface utilisateur, vous ajouterez les éléments suivants à *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="5a520-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="5a520-231">A <xref:System.Windows.Controls.ListBox> (pour la liste des personnes).</span><span class="sxs-lookup"><span data-stu-id="5a520-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="5a520-232">A <xref:System.Windows.Controls.Label> (pour l’en-tête de liste).</span><span class="sxs-lookup"><span data-stu-id="5a520-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="5a520-233">A <xref:System.Windows.Controls.Button> (pour cliquer pour voir le rapport de dépenses pour la personne sélectionnée dans la liste).</span><span class="sxs-lookup"><span data-stu-id="5a520-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="5a520-234">Chaque contrôle est placé dans <xref:System.Windows.Controls.Grid> une <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> rangée de la en fixant la propriété ci-jointe.</span><span class="sxs-lookup"><span data-stu-id="5a520-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="5a520-235">Pour plus d’informations sur les propriétés ci-jointes, voir [Aperçu des propriétés ci-jointes](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="5a520-236">Dans *`ExpenseItHome.xaml`*, ajouter le XAML <xref:System.Windows.Controls.Grid> suivant quelque part entre les balises:</span><span class="sxs-lookup"><span data-stu-id="5a520-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="5a520-237">Vous pouvez également créer les commandes en les faisant glisser de la fenêtre de la boîte à **outils** sur la fenêtre de conception, puis en définissant leurs propriétés dans la fenêtre **propriétés.**</span><span class="sxs-lookup"><span data-stu-id="5a520-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="5a520-238">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-238">Build and run the application.</span></span>

    <span data-ttu-id="5a520-239">L’illustration suivante montre les contrôles que vous avez créés :</span><span class="sxs-lookup"><span data-stu-id="5a520-239">The following illustration shows the controls you created:</span></span>

![ExpenseIt exemple capture d’écran affichant une liste de noms](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="5a520-241">Ajouter une image et un titre</span><span class="sxs-lookup"><span data-stu-id="5a520-241">Add an image and a title</span></span>

<span data-ttu-id="5a520-242">Dans cette section, vous mettrez à jour l’interface utilisateur de la page d’accueil avec une image et un titre de page.</span><span class="sxs-lookup"><span data-stu-id="5a520-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="5a520-243">Dans *`ExpenseItHome.xaml`*, ajouter une <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> autre <xref:System.Windows.Controls.ColumnDefinition.Width%2A> colonne à l’avec un fixe de 230 pixels:</span><span class="sxs-lookup"><span data-stu-id="5a520-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="5a520-244">Ajouter une autre <xref:System.Windows.Controls.Grid.RowDefinitions%2A>rangée à la , pour un total de quatre rangées:</span><span class="sxs-lookup"><span data-stu-id="5a520-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="5a520-245">Déplacez les commandes vers la <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> deuxième colonne en définissant la propriété à 1 dans chacun des trois contrôles (Border, ListBox et Button).</span><span class="sxs-lookup"><span data-stu-id="5a520-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="5a520-246">Déplacez chaque contrôle d’affilée <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> en incrémentant sa valeur de 1 pour chacun des trois contrôles (Border, ListBox et Button) et pour l’élément Frontière.</span><span class="sxs-lookup"><span data-stu-id="5a520-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="5a520-247">Le XAML pour les trois contrôles ressemble maintenant à ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="5a520-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="5a520-248">Réglez la <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriété sur le fichier d’image *watermark.png,* en ajoutant le XAML suivant n’importe où entre les `<Grid>` étiquettes et `</Grid>` les balises :</span><span class="sxs-lookup"><span data-stu-id="5a520-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="5a520-249">Avant <xref:System.Windows.Controls.Border> l’élément, <xref:System.Windows.Controls.Label> ajoutez un avec le contenu "Voir le rapport de dépenses".</span><span class="sxs-lookup"><span data-stu-id="5a520-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="5a520-250">Cette étiquette est le titre de la page.</span><span class="sxs-lookup"><span data-stu-id="5a520-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="5a520-251">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-251">Build and run the application.</span></span>

<span data-ttu-id="5a520-252">L’illustration suivante montre les résultats de ce que vous venez d’ajouter :</span><span class="sxs-lookup"><span data-stu-id="5a520-252">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt exemple capture d’écran montrant le nouveau fond d’image et le titre de la page](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="5a520-254">Ajouter du code pour gérer les événements</span><span class="sxs-lookup"><span data-stu-id="5a520-254">Add code to handle events</span></span>

1. <span data-ttu-id="5a520-255">Ajouter *`ExpenseItHome.xaml`* un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements à l’élément. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="5a520-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="5a520-256">Pour plus d’informations, voir [Comment : Créer un gestionnaire d’événement simple.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5a520-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="5a520-257">*`ExpenseItHome.xaml.vb`* Ouvrez *`ExpenseItHome.xaml.cs`* ou .</span><span class="sxs-lookup"><span data-stu-id="5a520-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="5a520-258">Ajoutez le code `ExpenseItHome` suivant à la classe pour ajouter un bouton cliquez sur gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5a520-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="5a520-259">Le gestionnaire de l’événement ouvre la page **ExpenseReportPage.**</span><span class="sxs-lookup"><span data-stu-id="5a520-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="5a520-260">Créer l’interface utilisateur pour ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="5a520-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="5a520-261">*ExpenseReportPage.xaml* affiche le rapport de dépenses pour **`ExpenseItHome`** la personne sélectionnée sur la page.</span><span class="sxs-lookup"><span data-stu-id="5a520-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="5a520-262">Dans cette section, vous créerez l’interface utilisateur pour **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="5a520-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="5a520-263">Vous ajouterez également des fonds d’arrière-plan et remplirez les couleurs aux différents éléments d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a520-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="5a520-264">Ouvrez *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="5a520-265">Ajoutez le XAML <xref:System.Windows.Controls.Grid> suivant entre les balises :</span><span class="sxs-lookup"><span data-stu-id="5a520-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="5a520-266">Cette interface utilisateur *`ExpenseItHome.xaml`* est similaire à , sauf <xref:System.Windows.Controls.DataGrid>que les données du rapport est affichée dans un .</span><span class="sxs-lookup"><span data-stu-id="5a520-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="5a520-267">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-267">Build and run the application.</span></span>

4. <span data-ttu-id="5a520-268">Sélectionnez le bouton **View.**</span><span class="sxs-lookup"><span data-stu-id="5a520-268">Select the **View** button.</span></span>

    <span data-ttu-id="5a520-269">La page de note de frais s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5a520-269">The expense report page appears.</span></span> <span data-ttu-id="5a520-270">Notez également que le bouton de navigation arrière est activé.</span><span class="sxs-lookup"><span data-stu-id="5a520-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="5a520-271">L’illustration suivante montre les éléments d’interface utilisateur ajoutés à *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt exemple capture d’écran montrant l’interface utilisateur vient de créer pour le ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="5a520-273">Contrôles de style</span><span class="sxs-lookup"><span data-stu-id="5a520-273">Style controls</span></span>

<span data-ttu-id="5a520-274">L’apparition de divers éléments est souvent la même pour tous les éléments du même type dans une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a520-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="5a520-275">L’interface utilisateur utilise des [styles](../controls/styling-and-templating.md) pour rendre les apparences réutilisables sur plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="5a520-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="5a520-276">La réutilisabilité des styles permet de simplifier la création et la gestion de XAML.</span><span class="sxs-lookup"><span data-stu-id="5a520-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="5a520-277">Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="5a520-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="5a520-278">Ouvrez *Application.xaml* ou *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="5a520-279">Ajoutez le XAML <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> suivant entre les balises :</span><span class="sxs-lookup"><span data-stu-id="5a520-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="5a520-280">Ce code XAML ajoute les styles suivants :</span><span class="sxs-lookup"><span data-stu-id="5a520-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="5a520-281">`headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="5a520-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="5a520-282">`labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="5a520-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="5a520-283">`columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="5a520-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="5a520-284">`listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste.</span><span class="sxs-lookup"><span data-stu-id="5a520-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="5a520-285">`listHeaderTextStyle`: Pour formater <xref:System.Windows.Controls.Label>l’en-tête de liste .</span><span class="sxs-lookup"><span data-stu-id="5a520-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="5a520-286">`buttonStyle`: Pour <xref:System.Windows.Controls.Button> formater le on `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="5a520-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="5a520-287">Notez que les styles sont <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> des ressources et des enfants de l’élément propriété.</span><span class="sxs-lookup"><span data-stu-id="5a520-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="5a520-288">À cet emplacement, les styles sont appliqués à tous les éléments d’une application.</span><span class="sxs-lookup"><span data-stu-id="5a520-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="5a520-289">Par exemple d’utiliser des ressources dans une application .NET, voir [Use Application Resources](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="5a520-290">Dans *`ExpenseItHome.xaml`*, remplacer <xref:System.Windows.Controls.Grid> tout entre les éléments par le XAML suivant:</span><span class="sxs-lookup"><span data-stu-id="5a520-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="5a520-291">Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles.</span><span class="sxs-lookup"><span data-stu-id="5a520-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="5a520-292">Par exemple, `headerTextStyle` le s’applique au <xref:System.Windows.Controls.Label>« Rapport de dépense de vue ».</span><span class="sxs-lookup"><span data-stu-id="5a520-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="5a520-293">Ouvrez *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="5a520-294">Remplacez tout <xref:System.Windows.Controls.Grid> entre les éléments par le XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="5a520-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="5a520-295">Cette XAML ajoute <xref:System.Windows.Controls.Label> des <xref:System.Windows.Controls.Border> styles à la et des éléments.</span><span class="sxs-lookup"><span data-stu-id="5a520-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="5a520-296">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-296">Build and run the application.</span></span> <span data-ttu-id="5a520-297">L’apparence de la fenêtre est la même qu’auparavant.</span><span class="sxs-lookup"><span data-stu-id="5a520-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt capture d’écran de l’échantillon avec la même apparence que dans la dernière section.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="5a520-299">Fermez l’application pour revenir à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a520-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="5a520-300">Lier les données à un contrôle</span><span class="sxs-lookup"><span data-stu-id="5a520-300">Bind data to a control</span></span>

<span data-ttu-id="5a520-301">Dans cette section, vous allez créer les données XML qui sont liées à divers contrôles.</span><span class="sxs-lookup"><span data-stu-id="5a520-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="5a520-302">Dans *`ExpenseItHome.xaml`*, après <xref:System.Windows.Controls.Grid> l’élément d’ouverture, ajouter <xref:System.Windows.Data.XmlDataProvider> le XAML suivant pour créer un qui contient les données pour chaque personne:</span><span class="sxs-lookup"><span data-stu-id="5a520-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="5a520-303">Les données sont <xref:System.Windows.Controls.Grid> créées comme une ressource.</span><span class="sxs-lookup"><span data-stu-id="5a520-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="5a520-304">Normalement, ces données seraient chargées comme un fichier, mais pour la simplicité, les données sont ajoutées en ligne.</span><span class="sxs-lookup"><span data-stu-id="5a520-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="5a520-305">Dans `<Grid.Resources>` l’élément, `<xref:System.Windows.DataTemplate>` ajouter l’élément suivant, qui définit <xref:System.Windows.Controls.ListBox>comment `<XmlDataProvider>` afficher les données dans le , après l’élément:</span><span class="sxs-lookup"><span data-stu-id="5a520-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="5a520-306">Pour plus d’informations sur les modèles de données, voir [l’aperçu des données.](../data/data-templating-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5a520-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="5a520-307">Remplacer l’existant <xref:System.Windows.Controls.ListBox> par le XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="5a520-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="5a520-308">Ce XAML lie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la <xref:System.Windows.Controls.ListBox> propriété de la source de données <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>et applique le modèle de données comme le .</span><span class="sxs-lookup"><span data-stu-id="5a520-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="5a520-309">Connectez les données aux contrôles</span><span class="sxs-lookup"><span data-stu-id="5a520-309">Connect data to controls</span></span>

<span data-ttu-id="5a520-310">Ensuite, vous ajouterez du code pour récupérer le **`ExpenseItHome`** nom sélectionné sur la page et le transmettre au constructeur de **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="5a520-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="5a520-311">**ExpenseReportPage** définit son contexte de données avec l’élément passé, ce à quoi les contrôles définis dans *ExpenseReportPage.xaml* lient.</span><span class="sxs-lookup"><span data-stu-id="5a520-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="5a520-312">Ouvrez *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="5a520-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="5a520-313">Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="5a520-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="5a520-314">*`ExpenseItHome.xaml.vb`* Ouvrez *`ExpenseItHome.xaml.cs`* ou .</span><span class="sxs-lookup"><span data-stu-id="5a520-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="5a520-315">Modifier <xref:System.Windows.Controls.Primitives.ButtonBase.Click> le gestionnaire d’événements pour appeler le nouveau constructeur en passant les données de rapport de dépenses de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="5a520-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="5a520-316">Données de style avec modèles de données</span><span class="sxs-lookup"><span data-stu-id="5a520-316">Style data with data templates</span></span>

<span data-ttu-id="5a520-317">Dans cette section, vous mettrez à jour l’interface utilisateur pour chaque élément des listes de données en utilisant des modèles de données.</span><span class="sxs-lookup"><span data-stu-id="5a520-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="5a520-318">Ouvrez *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="5a520-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="5a520-319">Lier le contenu des éléments «Nom» et «Département» <xref:System.Windows.Controls.Label> à la propriété de source de données appropriée.</span><span class="sxs-lookup"><span data-stu-id="5a520-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="5a520-320">Pour plus d’informations sur la liaison des données, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a520-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="5a520-321">Après l’élément d’ouverture, <xref:System.Windows.Controls.Grid> ajoutez les modèles de données suivants, qui définissent comment afficher les données du rapport de dépenses :</span><span class="sxs-lookup"><span data-stu-id="5a520-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="5a520-322">Remplacez <xref:System.Windows.Controls.DataGridTextColumn> les <xref:System.Windows.Controls.DataGridTemplateColumn> éléments <xref:System.Windows.Controls.DataGrid> par sous l’élément et appliquez les modèles à eux.</span><span class="sxs-lookup"><span data-stu-id="5a520-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="5a520-323">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="5a520-323">Build and run the application.</span></span>

6. <span data-ttu-id="5a520-324">Sélectionnez une personne, puis sélectionnez le bouton **Afficher.**</span><span class="sxs-lookup"><span data-stu-id="5a520-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="5a520-325">L’illustration suivante montre `ExpenseIt` les deux pages de l’application avec des contrôles, la mise en page, les styles, la liaison de données et les modèles de données appliqués :</span><span class="sxs-lookup"><span data-stu-id="5a520-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Les deux pages de l’application montrant la liste des noms et un rapport de dépenses.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="5a520-327">Cet échantillon démontre une caractéristique spécifique du WPF et ne suit pas toutes les meilleures pratiques pour des choses comme la sécurité, la localisation et l’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="5a520-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="5a520-328">Pour une couverture complète de WPF et les meilleures pratiques de développement de l’application .NET, voir les sujets suivants:</span><span class="sxs-lookup"><span data-stu-id="5a520-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="5a520-329">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="5a520-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="5a520-330">Sécurité</span><span class="sxs-lookup"><span data-stu-id="5a520-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="5a520-331">Globalisation et localisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="5a520-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="5a520-332">Performances WPF</span><span class="sxs-lookup"><span data-stu-id="5a520-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="5a520-333">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5a520-333">Next steps</span></span>

<span data-ttu-id="5a520-334">Dans ce pas-là, vous avez appris un certain nombre de techniques pour créer une interface utilisateur en utilisant Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5a520-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="5a520-335">Vous devez maintenant avoir une compréhension de base des éléments constitutifs d’une application .NET liée aux données.</span><span class="sxs-lookup"><span data-stu-id="5a520-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="5a520-336">Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a520-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="5a520-337">Architecture WPF</span><span class="sxs-lookup"><span data-stu-id="5a520-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="5a520-338">Vue d’ensemble XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5a520-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="5a520-339">Aperçu des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="5a520-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="5a520-340">Mise en page</span><span class="sxs-lookup"><span data-stu-id="5a520-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="5a520-341">Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a520-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="5a520-342">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="5a520-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="5a520-343">Contrôles</span><span class="sxs-lookup"><span data-stu-id="5a520-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="5a520-344">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="5a520-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5a520-345">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="5a520-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="5a520-346">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="5a520-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="5a520-347">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a520-347">See also</span></span>

- [<span data-ttu-id="5a520-348">Aperçu des panneaux</span><span class="sxs-lookup"><span data-stu-id="5a520-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="5a520-349">Aperçu de la température des données</span><span class="sxs-lookup"><span data-stu-id="5a520-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="5a520-350">Construire une application WPF</span><span class="sxs-lookup"><span data-stu-id="5a520-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="5a520-351">Styles et modèles</span><span class="sxs-lookup"><span data-stu-id="5a520-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
