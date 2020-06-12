---
title: Créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio pour Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 3a107fff2fd6aef5e06d9af3eac334fbf5688fa5
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713741"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="09ebe-103">Didacticiel : créer une bibliothèque de .NET Standard à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="09ebe-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="09ebe-104">Dans ce didacticiel, vous allez créer une bibliothèque de classes simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="09ebe-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span> <span data-ttu-id="09ebe-105">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) pour pouvoir l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="09ebe-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="09ebe-106">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="09ebe-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="09ebe-107">Une bibliothèque de classes qui cible .NET Standard 2,1 peut être utilisée par une application qui cible toute implémentation .NET qui prend en charge la version 2,1 de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="09ebe-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="09ebe-108">Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="09ebe-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="09ebe-109">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="09ebe-109">Your feedback is highly valued.</span></span> <span data-ttu-id="09ebe-110">Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="09ebe-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="09ebe-111">Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="09ebe-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="09ebe-112">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/41/index.html).</span><span class="sxs-lookup"><span data-stu-id="09ebe-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="09ebe-113">Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** sur l’écran d’accueil, qui vous amène à la [page Web de la communauté des développeurs Visual Studio pour Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="09ebe-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09ebe-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="09ebe-114">Prerequisites</span></span>

* <span data-ttu-id="09ebe-115">[Installez Visual Studio pour Mac version 8,6 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="09ebe-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="09ebe-116">Sélectionnez l’option d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09ebe-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="09ebe-117">L’installation de Xamarin est facultative pour le développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09ebe-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="09ebe-118">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="09ebe-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="09ebe-119">[Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="09ebe-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="09ebe-120">[Versions MacOS prises en charge](../install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="09ebe-120">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="09ebe-121">[Versions de .net Core prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="09ebe-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="09ebe-122">Créer une solution avec un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="09ebe-122">Create a solution with a class library project</span></span>

<span data-ttu-id="09ebe-123">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="09ebe-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="09ebe-124">Créez une solution et un projet de bibliothèque de classes dans la solution.</span><span class="sxs-lookup"><span data-stu-id="09ebe-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="09ebe-125">Vous ajouterez ultérieurement des projets connexes à la même solution.</span><span class="sxs-lookup"><span data-stu-id="09ebe-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="09ebe-126">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="09ebe-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="09ebe-127">Dans la fenêtre Démarrer, sélectionnez **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="09ebe-128">Dans la boîte de dialogue **nouveau projet** , sous le nœud **multiplateforme** , sélectionnez **bibliothèque**, puis sélectionnez le modèle de **bibliothèque .NET standard** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Boîte de dialogue Nouveau projet":::

1. <span data-ttu-id="09ebe-130">Dans la boîte de dialogue **configurer votre nouvelle bibliothèque de .NET standard** , choisissez « .NET standard 2,1 », puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Choisir .NET Standard 2,1":::

1. <span data-ttu-id="09ebe-132">Nommez le projet « StringLibrary » et la solution « ClassLibraryProjects ».</span><span class="sxs-lookup"><span data-stu-id="09ebe-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="09ebe-133">Laissez **l’option créer un répertoire de projet dans le répertoire de la solution** sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="09ebe-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="09ebe-134">Sélectionnez **Create** (Créer).</span><span class="sxs-lookup"><span data-stu-id="09ebe-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Options de la boîte de dialogue Nouveau projet dans Visual Studio pour Mac":::

1. <span data-ttu-id="09ebe-136">Dans le menu principal, sélectionnez **Afficher**  >  les**Pad**  >  **solution**, puis sélectionnez l’icône d’ancrage pour maintenir le pavé ouvert.</span><span class="sxs-lookup"><span data-stu-id="09ebe-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Icône d’ancrage du panneau solution":::

1. <span data-ttu-id="09ebe-138">Dans le panneau **solution** , développez le `StringLibrary` nœud pour afficher le fichier de classe fourni par le modèle, *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="09ebe-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="09ebe-139"><kbd>CTRL</kbd>+ cliquez sur le fichier, sélectionnez **Renommer** dans le menu contextuel, puis renommez le fichier *StringLibrary.cs*.</span><span class="sxs-lookup"><span data-stu-id="09ebe-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="09ebe-140">Ouvrez le fichier et remplacez le contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="09ebe-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="09ebe-141">Appuyez sur <kbd>⌘</kbd><kbd>s</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>) pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="09ebe-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="09ebe-142">Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="09ebe-143">Sélectionnez le bouton **Sortie de la build**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Marge inférieure de l’IDE Visual Studio pour Mac montrant le bouton Erreurs":::

1. <span data-ttu-id="09ebe-145">**Build**  >  Dans le menu, sélectionnez Générer**générer tout** .</span><span class="sxs-lookup"><span data-stu-id="09ebe-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="09ebe-146">La solution se génère.</span><span class="sxs-lookup"><span data-stu-id="09ebe-146">The solution builds.</span></span> <span data-ttu-id="09ebe-147">Le panneau de sortie de la build indique que la build a réussi.</span><span class="sxs-lookup"><span data-stu-id="09ebe-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Volet Sortie de la build Visual Studio pour Mac du panneau Erreurs avec le message de réussite de la build":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="09ebe-149">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="09ebe-149">Add a console app to the solution</span></span>

<span data-ttu-id="09ebe-150">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="09ebe-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="09ebe-151">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="09ebe-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="09ebe-152">Dans le panneau **solutions** , cliquez sur la solution en <kbd>appuyant sur la touche Ctrl</kbd> `ClassLibraryProjects` .</span><span class="sxs-lookup"><span data-stu-id="09ebe-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="09ebe-153">Ajoutez un nouveau projet d' **application console** en sélectionnant le modèle à partir des modèles d’application **Web et console**  >  **App** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="09ebe-154">Sélectionnez **.net Core 3,1** comme **Framework cible** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="09ebe-155">Nommez le projet **vitrine**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="09ebe-156">Sélectionnez **Créer** pour créer le projet dans la solution.</span><span class="sxs-lookup"><span data-stu-id="09ebe-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Ajouter un projet de démonstration":::

1. <span data-ttu-id="09ebe-158">Ouvrez le fichier *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="09ebe-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="09ebe-159">Remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="09ebe-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="09ebe-160">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="09ebe-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="09ebe-161">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="09ebe-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="09ebe-162">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="09ebe-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="09ebe-163">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="09ebe-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="09ebe-164">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="09ebe-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="09ebe-165">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="09ebe-165">Add a project reference</span></span>

<span data-ttu-id="09ebe-166">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="09ebe-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="09ebe-167">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="09ebe-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="09ebe-168">Dans le panneau **solutions** , <kbd>cliquez</kbd>sur le nœud **dépendances** du nouveau projet **Showcase** .</span><span class="sxs-lookup"><span data-stu-id="09ebe-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="09ebe-169">Dans le menu contextuel, sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="09ebe-170">Dans la boîte de dialogue **références** , sélectionnez **StringLibrary** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09ebe-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="09ebe-171">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="09ebe-171">Run the app</span></span>

1. <span data-ttu-id="09ebe-172"><kbd>ctrl</kbd>cliquez sur le projet Showcase et sélectionnez Exécuter le **projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="09ebe-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="09ebe-173">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="09ebe-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Fenêtre de console Visual Studio pour Mac montrant votre application en cours d’exécution":::

## <a name="additional-resources"></a><span data-ttu-id="09ebe-175">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="09ebe-175">Additional resources</span></span>

* [<span data-ttu-id="09ebe-176">Développer des bibliothèques avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="09ebe-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="09ebe-177">[.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="09ebe-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="09ebe-178">Notes de publication de Visual Studio 2019 pour Mac</span><span class="sxs-lookup"><span data-stu-id="09ebe-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="09ebe-179">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="09ebe-179">Next steps</span></span>

<span data-ttu-id="09ebe-180">Dans ce didacticiel, vous avez créé une solution et un projet de bibliothèque, et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="09ebe-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="09ebe-181">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="09ebe-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09ebe-182">Tester une bibliothèque .NET Standard avec .NET Core à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="09ebe-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
