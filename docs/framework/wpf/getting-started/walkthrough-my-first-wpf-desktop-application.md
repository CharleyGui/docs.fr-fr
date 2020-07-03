---
title: Créer votre première application WPF dans Visual Studio 2019-.NET Framework
titleSuffix: ''
description: Développez une application de bureau Windows Presentation Foundation (WPF) qui comprend des éléments communs à la plupart des applications WPF.
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
ms.openlocfilehash: c9af988bcf291325b11df4fd22827b47090c0b48
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853895"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="94699-103">Didacticiel : créer votre première application WPF dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="94699-103">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="94699-104">Cet article vous montre comment développer une application de bureau Windows Presentation Foundation (WPF) qui comprend les éléments communs à la plupart des applications WPF : balisage XAML Extensible Application Markup Language (XAML), code-behind, définitions d’application, contrôles, disposition, liaison de données et styles.</span><span class="sxs-lookup"><span data-stu-id="94699-104">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="94699-105">Pour développer l’application, vous allez utiliser Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94699-105">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="94699-106">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="94699-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="94699-107">Créez un projet WPF.</span><span class="sxs-lookup"><span data-stu-id="94699-107">Create a WPF project.</span></span>
> - <span data-ttu-id="94699-108">Utilisez XAML pour concevoir l’apparence de l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-108">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="94699-109">Écrivez du code pour générer le comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-109">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="94699-110">Créez une définition d’application pour gérer l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-110">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="94699-111">Ajoutez des contrôles et créez la disposition pour composer l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-111">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="94699-112">Créer des styles pour une apparence cohérente dans l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-112">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="94699-113">Liez l’interface utilisateur aux données, à la fois pour remplir l’interface utilisateur à partir des données et pour maintenir la synchronisation des données et de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94699-113">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="94699-114">À la fin du didacticiel, vous aurez créé une application Windows autonome qui permet aux utilisateurs d’afficher les notes de frais pour les personnes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="94699-114">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="94699-115">L’application est composée de plusieurs pages WPF qui sont hébergées dans une fenêtre de style navigateur.</span><span class="sxs-lookup"><span data-stu-id="94699-115">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="94699-116">L’exemple de code utilisé dans ce didacticiel est disponible pour les Visual Basic et C# dans le [didacticiel exemple de code d’application WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="94699-116">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="94699-117">Vous pouvez basculer le langage de code de l’exemple de code entre C# et Visual Basic à l’aide du sélecteur de langue en haut de cette page.</span><span class="sxs-lookup"><span data-stu-id="94699-117">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94699-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="94699-118">Prerequisites</span></span>

- <span data-ttu-id="94699-119">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement .net Desktop** installée.</span><span class="sxs-lookup"><span data-stu-id="94699-119">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="94699-120">Pour plus d’informations sur l’installation de la dernière version de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="94699-120">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="94699-121">Créer le projet d’application</span><span class="sxs-lookup"><span data-stu-id="94699-121">Create the application project</span></span>

<span data-ttu-id="94699-122">La première étape consiste à créer l’infrastructure d’application, qui comprend une définition d’application, deux pages et une image.</span><span class="sxs-lookup"><span data-stu-id="94699-122">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="94699-123">Créez un projet d’application WPF dans Visual Basic ou Visual C# nommé **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="94699-123">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="94699-124">Ouvrez Visual Studio et sélectionnez **créer un nouveau projet** dans le menu **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="94699-124">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="94699-125">La boîte de dialogue **créer un nouveau projet** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="94699-125">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="94699-126">Dans la liste déroulante **langue** , sélectionnez **C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="94699-126">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="94699-127">Sélectionnez le modèle **application WPF (.NET Framework)** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="94699-127">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Boîte de dialogue créer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="94699-129">La boîte de dialogue **configurer votre nouveau projet** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="94699-129">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="94699-130">Entrez le nom du projet **`ExpenseIt`** , puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="94699-130">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Boîte de dialogue Configurer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="94699-132">Visual Studio crée le projet et ouvre le concepteur pour la fenêtre d’application par défaut nommée **MainWindow. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="94699-132">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="94699-133">Ouvrez *application. Xaml* (Visual Basic) ou *app. Xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="94699-133">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="94699-134">Ce fichier XAML définit une application WPF et toutes les ressources d’application.</span><span class="sxs-lookup"><span data-stu-id="94699-134">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="94699-135">Vous utilisez également ce fichier pour spécifier l’interface utilisateur, dans ce cas, *MainWindow. Xaml*, qui s’affiche automatiquement au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-135">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="94699-136">Votre code XAML doit ressembler à ce qui suit dans Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="94699-136">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="94699-137">Et comme ce qui suit en C# :</span><span class="sxs-lookup"><span data-stu-id="94699-137">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="94699-138">Ouvrez *MainWindow. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-138">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="94699-139">Ce fichier XAML est la fenêtre principale de votre application et affiche le contenu créé dans les pages.</span><span class="sxs-lookup"><span data-stu-id="94699-139">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="94699-140">La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, telles que son titre, sa taille ou son icône, et gère les événements, tels que la fermeture ou le masquage.</span><span class="sxs-lookup"><span data-stu-id="94699-140">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="94699-141">Remplacez l' <xref:System.Windows.Window> élément par un <xref:System.Windows.Navigation.NavigationWindow> , comme indiqué dans le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="94699-141">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="94699-142">Cette application accède à un contenu différent en fonction de l’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94699-142">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="94699-143">C’est la raison pour laquelle le principal <xref:System.Windows.Window> doit être remplacé par un <xref:System.Windows.Navigation.NavigationWindow> .</span><span class="sxs-lookup"><span data-stu-id="94699-143">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="94699-144"><xref:System.Windows.Navigation.NavigationWindow>hérite de toutes les propriétés de <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="94699-144"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="94699-145">L' <xref:System.Windows.Navigation.NavigationWindow> élément dans le fichier XAML crée une instance de la <xref:System.Windows.Navigation.NavigationWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="94699-145">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="94699-146">Pour plus d’informations, consultez [vue d’ensemble](../app-development/navigation-overview.md)de la navigation.</span><span class="sxs-lookup"><span data-stu-id="94699-146">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="94699-147">Supprimez les <xref:System.Windows.Controls.Grid> éléments entre les <xref:System.Windows.Navigation.NavigationWindow> balises.</span><span class="sxs-lookup"><span data-stu-id="94699-147">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="94699-148">Modifiez les propriétés suivantes dans le code XAML pour l' <xref:System.Windows.Navigation.NavigationWindow> élément :</span><span class="sxs-lookup"><span data-stu-id="94699-148">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="94699-149">Affectez <xref:System.Windows.Window.Title%2A> à la propriété la valeur " `ExpenseIt` ".</span><span class="sxs-lookup"><span data-stu-id="94699-149">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="94699-150">Affectez <xref:System.Windows.FrameworkElement.Height%2A> à la propriété la valeur 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="94699-150">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="94699-151">Affectez <xref:System.Windows.FrameworkElement.Width%2A> à la propriété la valeur 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="94699-151">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="94699-152">Votre code XAML doit ressembler à ce qui suit pour Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="94699-152">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="94699-153">Et comme suit pour C# :</span><span class="sxs-lookup"><span data-stu-id="94699-153">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="94699-154">Ouvrez *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="94699-154">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="94699-155">Ce fichier est un fichier code-behind qui contient le code permettant de gérer les événements déclarés dans *MainWindow. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-155">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="94699-156">Ce fichier contient une classe partielle pour la fenêtre définie en XAML.</span><span class="sxs-lookup"><span data-stu-id="94699-156">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="94699-157">Si vous utilisez C#, modifiez la `MainWindow` classe pour qu’elle dérive de <xref:System.Windows.Navigation.NavigationWindow> .</span><span class="sxs-lookup"><span data-stu-id="94699-157">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="94699-158">(Dans Visual Basic, cela se produit automatiquement lorsque vous modifiez la fenêtre en XAML.) Votre code C# doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="94699-158">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="94699-159">Ajouter des fichiers à l’application</span><span class="sxs-lookup"><span data-stu-id="94699-159">Add files to the application</span></span>

<span data-ttu-id="94699-160">Dans cette section, vous allez ajouter deux pages et une image à l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-160">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="94699-161">Ajoutez une nouvelle page au projet et nommez-la *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="94699-161">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="94699-162">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le **`ExpenseIt`** nœud du projet et choisissez **Ajouter**une  >  **page**.</span><span class="sxs-lookup"><span data-stu-id="94699-162">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="94699-163">Dans la boîte de dialogue **Ajouter un nouvel élément** , le modèle **page (WPF)** est déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="94699-163">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="94699-164">Entrez le nom **`ExpenseItHome`** , puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="94699-164">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="94699-165">Cette page est la première page qui s’affiche lorsque l’application est lancée.</span><span class="sxs-lookup"><span data-stu-id="94699-165">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="94699-166">Elle affiche une liste des personnes à sélectionner, pour afficher une note de frais pour.</span><span class="sxs-lookup"><span data-stu-id="94699-166">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="94699-167">Ouvrez *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="94699-167">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="94699-168">Affectez <xref:System.Windows.Controls.Page.Title%2A> à la valeur « `ExpenseIt - Home` ».</span><span class="sxs-lookup"><span data-stu-id="94699-168">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="94699-169">Définissez `DesignHeight` sur 350 pixels et `DesignWidth` sur 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="94699-169">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="94699-170">Le code XAML se présente désormais comme suit pour Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="94699-170">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="94699-171">Et comme suit pour C# :</span><span class="sxs-lookup"><span data-stu-id="94699-171">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="94699-172">Ouvrez *MainWindow. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-172">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="94699-173">Ajoutez une <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriété à l' <xref:System.Windows.Navigation.NavigationWindow> élément et affectez-lui la valeur " `ExpenseItHome.xaml` ".</span><span class="sxs-lookup"><span data-stu-id="94699-173">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="94699-174">Cela définit *`ExpenseItHome.xaml`* la première page ouverte au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-174">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="94699-175">Exemple de code XAML dans Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="94699-175">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="94699-176">Et en C# :</span><span class="sxs-lookup"><span data-stu-id="94699-176">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="94699-177">Vous pouvez également définir la propriété **source** dans la catégorie **divers** de la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="94699-177">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriété source dans Fenêtre Propriétés](./media/properties-source.png)

1. <span data-ttu-id="94699-179">Ajoutez une autre nouvelle page WPF au projet et nommez-la *ExpenseReportPage. Xaml*::</span><span class="sxs-lookup"><span data-stu-id="94699-179">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="94699-180">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le **`ExpenseIt`** nœud du projet et choisissez **Ajouter**une  >  **page**.</span><span class="sxs-lookup"><span data-stu-id="94699-180">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="94699-181">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **page (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="94699-181">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="94699-182">Entrez le nom **ExpenseReportPage**, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="94699-182">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="94699-183">Cette page affiche la note de frais de la personne sélectionnée sur la **`ExpenseItHome`** page.</span><span class="sxs-lookup"><span data-stu-id="94699-183">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="94699-184">Ouvrez *ExpenseReportPage. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-184">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="94699-185">Affectez <xref:System.Windows.Controls.Page.Title%2A> à la valeur « `ExpenseIt - View Expense` ».</span><span class="sxs-lookup"><span data-stu-id="94699-185">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="94699-186">Définissez `DesignHeight` sur 350 pixels et `DesignWidth` sur 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="94699-186">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="94699-187">*ExpenseReportPage. Xaml* ressemble maintenant à ce qui suit dans Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="94699-187">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="94699-188">Et comme ce qui suit en C# :</span><span class="sxs-lookup"><span data-stu-id="94699-188">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="94699-189">Ouvrez *ExpenseItHome. Xaml. vb* et *ExpenseReportPage. Xaml. vb*, ou *ExpenseItHome.Xaml.cs* et *ExpenseReportPage.Xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="94699-189">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="94699-190">Lorsque vous créez un nouveau fichier d’échange, Visual Studio crée automatiquement son fichier *code-behind* .</span><span class="sxs-lookup"><span data-stu-id="94699-190">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="94699-191">Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94699-191">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="94699-192">Votre code doit ressembler à ce qui suit pour **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="94699-192">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="94699-193">Et comme suit pour **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="94699-193">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="94699-194">Ajoutez une image nommée *watermark.png* au projet.</span><span class="sxs-lookup"><span data-stu-id="94699-194">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="94699-195">Vous pouvez créer votre propre image, copier le fichier à partir de l’exemple de code ou l’extraire à partir du référentiel GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .</span><span class="sxs-lookup"><span data-stu-id="94699-195">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="94699-196">Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  un**élément existant**, ou appuyez sur **MAJ** + **ALT** + **A**.</span><span class="sxs-lookup"><span data-stu-id="94699-196">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="94699-197">Dans la boîte de dialogue **Ajouter un élément existant** , définissez le filtre de fichiers sur **tous les fichiers** ou **fichiers image**, accédez au fichier image que vous souhaitez utiliser, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="94699-197">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="94699-198">Génération et exécution de l’application</span><span class="sxs-lookup"><span data-stu-id="94699-198">Build and run the application</span></span>

1. <span data-ttu-id="94699-199">Pour générer et exécuter l’application, appuyez sur **F5** ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer** .</span><span class="sxs-lookup"><span data-stu-id="94699-199">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="94699-200">L’illustration suivante montre l’application avec les <xref:System.Windows.Navigation.NavigationWindow> boutons :</span><span class="sxs-lookup"><span data-stu-id="94699-200">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Application après l’avoir générée et exécutée.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="94699-202">Fermez l’application pour revenir à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94699-202">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="94699-203">Créer la disposition</span><span class="sxs-lookup"><span data-stu-id="94699-203">Create the layout</span></span>

<span data-ttu-id="94699-204">La disposition fournit un moyen ordonné de placer des éléments d’interface utilisateur, et gère également la taille et la position de ces éléments quand une interface utilisateur est redimensionnée.</span><span class="sxs-lookup"><span data-stu-id="94699-204">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="94699-205">En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :</span><span class="sxs-lookup"><span data-stu-id="94699-205">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="94699-206"><xref:System.Windows.Controls.Canvas>-Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants à l’aide de coordonnées relatives à la zone de canevas.</span><span class="sxs-lookup"><span data-stu-id="94699-206"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="94699-207"><xref:System.Windows.Controls.DockPanel>: Définit une zone dans laquelle vous pouvez réorganiser les éléments enfants horizontalement ou verticalement, l’un par rapport à l’autre.</span><span class="sxs-lookup"><span data-stu-id="94699-207"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="94699-208"><xref:System.Windows.Controls.Grid>-Définit une zone de grille flexible composée de colonnes et de lignes.</span><span class="sxs-lookup"><span data-stu-id="94699-208"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="94699-209"><xref:System.Windows.Controls.StackPanel>-Réorganise les éléments enfants en une seule ligne qui peut être orientée horizontalement ou verticalement.</span><span class="sxs-lookup"><span data-stu-id="94699-209"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="94699-210"><xref:System.Windows.Controls.VirtualizingStackPanel>-Réorganise et virtualise le contenu sur une seule ligne orientée horizontalement ou verticalement.</span><span class="sxs-lookup"><span data-stu-id="94699-210"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="94699-211"><xref:System.Windows.Controls.WrapPanel>-Positionne les éléments enfants dans un ordre séquentiel de gauche à droite, en fractionnant le contenu à la ligne suivante au bord de la zone conteneur.</span><span class="sxs-lookup"><span data-stu-id="94699-211"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="94699-212">Le classement suivant se produit de manière séquentielle de haut en bas ou de droite à gauche, selon la valeur de la propriété orientation.</span><span class="sxs-lookup"><span data-stu-id="94699-212">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="94699-213">Chacun de ces contrôles de disposition prend en charge un type particulier de disposition pour ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="94699-213">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="94699-214">`ExpenseIt`les pages peuvent être redimensionnées et chaque page possède des éléments disposés horizontalement et verticalement en même temps que d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="94699-214">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="94699-215">Dans cet exemple, <xref:System.Windows.Controls.Grid> est utilisé comme élément de disposition pour l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-215">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="94699-216">Pour plus d’informations sur les <xref:System.Windows.Controls.Panel> éléments, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="94699-216">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="94699-217">Pour plus d’informations sur la disposition, consultez [disposition](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="94699-217">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="94699-218">Dans cette section, vous créez une table à une seule colonne avec trois lignes et une marge de 10 pixels en ajoutant des définitions de colonne et de ligne au <xref:System.Windows.Controls.Grid> dans *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="94699-218">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="94699-219">Dans *`ExpenseItHome.xaml`* , affectez <xref:System.Windows.FrameworkElement.Margin%2A> à la propriété de l’élément la valeur <xref:System.Windows.Controls.Grid> « 10, 0, 10, 10 », qui correspond aux marges gauche, haut, droit et bas :</span><span class="sxs-lookup"><span data-stu-id="94699-219">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="94699-220">Vous pouvez également définir les valeurs de **marge** dans la fenêtre **Propriétés** , sous la catégorie **disposition** :</span><span class="sxs-lookup"><span data-stu-id="94699-220">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valeurs de marge dans Fenêtre Propriétés](./media/properties-margin.png)

2. <span data-ttu-id="94699-222">Ajoutez le code XAML suivant entre les <xref:System.Windows.Controls.Grid> balises pour créer les définitions de ligne et de colonne :</span><span class="sxs-lookup"><span data-stu-id="94699-222">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="94699-223">La <xref:System.Windows.Controls.RowDefinition.Height%2A> valeur de deux lignes est définie sur, ce qui <xref:System.Windows.GridLength.Auto%2A> signifie que les lignes sont dimensionnées en fonction du contenu des lignes.</span><span class="sxs-lookup"><span data-stu-id="94699-223">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="94699-224">La valeur par défaut <xref:System.Windows.Controls.RowDefinition.Height%2A> est le <xref:System.Windows.GridUnitType.Star> dimensionnement, ce qui signifie que la hauteur de ligne est une proportion pondérée de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="94699-224">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="94699-225">Par exemple, si deux lignes ont chacune une <xref:System.Windows.Controls.RowDefinition.Height%2A> de « \* », elles ont chacune une hauteur qui correspond à la moitié de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="94699-225">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="94699-226">Votre <xref:System.Windows.Controls.Grid> doit maintenant contenir le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="94699-226">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="94699-227">Ajouter des contrôles</span><span class="sxs-lookup"><span data-stu-id="94699-227">Add controls</span></span>

<span data-ttu-id="94699-228">Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’origine pour afficher une liste de personnes, dans laquelle vous sélectionnez une personne pour afficher son rapport de frais.</span><span class="sxs-lookup"><span data-stu-id="94699-228">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="94699-229">Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application.</span><span class="sxs-lookup"><span data-stu-id="94699-229">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="94699-230">Pour plus d’informations, consultez [Contrôles](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="94699-230">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="94699-231">Pour créer cette interface utilisateur, vous allez ajouter les éléments suivants à *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="94699-231">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="94699-232">A <xref:System.Windows.Controls.ListBox> (pour la liste des personnes).</span><span class="sxs-lookup"><span data-stu-id="94699-232">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="94699-233"><xref:System.Windows.Controls.Label>(Pour l’en-tête de liste).</span><span class="sxs-lookup"><span data-stu-id="94699-233">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="94699-234">A <xref:System.Windows.Controls.Button> (pour afficher la note de frais de la personne sélectionnée dans la liste).</span><span class="sxs-lookup"><span data-stu-id="94699-234">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="94699-235">Chaque contrôle est placé dans une ligne du <xref:System.Windows.Controls.Grid> en définissant la <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriété jointe.</span><span class="sxs-lookup"><span data-stu-id="94699-235">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="94699-236">Pour plus d’informations sur les propriétés jointes, consultez [vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="94699-236">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="94699-237">Dans *`ExpenseItHome.xaml`* , ajoutez le code XAML suivant entre les <xref:System.Windows.Controls.Grid> Balises :</span><span class="sxs-lookup"><span data-stu-id="94699-237">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="94699-238">Vous pouvez également créer les contrôles en les faisant glisser de la fenêtre **boîte à outils** vers la fenêtre de conception, puis en définissant leurs propriétés dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="94699-238">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="94699-239">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-239">Build and run the application.</span></span>

    <span data-ttu-id="94699-240">L’illustration suivante montre les contrôles que vous avez créés :</span><span class="sxs-lookup"><span data-stu-id="94699-240">The following illustration shows the controls you created:</span></span>

![Exemple d’instantané ExpenseIt l’affichage d’une liste de noms](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="94699-242">Ajouter une image et un titre</span><span class="sxs-lookup"><span data-stu-id="94699-242">Add an image and a title</span></span>

<span data-ttu-id="94699-243">Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’hébergement avec une image et un titre de page.</span><span class="sxs-lookup"><span data-stu-id="94699-243">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="94699-244">Dans *`ExpenseItHome.xaml`* , ajoutez une autre colonne au <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> avec un <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixels au fixe :</span><span class="sxs-lookup"><span data-stu-id="94699-244">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="94699-245">Ajoutez une autre ligne au <xref:System.Windows.Controls.Grid.RowDefinitions%2A> , pour un total de quatre lignes :</span><span class="sxs-lookup"><span data-stu-id="94699-245">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="94699-246">Déplacez les contrôles vers la deuxième colonne en affectant <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> à la propriété la valeur 1 dans chacun des trois contrôles (Border, ListBox et Button).</span><span class="sxs-lookup"><span data-stu-id="94699-246">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="94699-247">Déplacez chaque contrôle d’une ligne vers le haut en incrémentant sa <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valeur de 1 pour chacun des trois contrôles (Border, ListBox et Button) et pour l’élément Border.</span><span class="sxs-lookup"><span data-stu-id="94699-247">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="94699-248">Le code XAML des trois contrôles se présente désormais comme suit :</span><span class="sxs-lookup"><span data-stu-id="94699-248">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="94699-249">Affectez <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> à la propriété le *watermark.png* fichier image, en ajoutant le code XAML suivant entre `<Grid>` les `</Grid>` balises et :</span><span class="sxs-lookup"><span data-stu-id="94699-249">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="94699-250">Avant l' <xref:System.Windows.Controls.Border> élément, ajoutez un <xref:System.Windows.Controls.Label> avec le contenu « afficher la note de frais ».</span><span class="sxs-lookup"><span data-stu-id="94699-250">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="94699-251">Cette étiquette est le titre de la page.</span><span class="sxs-lookup"><span data-stu-id="94699-251">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="94699-252">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-252">Build and run the application.</span></span>

<span data-ttu-id="94699-253">L’illustration suivante montre les résultats de ce que vous venez d’ajouter :</span><span class="sxs-lookup"><span data-stu-id="94699-253">The following illustration shows the results of what you just added:</span></span>

![Capture d’écran de l’exemple ExpenseIt le nouvel arrière-plan d’image et le titre de la page](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="94699-255">Ajouter du code pour gérer les événements</span><span class="sxs-lookup"><span data-stu-id="94699-255">Add code to handle events</span></span>

1. <span data-ttu-id="94699-256">Dans *`ExpenseItHome.xaml`* , ajoutez un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements à l' <xref:System.Windows.Controls.Button> élément.</span><span class="sxs-lookup"><span data-stu-id="94699-256">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="94699-257">Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements simple](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="94699-257">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="94699-258">Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="94699-258">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="94699-259">Ajoutez le code suivant à la `ExpenseItHome` classe pour ajouter un gestionnaire d’événements de clic sur un bouton.</span><span class="sxs-lookup"><span data-stu-id="94699-259">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="94699-260">Le gestionnaire d’événements ouvre la page **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="94699-260">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="94699-261">Créer l’interface utilisateur pour ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="94699-261">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="94699-262">*ExpenseReportPage. Xaml* affiche la note de frais pour la personne sélectionnée sur la **`ExpenseItHome`** page.</span><span class="sxs-lookup"><span data-stu-id="94699-262">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="94699-263">Dans cette section, vous allez créer l’interface utilisateur pour **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="94699-263">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="94699-264">Vous ajouterez également des couleurs d’arrière-plan et de remplissage aux différents éléments de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94699-264">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="94699-265">Ouvrez *ExpenseReportPage. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-265">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="94699-266">Ajoutez le code XAML suivant entre les <xref:System.Windows.Controls.Grid> Balises :</span><span class="sxs-lookup"><span data-stu-id="94699-266">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="94699-267">Cette interface utilisateur est similaire à *`ExpenseItHome.xaml`* , sauf que les données de rapport s’affichent dans un <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="94699-267">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="94699-268">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-268">Build and run the application.</span></span>

4. <span data-ttu-id="94699-269">Sélectionnez le bouton **Afficher** .</span><span class="sxs-lookup"><span data-stu-id="94699-269">Select the **View** button.</span></span>

    <span data-ttu-id="94699-270">La page de note de frais s’affiche.</span><span class="sxs-lookup"><span data-stu-id="94699-270">The expense report page appears.</span></span> <span data-ttu-id="94699-271">Notez également que le bouton de navigation précédent est activé.</span><span class="sxs-lookup"><span data-stu-id="94699-271">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="94699-272">L’illustration suivante montre les éléments d’interface utilisateur ajoutés à *ExpenseReportPage. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-272">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Exemple de capture d’écran expenseux montrant l’interface utilisateur qui vient d’être créée pour ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="94699-274">Contrôles de style</span><span class="sxs-lookup"><span data-stu-id="94699-274">Style controls</span></span>

<span data-ttu-id="94699-275">L’apparence de différents éléments est souvent la même pour tous les éléments du même type dans une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94699-275">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="94699-276">L’interface utilisateur utilise des [styles](../../../desktop-wpf/fundamentals/styles-templates-overview.md) pour rendre les apparences réutilisables sur plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="94699-276">UI uses [styles](../../../desktop-wpf/fundamentals/styles-templates-overview.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="94699-277">La réutilisabilité des styles permet de simplifier la création et la gestion XAML.</span><span class="sxs-lookup"><span data-stu-id="94699-277">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="94699-278">Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="94699-278">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="94699-279">Ouvrez *application. Xaml* ou *app. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-279">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="94699-280">Ajoutez le code XAML suivant entre les <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> Balises :</span><span class="sxs-lookup"><span data-stu-id="94699-280">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="94699-281">Ce code XAML ajoute les styles suivants :</span><span class="sxs-lookup"><span data-stu-id="94699-281">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="94699-282">`headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="94699-282">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="94699-283">`labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="94699-283">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="94699-284">`columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="94699-284">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="94699-285">`listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste.</span><span class="sxs-lookup"><span data-stu-id="94699-285">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="94699-286">`listHeaderTextStyle`: Pour mettre en forme l’en-tête de liste <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="94699-286">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="94699-287">`buttonStyle`: Pour mettre en forme le <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml` .</span><span class="sxs-lookup"><span data-stu-id="94699-287">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="94699-288">Notez que les styles sont des ressources et des enfants de l' <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> élément Property.</span><span class="sxs-lookup"><span data-stu-id="94699-288">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="94699-289">À cet emplacement, les styles sont appliqués à tous les éléments d’une application.</span><span class="sxs-lookup"><span data-stu-id="94699-289">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="94699-290">Pour obtenir un exemple d’utilisation de ressources dans une application .NET, consultez [utiliser des ressources d’application](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="94699-290">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="94699-291">Dans *`ExpenseItHome.xaml`* , remplacez tout ce qui se trouve entre les <xref:System.Windows.Controls.Grid> éléments par le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="94699-291">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="94699-292">Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles.</span><span class="sxs-lookup"><span data-stu-id="94699-292">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="94699-293">Par exemple, l' `headerTextStyle` est appliqué à l' « afficher la note de frais » <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="94699-293">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="94699-294">Ouvrez *ExpenseReportPage. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-294">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="94699-295">Remplacez tout ce qui se trouve entre les <xref:System.Windows.Controls.Grid> éléments par le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="94699-295">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="94699-296">Ce code XAML ajoute des styles <xref:System.Windows.Controls.Label> aux <xref:System.Windows.Controls.Border> éléments et.</span><span class="sxs-lookup"><span data-stu-id="94699-296">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="94699-297">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-297">Build and run the application.</span></span> <span data-ttu-id="94699-298">L’apparence de la fenêtre est la même que précédemment.</span><span class="sxs-lookup"><span data-stu-id="94699-298">The window appearance is the same as previously.</span></span>

    ![Exemple de capture d’écran ExpenseIt avec la même apparence que dans la dernière section.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="94699-300">Fermez l’application pour revenir à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94699-300">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="94699-301">Lier des données à un contrôle</span><span class="sxs-lookup"><span data-stu-id="94699-301">Bind data to a control</span></span>

<span data-ttu-id="94699-302">Dans cette section, vous allez créer les données XML liées à différents contrôles.</span><span class="sxs-lookup"><span data-stu-id="94699-302">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="94699-303">Dans *`ExpenseItHome.xaml`* , après l’élément d’ouverture <xref:System.Windows.Controls.Grid> , ajoutez le code XAML suivant pour créer un <xref:System.Windows.Data.XmlDataProvider> qui contient les données pour chaque personne :</span><span class="sxs-lookup"><span data-stu-id="94699-303">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="94699-304">Les données sont créées en tant que <xref:System.Windows.Controls.Grid> ressource.</span><span class="sxs-lookup"><span data-stu-id="94699-304">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="94699-305">Normalement, ces données sont chargées en tant que fichier, mais pour des raisons de simplicité, les données sont ajoutées Inline.</span><span class="sxs-lookup"><span data-stu-id="94699-305">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="94699-306">Dans l' `<Grid.Resources>` élément, ajoutez l' `<xref:System.Windows.DataTemplate>` élément suivant, qui définit comment afficher les données dans le <xref:System.Windows.Controls.ListBox> , après l' `<XmlDataProvider>` élément :</span><span class="sxs-lookup"><span data-stu-id="94699-306">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="94699-307">Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../data/data-templating-overview.md)des modèles de données.</span><span class="sxs-lookup"><span data-stu-id="94699-307">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="94699-308">Remplacez le existant <xref:System.Windows.Controls.ListBox> par le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="94699-308">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="94699-309">Ce code XAML lie la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de <xref:System.Windows.Controls.ListBox> à la source de données et applique le modèle de données en tant que <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .</span><span class="sxs-lookup"><span data-stu-id="94699-309">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="94699-310">Connecter des données à des contrôles</span><span class="sxs-lookup"><span data-stu-id="94699-310">Connect data to controls</span></span>

<span data-ttu-id="94699-311">Ensuite, vous allez ajouter du code pour récupérer le nom qui est sélectionné dans la **`ExpenseItHome`** page et le passer au constructeur de **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="94699-311">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="94699-312">**ExpenseReportPage** définit son contexte de données avec l’élément passé, à savoir à quoi les contrôles définis dans *ExpenseReportPage. Xaml* se lient.</span><span class="sxs-lookup"><span data-stu-id="94699-312">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="94699-313">Ouvrez *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="94699-313">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="94699-314">Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="94699-314">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="94699-315">Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="94699-315">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="94699-316">Modifiez le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements pour appeler le nouveau constructeur en passant les données de la note de frais de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="94699-316">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="94699-317">Données de style avec des modèles de données</span><span class="sxs-lookup"><span data-stu-id="94699-317">Style data with data templates</span></span>

<span data-ttu-id="94699-318">Dans cette section, vous allez mettre à jour l’interface utilisateur pour chaque élément des listes liées aux données à l’aide de modèles de données.</span><span class="sxs-lookup"><span data-stu-id="94699-318">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="94699-319">Ouvrez *ExpenseReportPage. Xaml*.</span><span class="sxs-lookup"><span data-stu-id="94699-319">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="94699-320">Liez le contenu des éléments « Name » et « Department » <xref:System.Windows.Controls.Label> à la propriété de source de données appropriée.</span><span class="sxs-lookup"><span data-stu-id="94699-320">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="94699-321">Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="94699-321">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="94699-322">Après l’élément d’ouverture <xref:System.Windows.Controls.Grid> , ajoutez les modèles de données suivants, qui définissent comment afficher les données de note de frais :</span><span class="sxs-lookup"><span data-stu-id="94699-322">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="94699-323">Remplacez les <xref:System.Windows.Controls.DataGridTextColumn> éléments par <xref:System.Windows.Controls.DataGridTemplateColumn> sous l' <xref:System.Windows.Controls.DataGrid> élément et appliquez-leur les modèles.</span><span class="sxs-lookup"><span data-stu-id="94699-323">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="94699-324">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="94699-324">Build and run the application.</span></span>

6. <span data-ttu-id="94699-325">Sélectionnez une personne, puis cliquez sur le bouton **Afficher** .</span><span class="sxs-lookup"><span data-stu-id="94699-325">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="94699-326">L’illustration suivante montre les deux pages de l' `ExpenseIt` application avec les contrôles, la disposition, les styles, la liaison de données et les modèles de données appliqués :</span><span class="sxs-lookup"><span data-stu-id="94699-326">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Les deux pages de l’application indiquent la liste des noms et une note de frais.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="94699-328">Cet exemple illustre une fonctionnalité spécifique de WPF et ne suit pas toutes les méthodes recommandées pour la sécurité, la localisation et l’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="94699-328">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="94699-329">Pour une couverture complète de WPF et des meilleures pratiques en matière de développement d’applications .NET, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="94699-329">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="94699-330">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="94699-330">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="94699-331">Sécurité</span><span class="sxs-lookup"><span data-stu-id="94699-331">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="94699-332">Globalisation et localisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="94699-332">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="94699-333">Performances WPF</span><span class="sxs-lookup"><span data-stu-id="94699-333">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="94699-334">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="94699-334">Next steps</span></span>

<span data-ttu-id="94699-335">Dans cette procédure pas à pas, vous avez appris un certain nombre de techniques pour la création d’une interface utilisateur à l’aide d’Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="94699-335">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="94699-336">Vous devez maintenant avoir une compréhension de base des blocs de construction d’une application .NET liée aux données.</span><span class="sxs-lookup"><span data-stu-id="94699-336">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="94699-337">Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="94699-337">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="94699-338">Architecture WPF</span><span class="sxs-lookup"><span data-stu-id="94699-338">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="94699-339">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="94699-339">XAML overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="94699-340">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="94699-340">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="94699-341">Disposition</span><span class="sxs-lookup"><span data-stu-id="94699-341">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="94699-342">Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="94699-342">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="94699-343">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="94699-343">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="94699-344">Contrôles</span><span class="sxs-lookup"><span data-stu-id="94699-344">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="94699-345">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="94699-345">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="94699-346">Graphisme et multimédia</span><span class="sxs-lookup"><span data-stu-id="94699-346">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="94699-347">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="94699-347">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="94699-348">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94699-348">See also</span></span>

- [<span data-ttu-id="94699-349">Vue d’ensemble des panneaux</span><span class="sxs-lookup"><span data-stu-id="94699-349">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="94699-350">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="94699-350">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="94699-351">Générer une application WPF</span><span class="sxs-lookup"><span data-stu-id="94699-351">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="94699-352">Styles et modèles</span><span class="sxs-lookup"><span data-stu-id="94699-352">Styles and templates</span></span>](../controls/styles-and-templates.md)
