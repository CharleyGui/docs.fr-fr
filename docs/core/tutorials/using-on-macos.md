---
title: Bien démarrer avec .NET Core sur macOS
description: Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de Visual Studio Code.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e79f5dd90124d2a1902194af2edbde0f5df107c7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633979"
---
# <a name="get-started-with-net-core-on-macos"></a><span data-ttu-id="481e0-103">Bien démarrer avec .NET Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="481e0-103">Get started with .NET Core on macOS</span></span>

<span data-ttu-id="481e0-104">Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core pour macOS.</span><span class="sxs-lookup"><span data-stu-id="481e0-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="481e0-105">Découvrez comment créer des projets et des tests unitaires, utiliser les outils de débogage et incorporer des bibliothèques tierces à l’aide de [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="481e0-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="481e0-106">Cet article utilise [Visual Studio Code](https://code.visualstudio.com) sur macOS.</span><span class="sxs-lookup"><span data-stu-id="481e0-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="481e0-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="481e0-107">Prerequisites</span></span>

<span data-ttu-id="481e0-108">Installez le [SDK .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="481e0-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="481e0-109">Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="481e0-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="481e0-110">Installez [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="481e0-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="481e0-111">Au cours de cet article, vous allez également installer des extensions Visual Studio Code pour améliorer l’expérience de développement de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="481e0-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="481e0-112">Installez l’extension C# de Visual Studio Code en ouvrant Visual Studio Code et en appuyant sur <kbd>F1</kbd> pour ouvrir la palette Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="481e0-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="481e0-113">Tapez **ext install** pour afficher la liste des extensions.</span><span class="sxs-lookup"><span data-stu-id="481e0-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="481e0-114">Sélectionnez l’extension C#.</span><span class="sxs-lookup"><span data-stu-id="481e0-114">Select the C# extension.</span></span> <span data-ttu-id="481e0-115">Redémarrez Visual Studio Code pour activer l’extension.</span><span class="sxs-lookup"><span data-stu-id="481e0-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="481e0-116">Pour plus d’informations, consultez la [documentation sur l’extension C# pour Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="481e0-117">Prise en main</span><span class="sxs-lookup"><span data-stu-id="481e0-117">Get started</span></span>

<span data-ttu-id="481e0-118">Dans ce didacticiel, vous créez trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="481e0-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="481e0-119">Vous pouvez [voir ou télécharger la source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) de cette rubrique dans le dépôt dotnet/samples sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="481e0-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="481e0-120">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="481e0-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="481e0-121">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="481e0-121">Start Visual Studio Code.</span></span> <span data-ttu-id="481e0-122">Appuyez sur <kbd>Ctrl</kbd>+<kbd>\`</kbd> (accent grave) ou sélectionnez **Affichage > Terminal intégré** dans le menu pour ouvrir un terminal incorporé dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="481e0-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="481e0-123">Vous pouvez également ouvrir un interpréteur de commandes externe à l’aide de la commande **Ouvrir dans l’invite de commandes** de l’Explorateur (**Ouvrir dans Terminal** sur Mac ou Linux) si vous préférez travailler en dehors de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="481e0-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="481e0-124">Commencez par créer un fichier de solution qui servira de conteneur pour un ou plusieurs projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="481e0-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="481e0-125">Dans le terminal, créez un dossier *golden* et ouvrez le dossier.</span><span class="sxs-lookup"><span data-stu-id="481e0-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="481e0-126">Ce dossier est la racine de votre solution.</span><span class="sxs-lookup"><span data-stu-id="481e0-126">This folder is the root of your solution.</span></span> <span data-ttu-id="481e0-127">Exécutez la commande [`dotnet new`](../tools/dotnet-new.md) pour créer une solution, *golden.sln* :</span><span class="sxs-lookup"><span data-stu-id="481e0-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="481e0-128">À partir du dossier *golden*, exécutez la commande suivante pour créer un projet de bibliothèque qui génère deux fichiers,*library.csproj* et *Class1.cs*, dans le dossier *library* :</span><span class="sxs-lookup"><span data-stu-id="481e0-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="481e0-129">Exécutez la commande [`dotnet sln`](../tools/dotnet-sln.md) pour ajouter le projet *library.csproj* que vous venez de créer à la solution :</span><span class="sxs-lookup"><span data-stu-id="481e0-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="481e0-130">Le fichier *library.csproj* contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="481e0-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="481e0-131">Les méthodes de la bibliothèque sérialisent et désérialisent les objets au format JSON.</span><span class="sxs-lookup"><span data-stu-id="481e0-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="481e0-132">Pour prendre en charge la sérialisation et la désérialisation JSON, ajoutez une référence au package NuGet `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="481e0-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="481e0-133">La commande `dotnet add` ajoute de nouveaux éléments à un projet.</span><span class="sxs-lookup"><span data-stu-id="481e0-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="481e0-134">Pour ajouter une référence à un package NuGet, utilisez la commande [`dotnet add package`](../tools/dotnet-add-package.md) et spécifiez le nom du package :</span><span class="sxs-lookup"><span data-stu-id="481e0-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="481e0-135">Cette opération ajoute `Newtonsoft.Json` et ses dépendances au projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="481e0-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="481e0-136">Vous pouvez aussi modifier manuellement le fichier *library.csproj* et ajouter le nœud suivant :</span><span class="sxs-lookup"><span data-stu-id="481e0-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="481e0-137">Exécutez [`dotnet restore`](../tools/dotnet-restore.md), ([voir la remarque](#dotnet-restore-note)) qui restaure les dépendances et crée un dossier *obj* dans *library* avec trois fichiers, notamment un fichier *project.assets.json* :</span><span class="sxs-lookup"><span data-stu-id="481e0-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="481e0-138">Dans le dossier *library*, renommez le fichier *Class1.cs* en *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="481e0-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="481e0-139">Remplacez le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="481e0-139">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="481e0-140">La classe `Thing` contient une méthode publique, `Get`, qui retourne la somme de deux nombres. Pour cela, elle convertit la somme en chaîne, puis la désérialise en entier.</span><span class="sxs-lookup"><span data-stu-id="481e0-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="481e0-141">Ce code utilise un certain nombre de fonctionnalités C# modernes, comme les [directives `using static`](../../csharp/language-reference/keywords/using-static.md), les [membres expression-bodied](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) et l’[interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="481e0-142">Générez la bibliothèque à l’aide de la commande [ `dotnet build` ](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="481e0-143">Un fichier *library.dll* est généré sous *golden/library/bin/Debug/netstandard1.4* :</span><span class="sxs-lookup"><span data-stu-id="481e0-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="481e0-144">Créer le projet de test</span><span class="sxs-lookup"><span data-stu-id="481e0-144">Create the test project</span></span>

<span data-ttu-id="481e0-145">Créez un projet de test pour la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="481e0-145">Build a test project for the library.</span></span> <span data-ttu-id="481e0-146">À partir du dossier *golden*, créez un projet de test :</span><span class="sxs-lookup"><span data-stu-id="481e0-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="481e0-147">Ajoutez le projet de test à la solution :</span><span class="sxs-lookup"><span data-stu-id="481e0-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="481e0-148">Ajoutez une référence de projet à la bibliothèque créée à la section précédente pour que le compilateur puisse trouver et utiliser le projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="481e0-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="481e0-149">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="481e0-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="481e0-150">Vous pouvez aussi modifier manuellement le fichier *test-library.csproj* et ajouter le nœud suivant :</span><span class="sxs-lookup"><span data-stu-id="481e0-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="481e0-151">Maintenant que les dépendances ont été correctement configurées, créez les tests pour votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="481e0-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="481e0-152">Ouvrez *UnitTest1.cs* et remplacez son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="481e0-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="481e0-153">Le fait de déclarer la valeur 42 n’est pas égal à 19+23 (ou 42) quand vous créez initialement le test unitaire (`Assert.NotEqual`), qui échoue.</span><span class="sxs-lookup"><span data-stu-id="481e0-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="481e0-154">Lors de la création d’un test unitaire, une étape importante consiste à le faire échouer une fois pour confirmer sa logique.</span><span class="sxs-lookup"><span data-stu-id="481e0-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="481e0-155">À partir du dossier *golden*, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="481e0-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="481e0-156">Ces commandes trouvent de manière récursive tous les projets pour restaurer les dépendances, les générer et activer le Test Runner xUnit pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="481e0-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="481e0-157">Le test unique échoue comme prévu.</span><span class="sxs-lookup"><span data-stu-id="481e0-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="481e0-158">Modifiez le fichier *UnitTest1.cs* et remplacez l’assertion `Assert.NotEqual` par `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="481e0-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="481e0-159">Exécutez la commande suivante à partir du dossier *golden* pour réexécuter le test, qui réussit cette fois-ci :</span><span class="sxs-lookup"><span data-stu-id="481e0-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="481e0-160">Créer l’application console</span><span class="sxs-lookup"><span data-stu-id="481e0-160">Create the console app</span></span>

<span data-ttu-id="481e0-161">L’application console que vous allez créer dans les étapes suivantes est dépendante du projet de bibliothèque créé précédemment et appelle sa méthode de bibliothèque durant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="481e0-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="481e0-162">Ce modèle de développement vous permet de voir comment créer des bibliothèques réutilisables pour plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="481e0-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="481e0-163">Créez une application console à partir du dossier *golden* :</span><span class="sxs-lookup"><span data-stu-id="481e0-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="481e0-164">Ajoutez le projet d’application console à la solution :</span><span class="sxs-lookup"><span data-stu-id="481e0-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="481e0-165">Créez la dépendance à la bibliothèque en exécutant la commande `dotnet add reference` :</span><span class="sxs-lookup"><span data-stu-id="481e0-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="481e0-166">Exécutez `dotnet restore` ([voir la remarque](#dotnet-restore-note)) pour restaurer les dépendances des trois projets dans la solution.</span><span class="sxs-lookup"><span data-stu-id="481e0-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="481e0-167">Ouvrez *program.cs* et remplacez le contenu de la méthode `Main` par la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="481e0-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="481e0-168">Ajoutez deux directives `using` en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="481e0-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="481e0-169">Lancez la commande suivante `dotnet run` pour exécuter l’exécutable, où l’option `-p` après `dotnet run` spécifie le projet de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="481e0-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="481e0-170">L’application génère la chaîne « The answer is 42 ».</span><span class="sxs-lookup"><span data-stu-id="481e0-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="481e0-171">Déboguer l’application</span><span class="sxs-lookup"><span data-stu-id="481e0-171">Debug the application</span></span>

<span data-ttu-id="481e0-172">Définissez un point d’arrêt au niveau de l’instruction `WriteLine` dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="481e0-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="481e0-173">Pour ce faire, appuyez sur la touche <kbd>F9</kbd> quand le curseur se trouve sur la ligne `WriteLine` ou cliquez dans la marge gauche de la ligne où vous souhaitez définir le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="481e0-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="481e0-174">Un cercle rouge apparaît dans la marge à côté de la ligne de code.</span><span class="sxs-lookup"><span data-stu-id="481e0-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="481e0-175">Quand le point d’arrêt est atteint, l’exécution du code s’arrête *avant* l’exécution de la ligne de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="481e0-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="481e0-176">Ouvrez l’onglet du débogueur. Pour cela, sélectionnez l’icône de débogage dans la barre d’outils de Visual Studio Code, puis **Affichage > Déboguer** à partir de la barre de menus, ou utilisez le raccourci clavier <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd> :</span><span class="sxs-lookup"><span data-stu-id="481e0-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Débogueur Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="481e0-178">Appuyez sur le bouton de lecture pour démarrer l’application sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="481e0-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="481e0-179">L’application s’exécute jusqu’au point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="481e0-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="481e0-180">Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="481e0-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="481e0-181">Vérifiez que la réponse est 42.</span><span class="sxs-lookup"><span data-stu-id="481e0-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
