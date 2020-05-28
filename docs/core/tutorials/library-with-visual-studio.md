---
title: Créer une bibliothèque de classes .NET Standard dans Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005241"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="0534d-103">Didacticiel : créer une bibliothèque de .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0534d-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="0534d-104">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="0534d-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="0534d-105">Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0534d-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="0534d-106">Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="0534d-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="0534d-107">Pour obtenir la liste des versions de .NET Standard et les plateformes qu’elles prennent en charge, consultez [.NET standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="0534d-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="0534d-108">Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="0534d-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="0534d-109">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) pour pouvoir l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="0534d-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0534d-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0534d-110">Prerequisites</span></span>

- <span data-ttu-id="0534d-111">[Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="0534d-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="0534d-112">Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="0534d-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="0534d-113">Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="0534d-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="0534d-114">Créer une solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0534d-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="0534d-115">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="0534d-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="0534d-116">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="0534d-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="0534d-117">Vous ajouterez des projets connexes supplémentaires à la même solution.</span><span class="sxs-lookup"><span data-stu-id="0534d-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="0534d-118">Pour créer la solution vide :</span><span class="sxs-lookup"><span data-stu-id="0534d-118">To create the blank solution:</span></span>

1. <span data-ttu-id="0534d-119">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0534d-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="0534d-120">Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="0534d-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="0534d-121">Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="0534d-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="0534d-122">Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0534d-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="0534d-124">Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="0534d-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="0534d-125">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="0534d-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="0534d-126">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="0534d-126">Create a class library project</span></span>

1. <span data-ttu-id="0534d-127">Ajoutez un nouveau projet de bibliothèque de classes .NET Standard nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="0534d-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="0534d-128">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="0534d-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="0534d-129">Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="0534d-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="0534d-130">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="0534d-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="0534d-131">Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0534d-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0534d-132">Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="0534d-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="0534d-133">Ensuite, choisissez **créer**.</span><span class="sxs-lookup"><span data-stu-id="0534d-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="0534d-134">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0534d-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="0534d-135">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0534d-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="0534d-136">La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="0534d-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="0534d-138">Si vous utilisez Visual Basic, effacez le texte dans la zone de texte **espace de noms racine** .</span><span class="sxs-lookup"><span data-stu-id="0534d-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="0534d-140">Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="0534d-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="0534d-141">Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) mot clé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="0534d-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="0534d-142">Remplacez le code dans la fenêtre de code pour *Class1.cs* ou *Class1. vb* par le code suivant, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="0534d-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="0534d-143">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="0534d-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="0534d-144">La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="0534d-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="0534d-145">Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="0534d-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="0534d-146">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="0534d-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="0534d-147">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="0534d-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="0534d-148">Dans la barre de menus, sélectionnez **générer**  >  **générer la solution** pour vérifier que le projet se compile sans erreur.</span><span class="sxs-lookup"><span data-stu-id="0534d-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="0534d-149">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="0534d-149">Add a console app to the solution</span></span>

<span data-ttu-id="0534d-150">Utilisez la bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="0534d-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="0534d-151">Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.</span><span class="sxs-lookup"><span data-stu-id="0534d-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="0534d-152">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="0534d-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0534d-153">Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="0534d-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="0534d-154">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="0534d-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="0534d-155">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0534d-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0534d-156">Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="0534d-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="0534d-157">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="0534d-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="0534d-158">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="0534d-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="0534d-160">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="0534d-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="0534d-161">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="0534d-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="0534d-162">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `ShowCase` nœud **dépendances** du projet, puis sélectionnez **Ajouter une référence de projet**.</span><span class="sxs-lookup"><span data-stu-id="0534d-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Menu contextuel ajouter une référence dans Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="0534d-164">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez le projet **StringLibrary** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0534d-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="0534d-166">Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0534d-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="0534d-167">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="0534d-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="0534d-168">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0534d-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="0534d-169">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="0534d-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="0534d-170">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="0534d-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="0534d-171">Si l’utilisateur appuie sur la touche entrée sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="0534d-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="0534d-172">Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="0534d-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="0534d-173">Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="0534d-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="0534d-175">Essayez le programme en entrant des chaînes et en appuyant sur **entrée**, puis appuyez sur **entrée** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="0534d-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Fenêtre de console avec la vitrine en cours d’exécution":::

## <a name="next-steps"></a><span data-ttu-id="0534d-177">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0534d-177">Next steps</span></span>

<span data-ttu-id="0534d-178">Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="0534d-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="0534d-179">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="0534d-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0534d-180">Tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0534d-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
