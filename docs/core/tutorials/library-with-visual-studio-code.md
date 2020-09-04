---
title: Créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio Code
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio Code.
ms.date: 06/08/2020
ms.openlocfilehash: d37e3c663146c90f4ae4188b25ea7e501501c93b
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465284"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="4d87f-103">Didacticiel : créer une bibliothèque de .NET Standard à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4d87f-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="4d87f-104">Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="4d87f-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="4d87f-105">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) pour pouvoir l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="4d87f-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="4d87f-106">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="4d87f-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="4d87f-107">Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4d87f-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="4d87f-108">Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="4d87f-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d87f-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4d87f-109">Prerequisites</span></span>

1. <span data-ttu-id="4d87f-110">[Visual Studio code](https://code.visualstudio.com/) avec l' [extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installée.</span><span class="sxs-lookup"><span data-stu-id="4d87f-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="4d87f-111">Pour plus d’informations sur la façon d’installer des extensions sur Visual Studio Code, consultez [vs code d’extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="4d87f-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="4d87f-112">Le [Kit de développement logiciel (SDK) .net Core 3,1 ou version ultérieure](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="4d87f-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="4d87f-113">Créer une solution</span><span class="sxs-lookup"><span data-stu-id="4d87f-113">Create a solution</span></span>

<span data-ttu-id="4d87f-114">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4d87f-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="4d87f-115">Une solution sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="4d87f-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="4d87f-116">Vous ajouterez des projets connexes supplémentaires à la même solution.</span><span class="sxs-lookup"><span data-stu-id="4d87f-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="4d87f-117">Démarrer Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4d87f-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="4d87f-118">**File**  >  Dans le menu principal, sélectionnez fichier**ouvrir le dossier** (**Ouvrir...** sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="4d87f-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="4d87f-119">Dans la boîte de dialogue **ouvrir un dossier** , créez un dossier *ClassLibraryProjects* , puis cliquez sur **Sélectionner un dossier** (**ouvrir** sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="4d87f-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="4d87f-120">Ouvrez le **Terminal** dans Visual Studio code en sélectionnant **Afficher**le  >  **Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="4d87f-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="4d87f-121">Le **Terminal** s’ouvre avec l’invite de commandes dans le dossier *ClassLibraryProjects*</span><span class="sxs-lookup"><span data-stu-id="4d87f-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="4d87f-122">Dans le **Terminal**, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4d87f-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="4d87f-123">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-123">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="4d87f-124">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="4d87f-124">Create a class library project</span></span>

<span data-ttu-id="4d87f-125">Ajoutez un nouveau projet de bibliothèque de classes .NET Standard nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="4d87f-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="4d87f-126">Dans le terminal, exécutez la commande suivante pour créer le projet de bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="4d87f-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="4d87f-127">La `-o` `--output` commande ou spécifie l’emplacement où la sortie générée doit être placée.</span><span class="sxs-lookup"><span data-stu-id="4d87f-127">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="4d87f-128">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-128">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="4d87f-129">Exécutez la commande suivante pour ajouter le projet de bibliothèque à la solution :</span><span class="sxs-lookup"><span data-stu-id="4d87f-129">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="4d87f-130">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-130">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="4d87f-131">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4d87f-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="4d87f-132">Dans l' **Explorateur**, ouvrez *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="4d87f-132">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="4d87f-133">L' `TargetFramework` élément indique que le projet cible .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="4d87f-133">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="4d87f-134">Ouvrez *Class1.cs* et remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d87f-134">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="4d87f-135">La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="4d87f-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="4d87f-136">Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="4d87f-136">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="4d87f-137">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="4d87f-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="4d87f-138">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="4d87f-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="4d87f-139">Enregistrez le fichier .</span><span class="sxs-lookup"><span data-stu-id="4d87f-139">Save the file.</span></span>

1. <span data-ttu-id="4d87f-140">Exécutez la commande suivante pour générer la solution et vérifier que le projet se compile sans erreur.</span><span class="sxs-lookup"><span data-stu-id="4d87f-140">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="4d87f-141">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-141">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="4d87f-142">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="4d87f-142">Add a console app to the solution</span></span>

<span data-ttu-id="4d87f-143">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4d87f-143">Add a console application that uses the class library.</span></span> <span data-ttu-id="4d87f-144">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="4d87f-144">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="4d87f-145">Dans le terminal, exécutez la commande suivante pour créer le projet d’application console :</span><span class="sxs-lookup"><span data-stu-id="4d87f-145">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="4d87f-146">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-146">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="4d87f-147">Exécutez la commande suivante pour ajouter le projet d’application console à la solution :</span><span class="sxs-lookup"><span data-stu-id="4d87f-147">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="4d87f-148">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-148">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="4d87f-149">Ouvrez *Showcase/Program. cs* et remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d87f-149">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="4d87f-150">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4d87f-150">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="4d87f-151">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d87f-151">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="4d87f-152">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4d87f-152">The program prompts the user to enter a string.</span></span> <span data-ttu-id="4d87f-153">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="4d87f-153">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="4d87f-154">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="4d87f-154">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="4d87f-155">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="4d87f-155">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="4d87f-156">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="4d87f-156">Add a project reference</span></span>

<span data-ttu-id="4d87f-157">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4d87f-157">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="4d87f-158">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4d87f-158">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="4d87f-159">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4d87f-159">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="4d87f-160">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-160">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="4d87f-161">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="4d87f-161">Run the app</span></span>

1. <span data-ttu-id="4d87f-162">Exécutez la commande suivante dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4d87f-162">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="4d87f-163">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="4d87f-163">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="4d87f-164">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d87f-164">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="4d87f-165">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4d87f-165">Additional resources</span></span>

* [<span data-ttu-id="4d87f-166">Développer des bibliothèques avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d87f-166">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="4d87f-167">[.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="4d87f-167">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d87f-168">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4d87f-168">Next steps</span></span>

<span data-ttu-id="4d87f-169">Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4d87f-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="4d87f-170">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="4d87f-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4d87f-171">Tester une bibliothèque .NET Standard avec .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4d87f-171">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
