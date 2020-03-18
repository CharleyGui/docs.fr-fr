---
title: Organisation et test de projets avec le CLI core .NET
description: Ce didacticiel explique comment organiser et tester des projets .NET Core à partir de la ligne de commande.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239909"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="c6a5b-103">Organisation et test de projets avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="c6a5b-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="c6a5b-104">Ce tutoriel, qui fait suite à [Bien démarrer avec .NET Core sur Windows/Linux/macOS en ligne de commande](cli-create-console-app.md), montre comment aller au-delà de la création d’une application console simple pour développer des applications avancées et bien organisées.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="c6a5b-105">Après une présentation des dossiers disponibles pour organiser votre code, ce didacticiel vous montre comment étendre une application console avec le framework de tests [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="c6a5b-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="c6a5b-106">Utilisation de dossiers pour organiser le code</span><span class="sxs-lookup"><span data-stu-id="c6a5b-106">Using folders to organize code</span></span>

<span data-ttu-id="c6a5b-107">Si vous souhaitez introduire de nouveaux types dans une application console, ajoutez des fichiers contenant les types à l’application.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="c6a5b-108">Par exemple, si vous ajoutez des fichiers contenant les types `AccountInformation` et `MonthlyReportRecords` à votre projet, la structure du fichier projet est plate et facile à parcourir :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="c6a5b-109">Toutefois, cela ne fonctionne bien que si la taille de votre projet est relativement petite.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="c6a5b-110">Imaginez ce qui se passerait si vous ajoutiez 20 types au projet :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="c6a5b-111">avec autant de fichiers alourdissant le répertoire racine du projet, la navigation et la maintenance seraient particulièrement difficiles.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="c6a5b-112">Pour organiser le projet, créez un dossier et nommez-le *Models* pour stocker les fichiers de types.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="c6a5b-113">Placez les fichiers de types dans le dossier *Models* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="c6a5b-114">Les projets qui regroupent logiquement les fichiers dans des dossiers simplifient la navigation et la gestion.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="c6a5b-115">Dans la section suivante, vous allez créer un exemple plus complexe avec des dossiers et des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="c6a5b-116">Organisation et test du code à l’aide de l’exemple NewTypes Pets</span><span class="sxs-lookup"><span data-stu-id="c6a5b-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="c6a5b-117">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="c6a5b-117">Building the sample</span></span>

<span data-ttu-id="c6a5b-118">Pour les étapes suivantes, vous pouvez soit suivre [l’exemple NewTypes Pets](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild), soit créer vos propres fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="c6a5b-119">Les types et les tests sont logiquement organisés dans une structure de dossiers qui autorise l’ajout d’autres types et tests par la suite.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="c6a5b-120">L’exemple contient deux types, `Dog` et `Cat`, qui implémentent une interface commune `IPet`.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="c6a5b-121">Pour le projet `NewTypes`, votre objectif est d’organiser les types liés aux animaux domestiques dans un dossier *Pets*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="c6a5b-122">Si un autre jeu de types est ajouté par la suite, *WildAnimals* par exemple, il est placé dans le dossier *NewTypes* aux côtés du dossier *Pets*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="c6a5b-123">Le dossier *WildAnimals* peut contenir des types pour des animaux non domestiques, par exemple `Squirrel` et `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="c6a5b-124">De cette façon, à mesure que vous ajoutez des types, le projet reste bien organisé.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="c6a5b-125">Créez la structure de dossiers suivante avec le contenu de fichier indiqué :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="c6a5b-126">*IPet.cs* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="c6a5b-127">*Dog.cs* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="c6a5b-128">*Cat.cs* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="c6a5b-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="c6a5b-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="c6a5b-130">*NewTypes.csproj* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="c6a5b-131">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="c6a5b-132">Observez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="c6a5b-133">Exercice facultatif : Vous pouvez ajouter un nouveau type d’animal domestique, par exemple `Bird`, en étendant ce projet.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="c6a5b-134">Faites en sorte que la méthode `TalkToOwner` du type Bird envoie un `Tweet!` au propriétaire.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="c6a5b-135">Réexécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-135">Run the app again.</span></span> <span data-ttu-id="c6a5b-136">La sortie inclut `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="c6a5b-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="c6a5b-137">Test de l’exemple</span><span class="sxs-lookup"><span data-stu-id="c6a5b-137">Testing the sample</span></span>

<span data-ttu-id="c6a5b-138">Le projet `NewTypes` est en place et vous l’avez organisé en conservant les types liés aux animaux domestiques dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="c6a5b-139">Créez à présent votre projet de test et commencez à écrire des tests à l’aide du framework de tests [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="c6a5b-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="c6a5b-140">Les tests unitaires vous permettent de vérifier automatiquement le comportement de vos types d’animaux domestiques et de vous assurer qu’ils fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="c6a5b-141">Accédez au dossier *src*, puis créez un dossier *test* et un sous-dossier *NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="c6a5b-142">À une invite de commandes à partir du dossier *NewTypesTests*, exécutez `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="c6a5b-143">Deux fichiers sont générés : *NewTypesTests.csproj* et *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="c6a5b-144">Le projet de test ne peut pas actuellement tester les types dans `NewTypes` et nécessite une référence de projet au projet `NewTypes`.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="c6a5b-145">Pour ajouter une référence [`dotnet add reference`](../tools/dotnet-add-reference.md) de projet, utilisez la commande :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="c6a5b-146">Vous pouvez également ajouter manuellement la référence de projet en ajoutant un nœud `<ItemGroup>` au fichier *NewTypesTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="c6a5b-147">*NewTypesTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="c6a5b-148">Le fichier *NewTypesTests.csproj* contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="c6a5b-149">Référence de package à `Microsoft.NET.Test.Sdk` (infrastructure de tests .NET)</span><span class="sxs-lookup"><span data-stu-id="c6a5b-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="c6a5b-150">Référence de package à `xunit` (framework de tests xUnit)</span><span class="sxs-lookup"><span data-stu-id="c6a5b-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="c6a5b-151">Référence de package à `xunit.runner.visualstudio` (Test Runner)</span><span class="sxs-lookup"><span data-stu-id="c6a5b-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="c6a5b-152">Référence de projet à `NewTypes` (code à tester)</span><span class="sxs-lookup"><span data-stu-id="c6a5b-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="c6a5b-153">Renommez *UnitTest1.cs* en *PetTests.cs* et remplacez le code dans le fichier par le suivant :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="c6a5b-154">Exercice facultatif : Si vous avez précédemment ajouté un type `Bird` qui envoie un `Tweet!` au propriétaire, ajoutez une méthode de test au fichier *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, pour vérifier que la méthode `TalkToOwner` fonctionne correctement pour le type `Bird`.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="c6a5b-155">Bien que l’on s’attende à ce que les valeurs `expected` et `actual` soient identiques, une assertion initiale avec les vérifications `Assert.NotEqual` spécifie que ces valeurs *ne sont pas égales*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="c6a5b-156">Commencez toujours par créer un test en le faisant échouer pour vérifier sa logique.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="c6a5b-157">Après avoir vérifié que le test échoue, modifiez l’assertion pour que le test réussisse.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="c6a5b-158">Le code suivant montre la structure complète du projet :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-158">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="c6a5b-159">Démarrez dans le répertoire *test/NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="c6a5b-160">Restaurer le projet [`dotnet restore`](../tools/dotnet-restore.md) d’essai avec la commande.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="c6a5b-161">Exécutez les [`dotnet test`](../tools/dotnet-test.md) tests avec la commande.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="c6a5b-162">Cette commande démarre le Test Runner spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c6a5b-163">Comme prévu, les tests échouent et la console affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="c6a5b-164">Remplacez les assertions de vos tests `Assert.NotEqual` par `Assert.Equal` :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="c6a5b-165">Réexécutez les tests avec la commande `dotnet test` et observez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c6a5b-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="c6a5b-166">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-166">Testing passes.</span></span> <span data-ttu-id="c6a5b-167">Les méthodes des types d’animaux domestiques retournent des valeurs correctes quand elles communiquent avec le propriétaire.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="c6a5b-168">Vous avez appris les techniques permettant d’organiser et de tester des projets à l’aide de xUnit.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="c6a5b-169">Vous pouvez maintenant les mettre en pratique dans vos propres projets.</span><span class="sxs-lookup"><span data-stu-id="c6a5b-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="c6a5b-170">*Codez bien !*</span><span class="sxs-lookup"><span data-stu-id="c6a5b-170">*Happy coding!*</span></span>
