---
title: Créer une bibliothèque de classes .NET à l’aide de Visual Studio Code
description: Découvrez comment créer une bibliothèque de classes .NET à l’aide de Visual Studio Code.
ms.date: 11/18/2020
ms.openlocfilehash: 4daa077fc54da3de2f808d831e06ee5f9bb3bde7
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916089"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a><span data-ttu-id="deba2-103">Didacticiel : créer une bibliothèque de classes .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="deba2-103">Tutorial: Create a .NET class library using Visual Studio Code</span></span>

<span data-ttu-id="deba2-104">Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="deba2-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span>

<span data-ttu-id="deba2-105">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="deba2-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="deba2-106">Si la bibliothèque cible .NET Standard 2,0, elle peut être appelée par n’importe quelle implémentation .NET (y compris .NET Framework) qui prend en charge .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="deba2-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="deba2-107">Si la bibliothèque cible .NET 5, elle peut être appelée par n’importe quelle application qui cible .NET 5.</span><span class="sxs-lookup"><span data-stu-id="deba2-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="deba2-108">Ce didacticiel montre comment cibler .NET 5.</span><span class="sxs-lookup"><span data-stu-id="deba2-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="deba2-109">Lorsque vous créez une bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="deba2-109">When you create a class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="deba2-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="deba2-110">Prerequisites</span></span>

1. <span data-ttu-id="deba2-111">[Visual Studio code](https://code.visualstudio.com/) avec l' [extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installée.</span><span class="sxs-lookup"><span data-stu-id="deba2-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="deba2-112">Pour plus d’informations sur la façon d’installer des extensions sur Visual Studio Code, consultez [vs code d’extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="deba2-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="deba2-113">Le [Kit de développement logiciel (SDK) .net 5,0 ou version ultérieure](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="deba2-113">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="deba2-114">Créer une solution</span><span class="sxs-lookup"><span data-stu-id="deba2-114">Create a solution</span></span>

<span data-ttu-id="deba2-115">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="deba2-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="deba2-116">Une solution sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="deba2-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="deba2-117">Vous ajouterez des projets connexes supplémentaires à la même solution.</span><span class="sxs-lookup"><span data-stu-id="deba2-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="deba2-118">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="deba2-118">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="deba2-119">**File**  >  Dans le menu principal, sélectionnez fichier **ouvrir le dossier** (**Ouvrir...** sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="deba2-119">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="deba2-120">Dans la boîte de dialogue **ouvrir un dossier** , créez un dossier *ClassLibraryProjects* , puis cliquez sur **Sélectionner un dossier** (**ouvrir** sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="deba2-120">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="deba2-121">Ouvrez le **Terminal** dans Visual Studio code en sélectionnant **Afficher** le  >  **Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="deba2-121">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="deba2-122">Le **Terminal** s’ouvre avec l’invite de commandes dans le dossier *ClassLibraryProjects*</span><span class="sxs-lookup"><span data-stu-id="deba2-122">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="deba2-123">Dans le **Terminal**, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="deba2-123">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="deba2-124">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-124">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="deba2-125">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="deba2-125">Create a class library project</span></span>

<span data-ttu-id="deba2-126">Ajoutez un nouveau projet de bibliothèque de classes .NET nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="deba2-126">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="deba2-127">Dans le terminal, exécutez la commande suivante pour créer le projet de bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="deba2-127">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="deba2-128">La `-o` `--output` commande ou spécifie l’emplacement où la sortie générée doit être placée.</span><span class="sxs-lookup"><span data-stu-id="deba2-128">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="deba2-129">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-129">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="deba2-130">Exécutez la commande suivante pour ajouter le projet de bibliothèque à la solution :</span><span class="sxs-lookup"><span data-stu-id="deba2-130">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="deba2-131">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-131">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="deba2-132">Assurez-vous que la bibliothèque cible .NET 5.</span><span class="sxs-lookup"><span data-stu-id="deba2-132">Check to make sure that the library targets .NET 5.</span></span> <span data-ttu-id="deba2-133">Dans l' **Explorateur**, ouvrez *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="deba2-133">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="deba2-134">L' `TargetFramework` élément indique que le projet cible .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="deba2-134">The `TargetFramework` element shows that the project targets .NET 5.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="deba2-135">Ouvrez *Class1.cs* et remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="deba2-135">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="deba2-136">La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="deba2-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="deba2-137">Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="deba2-137">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="deba2-138">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="deba2-138">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="deba2-139">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="deba2-139">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="deba2-140">Enregistrez le fichier .</span><span class="sxs-lookup"><span data-stu-id="deba2-140">Save the file.</span></span>

1. <span data-ttu-id="deba2-141">Exécutez la commande suivante pour générer la solution et vérifier que le projet se compile sans erreur.</span><span class="sxs-lookup"><span data-stu-id="deba2-141">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="deba2-142">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-142">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="deba2-143">Ajouter une application console à la solution</span><span class="sxs-lookup"><span data-stu-id="deba2-143">Add a console app to the solution</span></span>

<span data-ttu-id="deba2-144">Ajoutez une application console qui utilise la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="deba2-144">Add a console application that uses the class library.</span></span> <span data-ttu-id="deba2-145">L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="deba2-145">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="deba2-146">Dans le terminal, exécutez la commande suivante pour créer le projet d’application console :</span><span class="sxs-lookup"><span data-stu-id="deba2-146">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="deba2-147">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-147">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="deba2-148">Exécutez la commande suivante pour ajouter le projet d’application console à la solution :</span><span class="sxs-lookup"><span data-stu-id="deba2-148">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="deba2-149">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-149">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="deba2-150">Ouvrez *Showcase/Program. cs* et remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="deba2-150">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="deba2-151">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="deba2-151">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="deba2-152">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="deba2-152">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="deba2-153">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="deba2-153">The program prompts the user to enter a string.</span></span> <span data-ttu-id="deba2-154">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="deba2-154">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="deba2-155">Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="deba2-155">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="deba2-156">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="deba2-156">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="deba2-157">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="deba2-157">Add a project reference</span></span>

<span data-ttu-id="deba2-158">Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="deba2-158">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="deba2-159">Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="deba2-159">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="deba2-160">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="deba2-160">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="deba2-161">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-161">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="deba2-162">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="deba2-162">Run the app</span></span>

1. <span data-ttu-id="deba2-163">Exécutez la commande suivante dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="deba2-163">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="deba2-164">Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="deba2-164">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="deba2-165">La sortie du terminal ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deba2-165">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="deba2-166">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="deba2-166">Additional resources</span></span>

* [<span data-ttu-id="deba2-167">Développer des bibliothèques avec l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="deba2-167">Develop libraries with the .NET CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="deba2-168">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="deba2-168">Next steps</span></span>

<span data-ttu-id="deba2-169">Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="deba2-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="deba2-170">Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.</span><span class="sxs-lookup"><span data-stu-id="deba2-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="deba2-171">Test d’une bibliothèque de classes .NET avec .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="deba2-171">Test a .NET class library with .NET using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
