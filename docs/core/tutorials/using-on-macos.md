---
title: 'Tutoriel : Créer une solution .NET Core dans macOS à l’aide de Visual Studio Code'
description: Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 022afd99c6d36d7a60ac40f3f27ba073c5470bd2
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082811"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="bb64b-103">Tutoriel : Créer une solution .NET Core dans macOS à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bb64b-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="bb64b-104">Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core pour macOS.</span><span class="sxs-lookup"><span data-stu-id="bb64b-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="bb64b-105">Découvrez comment créer des projets et des tests unitaires, utiliser les outils de débogage et incorporer des bibliothèques tierces à l’aide de [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="bb64b-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="bb64b-106">Cet article utilise [Visual Studio Code](https://code.visualstudio.com) sur macOS.</span><span class="sxs-lookup"><span data-stu-id="bb64b-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb64b-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="bb64b-107">Prerequisites</span></span>

<span data-ttu-id="bb64b-108">Installez le [SDK .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="bb64b-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="bb64b-109">Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb64b-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="bb64b-110">Installez [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="bb64b-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="bb64b-111">Au cours de cet article, vous allez également installer des extensions Visual Studio Code pour améliorer l’expérience de développement de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb64b-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="bb64b-112">Installez l’extension C# de Visual Studio Code en ouvrant Visual Studio Code et en appuyant sur <kbd>F1</kbd> pour ouvrir la palette Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bb64b-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="bb64b-113">Tapez **ext install** pour afficher la liste des extensions.</span><span class="sxs-lookup"><span data-stu-id="bb64b-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="bb64b-114">Sélectionnez l’extension C#.</span><span class="sxs-lookup"><span data-stu-id="bb64b-114">Select the C# extension.</span></span> <span data-ttu-id="bb64b-115">Redémarrez Visual Studio Code pour activer l’extension.</span><span class="sxs-lookup"><span data-stu-id="bb64b-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="bb64b-116">Pour plus d’informations, consultez la [documentation sur l’extension C# pour Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="bb64b-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="bb64b-117">Prise en main</span><span class="sxs-lookup"><span data-stu-id="bb64b-117">Get started</span></span>

<span data-ttu-id="bb64b-118">Dans ce didacticiel, vous créez trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb64b-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="bb64b-119">Vous pouvez [voir ou télécharger la source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) de cette rubrique dans le dépôt dotnet/samples sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="bb64b-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="bb64b-120">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="bb64b-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="bb64b-121">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bb64b-121">Start Visual Studio Code.</span></span> <span data-ttu-id="bb64b-122">Appuyez sur <kbd>Ctrl</kbd>+<kbd>\`</kbd> (accent grave) ou sélectionnez **Affichage > Terminal intégré** dans le menu pour ouvrir un terminal incorporé dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bb64b-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="bb64b-123">Vous pouvez également ouvrir un interpréteur de commandes externe à l’aide de la commande **Ouvrir dans l’invite de commandes** de l’Explorateur (**Ouvrir dans Terminal** sur Mac ou Linux) si vous préférez travailler en dehors de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bb64b-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="bb64b-124">Commencez par créer un fichier de solution qui servira de conteneur pour un ou plusieurs projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb64b-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="bb64b-125">Dans le terminal, exécutez la [`dotnet new`](../tools/dotnet-new.md) commande pour créer une solution *Golden. sln* à l’intérieur d’un nouveau dossier nommé *Golden*:</span><span class="sxs-lookup"><span data-stu-id="bb64b-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```console
dotnet new sln -o golden
```

<span data-ttu-id="bb64b-126">Accédez au nouveau dossier *Golden* et exécutez la commande suivante pour créer un projet de bibliothèque, qui génère deux fichiers,*Library. csproj* et *Class1.cs*, dans le dossier de *bibliothèque* :</span><span class="sxs-lookup"><span data-stu-id="bb64b-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="bb64b-127">Exécutez la commande [`dotnet sln`](../tools/dotnet-sln.md) pour ajouter le projet *library.csproj* que vous venez de créer à la solution :</span><span class="sxs-lookup"><span data-stu-id="bb64b-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="bb64b-128">Le fichier *library.csproj* contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb64b-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="bb64b-129">Les méthodes de la bibliothèque sérialisent et désérialisent les objets au format JSON.</span><span class="sxs-lookup"><span data-stu-id="bb64b-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="bb64b-130">Pour prendre en charge la sérialisation et la désérialisation JSON, ajoutez une référence au package NuGet `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="bb64b-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="bb64b-131">La commande `dotnet add` ajoute de nouveaux éléments à un projet.</span><span class="sxs-lookup"><span data-stu-id="bb64b-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="bb64b-132">Pour ajouter une référence à un package NuGet, utilisez la commande [`dotnet add package`](../tools/dotnet-add-package.md) et spécifiez le nom du package :</span><span class="sxs-lookup"><span data-stu-id="bb64b-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="bb64b-133">Cette opération ajoute `Newtonsoft.Json` et ses dépendances au projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb64b-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="bb64b-134">Vous pouvez aussi modifier manuellement le fichier *library.csproj* et ajouter le nœud suivant :</span><span class="sxs-lookup"><span data-stu-id="bb64b-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="bb64b-135">Exécutez [`dotnet restore`](../tools/dotnet-restore.md), ([voir la remarque](#dotnet-restore-note)) qui restaure les dépendances et crée un dossier *obj* dans *library* avec trois fichiers, notamment un fichier *project.assets.json* :</span><span class="sxs-lookup"><span data-stu-id="bb64b-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="bb64b-136">Dans le dossier *library*, renommez le fichier *Class1.cs* en *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="bb64b-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="bb64b-137">Remplacez le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bb64b-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="bb64b-138">La classe `Thing` contient une méthode publique, `Get`, qui retourne la somme de deux nombres. Pour cela, elle convertit la somme en chaîne, puis la désérialise en entier.</span><span class="sxs-lookup"><span data-stu-id="bb64b-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="bb64b-139">Ce code utilise un certain nombre de fonctionnalités C# modernes, comme les [directives `using static`](../../csharp/language-reference/keywords/using-static.md), les [membres expression-bodied](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) et l’[interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="bb64b-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="bb64b-140">Générez la bibliothèque à l’aide de la commande [ `dotnet build` ](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="bb64b-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="bb64b-141">Un fichier *library.dll* est généré sous *golden/library/bin/Debug/netstandard1.4* :</span><span class="sxs-lookup"><span data-stu-id="bb64b-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="bb64b-142">Créer le projet de test</span><span class="sxs-lookup"><span data-stu-id="bb64b-142">Create the test project</span></span>

<span data-ttu-id="bb64b-143">Créez un projet de test pour la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb64b-143">Build a test project for the library.</span></span> <span data-ttu-id="bb64b-144">À partir du dossier *golden*, créez un projet de test :</span><span class="sxs-lookup"><span data-stu-id="bb64b-144">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="bb64b-145">Ajoutez le projet de test à la solution :</span><span class="sxs-lookup"><span data-stu-id="bb64b-145">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="bb64b-146">Ajoutez une référence de projet à la bibliothèque créée à la section précédente pour que le compilateur puisse trouver et utiliser le projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb64b-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="bb64b-147">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="bb64b-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="bb64b-148">Vous pouvez aussi modifier manuellement le fichier *test-library.csproj* et ajouter le nœud suivant :</span><span class="sxs-lookup"><span data-stu-id="bb64b-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="bb64b-149">Maintenant que les dépendances ont été correctement configurées, créez les tests pour votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb64b-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="bb64b-150">Ouvrez *UnitTest1.cs* et remplacez son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bb64b-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="bb64b-151">Le fait de déclarer la valeur 42 n’est pas égal à 19+23 (ou 42) quand vous créez initialement le test unitaire (`Assert.NotEqual`), qui échoue.</span><span class="sxs-lookup"><span data-stu-id="bb64b-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="bb64b-152">Lors de la création d’un test unitaire, une étape importante consiste à le faire échouer une fois pour confirmer sa logique.</span><span class="sxs-lookup"><span data-stu-id="bb64b-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="bb64b-153">À partir du dossier *golden*, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb64b-153">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="bb64b-154">Ces commandes trouvent de manière récursive tous les projets pour restaurer les dépendances, les générer et activer le Test Runner xUnit pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="bb64b-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="bb64b-155">Le test unique échoue comme prévu.</span><span class="sxs-lookup"><span data-stu-id="bb64b-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="bb64b-156">Modifiez le fichier *UnitTest1.cs* et remplacez l’assertion `Assert.NotEqual` par `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="bb64b-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="bb64b-157">Exécutez la commande suivante à partir du dossier *golden* pour réexécuter le test, qui réussit cette fois-ci :</span><span class="sxs-lookup"><span data-stu-id="bb64b-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="bb64b-158">Créer l’application console</span><span class="sxs-lookup"><span data-stu-id="bb64b-158">Create the console app</span></span>

<span data-ttu-id="bb64b-159">L’application console que vous allez créer dans les étapes suivantes est dépendante du projet de bibliothèque créé précédemment et appelle sa méthode de bibliothèque durant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bb64b-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="bb64b-160">Ce modèle de développement vous permet de voir comment créer des bibliothèques réutilisables pour plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="bb64b-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="bb64b-161">Créez une application console à partir du dossier *golden* :</span><span class="sxs-lookup"><span data-stu-id="bb64b-161">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="bb64b-162">Ajoutez le projet d’application console à la solution :</span><span class="sxs-lookup"><span data-stu-id="bb64b-162">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="bb64b-163">Créez la dépendance à la bibliothèque en exécutant la commande `dotnet add reference` :</span><span class="sxs-lookup"><span data-stu-id="bb64b-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="bb64b-164">Exécutez `dotnet restore` ([voir la remarque](#dotnet-restore-note)) pour restaurer les dépendances des trois projets dans la solution.</span><span class="sxs-lookup"><span data-stu-id="bb64b-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="bb64b-165">Ouvrez *program.cs* et remplacez le contenu de la méthode `Main` par la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="bb64b-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="bb64b-166">Ajoutez deux directives `using` en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="bb64b-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="bb64b-167">Lancez la commande suivante `dotnet run` pour exécuter l’exécutable, où l’option `-p` après `dotnet run` spécifie le projet de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="bb64b-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="bb64b-168">L’application génère la chaîne « The answer is 42 ».</span><span class="sxs-lookup"><span data-stu-id="bb64b-168">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="bb64b-169">Déboguer l’application</span><span class="sxs-lookup"><span data-stu-id="bb64b-169">Debug the application</span></span>

<span data-ttu-id="bb64b-170">Définissez un point d’arrêt au niveau de l’instruction `WriteLine` dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="bb64b-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="bb64b-171">Pour ce faire, appuyez sur la touche <kbd>F9</kbd> quand le curseur se trouve sur la ligne `WriteLine` ou cliquez dans la marge gauche de la ligne où vous souhaitez définir le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bb64b-171">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="bb64b-172">Un cercle rouge apparaît dans la marge à côté de la ligne de code.</span><span class="sxs-lookup"><span data-stu-id="bb64b-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="bb64b-173">Quand le point d’arrêt est atteint, l’exécution du code s’arrête *avant* l’exécution de la ligne de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bb64b-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="bb64b-174">Ouvrez l’onglet du débogueur. Pour cela, sélectionnez l’icône de débogage dans la barre d’outils de Visual Studio Code, puis **Affichage > Déboguer** à partir de la barre de menus, ou utilisez le raccourci clavier <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd> :</span><span class="sxs-lookup"><span data-stu-id="bb64b-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Débogueur Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="bb64b-176">Appuyez sur le bouton de lecture pour démarrer l’application sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="bb64b-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="bb64b-177">L’application s’exécute jusqu’au point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bb64b-177">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="bb64b-178">Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés.</span><span class="sxs-lookup"><span data-stu-id="bb64b-178">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="bb64b-179">Vérifiez que la réponse est 42.</span><span class="sxs-lookup"><span data-stu-id="bb64b-179">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
