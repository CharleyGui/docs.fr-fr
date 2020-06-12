---
title: Créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701563"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="8915e-103">Didacticiel : créer une bibliothèque de .NET Standard à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8915e-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="8915e-104">Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="8915e-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="8915e-105">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) pour pouvoir l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="8915e-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="8915e-106">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="8915e-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="8915e-107">Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8915e-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="8915e-108">Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="8915e-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8915e-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8915e-109">Prerequisites</span></span>

- <span data-ttu-id="8915e-110">[Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="8915e-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="8915e-111">Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="8915e-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="8915e-112">Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="8915e-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="8915e-113">Créer une solution</span><span class="sxs-lookup"><span data-stu-id="8915e-113">Create a solution</span></span>

<span data-ttu-id="8915e-114">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="8915e-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="8915e-115">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="8915e-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="8915e-116">Vous ajouterez des projets connexes supplémentaires à la même solution.</span><span class="sxs-lookup"><span data-stu-id="8915e-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="8915e-117">Pour créer la solution vide :</span><span class="sxs-lookup"><span data-stu-id="8915e-117">To create the blank solution:</span></span>

1. <span data-ttu-id="8915e-118">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8915e-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="8915e-119">Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="8915e-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="8915e-120">Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="8915e-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="8915e-121">Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8915e-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="8915e-123">Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="8915e-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="8915e-124">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="8915e-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="8915e-125">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="8915e-125">Create a class library project</span></span>

1. <span data-ttu-id="8915e-126">Ajoutez un nouveau projet de bibliothèque de classes .NET Standard nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="8915e-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="8915e-127">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="8915e-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="8915e-128">Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="8915e-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="8915e-129">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="8915e-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="8915e-130">Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8915e-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="8915e-131">Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="8915e-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="8915e-132">Ensuite, choisissez **créer**.</span><span class="sxs-lookup"><span data-stu-id="8915e-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="8915e-133">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8915e-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="8915e-134">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8915e-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="8915e-135">La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="8915e-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="8915e-137">Si vous utilisez Visual Basic, effacez le texte dans la zone de texte **espace de noms racine** .</span><span class="sxs-lookup"><span data-stu-id="8915e-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="8915e-139">Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="8915e-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="8915e-140">Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) mot clé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="8915e-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="8915e-141">Remplacez le code dans la fenêtre de code pour *Class1.cs* ou *Class1. vb* par le code suivant, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="8915e-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="8915e-142">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="8915e-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="8915e-143">La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="8915e-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="8915e-144">Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="8915e-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="8915e-145">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="8915e-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="8915e-146">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="8915e-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="8915e-147">Dans la barre de menus, sélectionnez **générer**  >  **générer la solution** pour vérifier que le projet se compile sans erreur.</span><span class="sxs-lookup"><span data-stu-id="8915e-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="8915e-148">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="8915e-148">Add a console app to the solution</span></span>

<span data-ttu-id="8915e-149">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="8915e-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="8915e-150">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="8915e-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="8915e-151">Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.</span><span class="sxs-lookup"><span data-stu-id="8915e-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="8915e-152">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="8915e-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="8915e-153">Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="8915e-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="8915e-154">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="8915e-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="8915e-155">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8915e-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="8915e-156">Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="8915e-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="8915e-157">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="8915e-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="8915e-158">Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8915e-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="8915e-159">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="8915e-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="8915e-160">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8915e-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="8915e-161">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8915e-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="8915e-162">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="8915e-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="8915e-163">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="8915e-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="8915e-164">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="8915e-164">Add a project reference</span></span>

<span data-ttu-id="8915e-165">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="8915e-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="8915e-166">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="8915e-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="8915e-167">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `ShowCase` nœud **dépendances** du projet, puis sélectionnez **Ajouter une référence de projet**.</span><span class="sxs-lookup"><span data-stu-id="8915e-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Menu contextuel ajouter une référence dans Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="8915e-169">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez le projet **StringLibrary** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8915e-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="8915e-171">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="8915e-171">Run the app</span></span>

1. <span data-ttu-id="8915e-172">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="8915e-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="8915e-174">Appuyez sur <kbd>MAJ</kbd> + <kbd>F5</kbd> pour compiler et exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="8915e-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="8915e-176">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8915e-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Fenêtre de console avec la vitrine en cours d’exécution":::

## <a name="additional-resources"></a><span data-ttu-id="8915e-178">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8915e-178">Additional resources</span></span>

* [<span data-ttu-id="8915e-179">Développer des bibliothèques avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="8915e-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="8915e-180">[.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="8915e-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8915e-181">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8915e-181">Next steps</span></span>

<span data-ttu-id="8915e-182">Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8915e-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="8915e-183">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="8915e-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8915e-184">Tester une bibliothèque .NET Standard avec .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8915e-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
