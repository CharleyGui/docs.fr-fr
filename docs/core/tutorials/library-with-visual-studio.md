---
title: Créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 45a44dcd73e1abcc8dfd75cd54da5a2310f027c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118258"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="71de4-103">Didacticiel : créer une bibliothèque de .NET Standard à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71de4-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="71de4-104">Dans ce didacticiel, vous allez créer une bibliothèque de classes simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="71de4-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="71de4-105">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="71de4-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="71de4-106">Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="71de4-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="71de4-107">Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez la distribuer en tant que package NuGet ou en tant que composant fourni avec l’application qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="71de4-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71de4-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="71de4-108">Prerequisites</span></span>

- <span data-ttu-id="71de4-109">[Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="71de4-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="71de4-110">Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="71de4-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="71de4-111">Créer une solution</span><span class="sxs-lookup"><span data-stu-id="71de4-111">Create a solution</span></span>

<span data-ttu-id="71de4-112">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="71de4-113">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="71de4-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="71de4-114">Vous ajouterez des projets connexes supplémentaires à la même solution.</span><span class="sxs-lookup"><span data-stu-id="71de4-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="71de4-115">Pour créer la solution vide :</span><span class="sxs-lookup"><span data-stu-id="71de4-115">To create the blank solution:</span></span>

1. <span data-ttu-id="71de4-116">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71de4-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="71de4-117">Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="71de4-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="71de4-118">Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="71de4-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="71de4-119">Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="71de4-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="71de4-121">Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="71de4-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="71de4-122">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="71de4-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="71de4-123">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="71de4-123">Create a class library project</span></span>

1. <span data-ttu-id="71de4-124">Ajoutez un nouveau projet de bibliothèque de classes .NET Standard nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="71de4-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="71de4-125">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="71de4-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="71de4-126">Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="71de4-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="71de4-127">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="71de4-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="71de4-128">Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="71de4-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="71de4-129">Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="71de4-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="71de4-130">Ensuite, choisissez **créer**.</span><span class="sxs-lookup"><span data-stu-id="71de4-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="71de4-131">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="71de4-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="71de4-132">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="71de4-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="71de4-133">La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="71de4-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="71de4-135">Si vous utilisez Visual Basic, effacez le texte dans la zone de texte **espace de noms racine** .</span><span class="sxs-lookup"><span data-stu-id="71de4-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="71de4-137">Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="71de4-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="71de4-138">Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) mot clé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="71de4-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="71de4-139">Remplacez le code dans la fenêtre de code pour *Class1.cs*  ou *Class1. vb* par le code suivant, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="71de4-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="71de4-140">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="71de4-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="71de4-141">La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="71de4-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="71de4-142">Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="71de4-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="71de4-143">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="71de4-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="71de4-144">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="71de4-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="71de4-145">`StartsWithUpper` est implémenté en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) afin que vous puissiez l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="71de4-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="71de4-146">Dans la barre de menus, sélectionnez **générer**  >  **générer la solution** ou appuyez sur <kbd>CTRL</kbd> + <kbd>MAJ</kbd> + <kbd>B</kbd> pour vérifier que le projet se compile sans erreur.</span><span class="sxs-lookup"><span data-stu-id="71de4-146">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="71de4-147">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="71de4-147">Add a console app to the solution</span></span>

<span data-ttu-id="71de4-148">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="71de4-149">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="71de4-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="71de4-150">Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.</span><span class="sxs-lookup"><span data-stu-id="71de4-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="71de4-151">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="71de4-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="71de4-152">Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="71de4-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="71de4-153">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="71de4-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="71de4-154">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="71de4-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="71de4-155">Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="71de4-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="71de4-156">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="71de4-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="71de4-157">Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="71de4-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="71de4-158">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="71de4-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="71de4-159">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="71de4-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="71de4-160">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="71de4-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="71de4-161">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="71de4-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="71de4-162">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="71de4-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="71de4-163">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="71de4-163">Add a project reference</span></span>

<span data-ttu-id="71de4-164">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="71de4-165">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="71de4-166">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `ShowCase` nœud **dépendances** du projet, puis sélectionnez **Ajouter une référence de projet**.</span><span class="sxs-lookup"><span data-stu-id="71de4-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Menu contextuel ajouter une référence dans Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="71de4-168">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez le projet **StringLibrary** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="71de4-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="71de4-170">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="71de4-170">Run the app</span></span>

1. <span data-ttu-id="71de4-171">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="71de4-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="71de4-173">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour compiler et exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="71de4-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="71de4-175">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="71de4-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Fenêtre de console avec la vitrine en cours d’exécution":::

## <a name="additional-resources"></a><span data-ttu-id="71de4-177">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="71de4-177">Additional resources</span></span>

* [<span data-ttu-id="71de4-178">Développer des bibliothèques avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="71de4-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="71de4-179">[.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="71de4-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="71de4-180">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="71de4-180">Next steps</span></span>

<span data-ttu-id="71de4-181">Dans ce didacticiel, vous avez créé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="71de4-182">Dans le didacticiel suivant, vous allez apprendre à effectuer un test unitaire de la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="71de4-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71de4-183">Test unitaire d’une bibliothèque de .NET Standard à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71de4-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="71de4-184">Vous pouvez également ignorer les tests unitaires automatisés et apprendre à partager la bibliothèque en créant un package NuGet :</span><span class="sxs-lookup"><span data-stu-id="71de4-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71de4-185">Créer et publier un package avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71de4-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="71de4-186">Ou Découvrez comment publier une application console.</span><span class="sxs-lookup"><span data-stu-id="71de4-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="71de4-187">Si vous publiez l’application console à partir de la solution que vous avez créée dans ce didacticiel, la bibliothèque de classes y est insérée comme un fichier *. dll* .</span><span class="sxs-lookup"><span data-stu-id="71de4-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71de4-188">Publier une application console .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71de4-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
