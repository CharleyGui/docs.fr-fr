---
title: Créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac.
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599297"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a><span data-ttu-id="af447-103">Didacticiel : créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="af447-103">Tutorial: Create a .NET class library using Visual Studio for Mac</span></span>

<span data-ttu-id="af447-104">Dans ce didacticiel, vous allez créer une bibliothèque de classes qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="af447-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span>

<span data-ttu-id="af447-105">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="af447-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="af447-106">Si la bibliothèque cible .NET Standard 2,0, elle peut être appelée par n’importe quelle implémentation .NET (y compris .NET Framework) qui prend en charge .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="af447-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="af447-107">Si la bibliothèque cible .NET 5, elle peut être appelée par n’importe quelle application qui cible .NET 5.</span><span class="sxs-lookup"><span data-stu-id="af447-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="af447-108">Ce didacticiel montre comment cibler .NET 5.</span><span class="sxs-lookup"><span data-stu-id="af447-108">This tutorial shows how to target .NET 5.</span></span>

> [!NOTE]
> <span data-ttu-id="af447-109">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="af447-109">Your feedback is highly valued.</span></span> <span data-ttu-id="af447-110">Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="af447-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="af447-111">Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="af447-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="af447-112">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://aka.ms/feedback/report?space=41).</span><span class="sxs-lookup"><span data-stu-id="af447-112">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> - <span data-ttu-id="af447-113">Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** sur l’écran d’accueil, qui vous amène à la [page Web de la communauté des développeurs Visual Studio pour Mac](https://aka.ms/feedback/suggest?space=41).</span><span class="sxs-lookup"><span data-stu-id="af447-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af447-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="af447-114">Prerequisites</span></span>

* <span data-ttu-id="af447-115">[Installez Visual Studio pour Mac version 8,8 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="af447-115">[Install Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="af447-116">Sélectionnez l’option d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af447-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="af447-117">L’installation de Xamarin est facultative pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="af447-117">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="af447-118">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="af447-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="af447-119">[Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="af447-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="af447-120">[Versions MacOS prises en charge](../install/macos.md).</span><span class="sxs-lookup"><span data-stu-id="af447-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="af447-121">[Versions .net prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="af447-121">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="af447-122">Créer une solution avec un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="af447-122">Create a solution with a class library project</span></span>

<span data-ttu-id="af447-123">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="af447-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="af447-124">Créez une solution et un projet de bibliothèque de classes dans la solution.</span><span class="sxs-lookup"><span data-stu-id="af447-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="af447-125">Vous ajouterez ultérieurement des projets connexes à la même solution.</span><span class="sxs-lookup"><span data-stu-id="af447-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="af447-126">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="af447-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="af447-127">Dans la fenêtre Démarrer, sélectionnez **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="af447-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="af447-128">Dans la boîte **de dialogue Choisir un modèle pour votre nouveau projet** , sélectionnez Bibliothèque de classes **Web et console**  >  **Library**  >  **Class Library**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="af447-128">In the **Choose a template for your new project** dialog select **Web and Console** > **Library** > **Class Library**, and then select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Boîte de dialogue Nouveau projet":::

1. <span data-ttu-id="af447-130">Dans la boîte de dialogue **configurer votre nouvelle bibliothèque de classes** , choisissez **.net 5,0**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="af447-130">In the **Configure your new Class Library** dialog, choose **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="af447-131">Nommez le projet « StringLibrary » et la solution « ClassLibraryProjects ».</span><span class="sxs-lookup"><span data-stu-id="af447-131">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="af447-132">Laissez **l’option créer un répertoire de projet dans le répertoire de la solution** sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="af447-132">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="af447-133">Sélectionnez **Create** (Créer).</span><span class="sxs-lookup"><span data-stu-id="af447-133">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Options de la boîte de dialogue Nouveau projet dans Visual Studio pour Mac":::

1. <span data-ttu-id="af447-135">Dans le menu principal, sélectionnez **Afficher**  >  la **solution**, puis sélectionnez l’icône d’ancrage pour maintenir le pavé ouvert.</span><span class="sxs-lookup"><span data-stu-id="af447-135">From the main menu, select **View** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Icône d’ancrage du panneau solution":::

1. <span data-ttu-id="af447-137">Dans le panneau **solution** , développez le `StringLibrary` nœud pour afficher le fichier de classe fourni par le modèle, *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="af447-137">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="af447-138"><kbd>CTRL</kbd>+ cliquez sur le fichier, sélectionnez **Renommer** dans le menu contextuel, puis renommez le fichier *StringLibrary.cs*.</span><span class="sxs-lookup"><span data-stu-id="af447-138"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="af447-139">Ouvrez le fichier et remplacez le contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="af447-139">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="af447-140">Appuyez sur <kbd>⌘</kbd><kbd>s</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>) pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="af447-140">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="af447-141">Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**.</span><span class="sxs-lookup"><span data-stu-id="af447-141">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="af447-142">Sélectionnez le bouton **Sortie de la build**.</span><span class="sxs-lookup"><span data-stu-id="af447-142">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Marge inférieure de l’IDE Visual Studio pour Mac montrant le bouton Erreurs":::

1. <span data-ttu-id="af447-144">**Build**  >  Dans le menu, sélectionnez Générer **générer tout** .</span><span class="sxs-lookup"><span data-stu-id="af447-144">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="af447-145">La solution se génère.</span><span class="sxs-lookup"><span data-stu-id="af447-145">The solution builds.</span></span> <span data-ttu-id="af447-146">Le panneau de sortie de la build indique que la build a réussi.</span><span class="sxs-lookup"><span data-stu-id="af447-146">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Volet Sortie de la build Visual Studio pour Mac du panneau Erreurs avec le message de réussite de la build":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="af447-148">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="af447-148">Add a console app to the solution</span></span>

<span data-ttu-id="af447-149">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="af447-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="af447-150">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="af447-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="af447-151">Dans le panneau **solutions** , cliquez sur la solution en <kbd>appuyant sur la touche Ctrl</kbd> `ClassLibraryProjects` .</span><span class="sxs-lookup"><span data-stu-id="af447-151">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="af447-152">Ajoutez un nouveau projet d' **application console** en sélectionnant le modèle à partir des modèles d’application **Web et console**  >  **App** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="af447-152">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="af447-153">Sélectionnez **.net 5,0** comme **Framework cible** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="af447-153">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="af447-154">Nommez le projet **vitrine**.</span><span class="sxs-lookup"><span data-stu-id="af447-154">Name the project **ShowCase**.</span></span> <span data-ttu-id="af447-155">Sélectionnez **Créer** pour créer le projet dans la solution.</span><span class="sxs-lookup"><span data-stu-id="af447-155">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Ajouter un projet de démonstration":::

1. <span data-ttu-id="af447-157">Ouvrez le fichier *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="af447-157">Open the *Program.cs* file.</span></span> <span data-ttu-id="af447-158">Remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="af447-158">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="af447-159">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="af447-159">The program prompts the user to enter a string.</span></span> <span data-ttu-id="af447-160">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="af447-160">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="af447-161">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="af447-161">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="af447-162">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="af447-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="af447-163">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af447-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="af447-164">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="af447-164">Add a project reference</span></span>

<span data-ttu-id="af447-165">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="af447-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="af447-166">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="af447-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="af447-167">Dans le panneau **solutions** , <kbd>cliquez</kbd>sur le nœud **dépendances** du nouveau projet **Showcase** .</span><span class="sxs-lookup"><span data-stu-id="af447-167">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="af447-168">Dans le menu contextuel, sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="af447-168">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="af447-169">Dans la boîte de dialogue **références** , sélectionnez **StringLibrary** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="af447-169">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="af447-170">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="af447-170">Run the app</span></span>

1. <span data-ttu-id="af447-171"><kbd>ctrl</kbd>cliquez sur le projet **Showcase** et sélectionnez **exécuter le projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="af447-171"><kbd>ctrl</kbd>-click the **ShowCase** project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="af447-172">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="af447-172">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Fenêtre de console Visual Studio pour Mac montrant votre application en cours d’exécution":::

## <a name="additional-resources"></a><span data-ttu-id="af447-174">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="af447-174">Additional resources</span></span>

* [<span data-ttu-id="af447-175">Développer des bibliothèques avec l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="af447-175">Develop libraries with the .NET CLI</span></span>](libraries.md)
* [<span data-ttu-id="af447-176">Notes de publication de Visual Studio 2019 pour Mac</span><span class="sxs-lookup"><span data-stu-id="af447-176">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)
* <span data-ttu-id="af447-177">[.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="af447-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="af447-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="af447-178">Next steps</span></span>

<span data-ttu-id="af447-179">Dans ce didacticiel, vous avez créé une solution et un projet de bibliothèque, et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="af447-179">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="af447-180">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="af447-180">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af447-181">Tester une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="af447-181">Test a .NET class library using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
