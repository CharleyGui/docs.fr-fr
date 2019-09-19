---
title: Effectuer des tests unitaires F# dans .NET Core avec dotnet test et MSTest
description: Apprenez les concepts des tests unitaires pour F# dans .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 68878073b031d155c9ff67f24ed950570e666523
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117006"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="93cc2-103">Effectuer des tests unitaires des bibliothèques F# dans .NET Core à l’aide de dotnet test et de MSTest</span><span class="sxs-lookup"><span data-stu-id="93cc2-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="93cc2-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="93cc2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="93cc2-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="93cc2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="93cc2-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="93cc2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="93cc2-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="93cc2-107">Creating the source project</span></span>

<span data-ttu-id="93cc2-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="93cc2-108">Open a shell window.</span></span> <span data-ttu-id="93cc2-109">Créez un répertoire appelé *unit-testing-with-fsharp* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="93cc2-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="93cc2-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution.</span><span class="sxs-lookup"><span data-stu-id="93cc2-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="93cc2-111">Ceci permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="93cc2-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="93cc2-112">Dans le répertoire de la solution, créez un répertoire *MathService*.</span><span class="sxs-lookup"><span data-stu-id="93cc2-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="93cc2-113">La structure du répertoire et des fichiers jusqu’ici est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="93cc2-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="93cc2-114">Accédez au répertoire *MathService* et exécutez [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="93cc2-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="93cc2-115">Vous allez créer une implémentation défaillante du service Math :</span><span class="sxs-lookup"><span data-stu-id="93cc2-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="93cc2-116">Accédez de nouveau au répertoire *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="93cc2-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="93cc2-117">Exécutez [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="93cc2-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="93cc2-118">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="93cc2-118">Creating the test project</span></span>

<span data-ttu-id="93cc2-119">Ensuite, créez le répertoire *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="93cc2-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="93cc2-120">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="93cc2-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="93cc2-121">Accédez au répertoire *MathService.Tests* et créez un projet à l’aide de [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="93cc2-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="93cc2-122">Vous obtenez un projet de test qui utilise MSTest comme framework de test.</span><span class="sxs-lookup"><span data-stu-id="93cc2-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="93cc2-123">Le modèle généré configure le Test Runner dans *MathServiceTests.fsproj* :</span><span class="sxs-lookup"><span data-stu-id="93cc2-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="93cc2-124">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="93cc2-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="93cc2-125">`dotnet new` a ajouté MSTest et le Runner MSTest à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="93cc2-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="93cc2-126">Maintenant, ajoutez la bibliothèque de classes `MathService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="93cc2-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="93cc2-127">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="93cc2-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="93cc2-128">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="93cc2-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="93cc2-129">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="93cc2-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="93cc2-130">Exécutez [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="93cc2-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="93cc2-131">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="93cc2-131">Creating the first test</span></span>

<span data-ttu-id="93cc2-132">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="93cc2-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="93cc2-133">Ouvrez *Tests.fs* et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="93cc2-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="93cc2-134">L’attribut `[<TestClass>]` désigne une classe qui contient des tests.</span><span class="sxs-lookup"><span data-stu-id="93cc2-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="93cc2-135">L’attribut `[<TestMethod>]` désigne une méthode de test qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="93cc2-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="93cc2-136">À partir du répertoire *unit-testing-with-fsharp*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="93cc2-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="93cc2-137">Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="93cc2-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="93cc2-138">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="93cc2-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="93cc2-139">Ces deux tests illustrent les tests de réussite et d’échec les plus basiques.</span><span class="sxs-lookup"><span data-stu-id="93cc2-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="93cc2-140">`My test` réussit et `Fail every time` échoue.</span><span class="sxs-lookup"><span data-stu-id="93cc2-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="93cc2-141">À présent, créez un test pour la méthode `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="93cc2-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="93cc2-142">La méthode `squaresOfOdds` retourne une liste des carrés de toutes les valeurs de nombre entier impair qui font partie de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="93cc2-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="93cc2-143">Au lieu d’essayer d’écrire toutes ces fonctions simultanément, vous pouvez créer de manière itérative des tests qui valident les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="93cc2-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="93cc2-144">La réussite de chaque test correspond à la création de la fonctionnalité nécessaire pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="93cc2-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="93cc2-145">Le test le plus simple que nous pouvons écrire consiste à appeler `squaresOfOdds` avec tous les nombres pairs, où le résultat doit être une séquence vide de nombres entiers.</span><span class="sxs-lookup"><span data-stu-id="93cc2-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="93cc2-146">Voici ce test :</span><span class="sxs-lookup"><span data-stu-id="93cc2-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="93cc2-147">Notez que la séquence `expected` a été convertie en liste.</span><span class="sxs-lookup"><span data-stu-id="93cc2-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="93cc2-148">La bibliothèque MSTest s’appuie sur de nombreux types .NET standard.</span><span class="sxs-lookup"><span data-stu-id="93cc2-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="93cc2-149">Cette dépendance signifie que votre interface publique et les résultats attendus prennent en charge <xref:System.Collections.ICollection> plutôt que <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="93cc2-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="93cc2-150">Lorsque vous exécutez le test, vous constatez que votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="93cc2-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="93cc2-151">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="93cc2-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="93cc2-152">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `Mathservice` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="93cc2-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="93cc2-153">Dans le répertoire *unit-testing-with-fsharp*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="93cc2-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="93cc2-154">La commande `dotnet test` exécute une build pour le projet `MathService` puis pour le projet `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="93cc2-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="93cc2-155">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="93cc2-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="93cc2-156">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="93cc2-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="93cc2-157">Finalisation des spécifications</span><span class="sxs-lookup"><span data-stu-id="93cc2-157">Completing the requirements</span></span>

<span data-ttu-id="93cc2-158">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="93cc2-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="93cc2-159">Le cas simple suivant fonctionne avec une séquence dont le seul nombre impair est `1`.</span><span class="sxs-lookup"><span data-stu-id="93cc2-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="93cc2-160">Le nombre 1 est plus facile, car le carré de 1 est 1.</span><span class="sxs-lookup"><span data-stu-id="93cc2-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="93cc2-161">Voici ce test suivant :</span><span class="sxs-lookup"><span data-stu-id="93cc2-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="93cc2-162">L’exécution de `dotnet test` fait échouer le nouveau test.</span><span class="sxs-lookup"><span data-stu-id="93cc2-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="93cc2-163">Vous devez mettre à jour la méthode `squaresOfOdds` pour gérer ce nouveau test.</span><span class="sxs-lookup"><span data-stu-id="93cc2-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="93cc2-164">Vous devez filtrer tous les nombres pairs hors de la séquence pour que ce test réussisse.</span><span class="sxs-lookup"><span data-stu-id="93cc2-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="93cc2-165">Pour ce faire, vous pouvez écrire une petite fonction de filtre et utiliser `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="93cc2-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="93cc2-166">Notez l’appel à `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="93cc2-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="93cc2-167">Ceci crée une liste qui implémente l’interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="93cc2-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="93cc2-168">Encore une étape : calculer le carré de chaque nombre impair.</span><span class="sxs-lookup"><span data-stu-id="93cc2-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="93cc2-169">Commencez par écrire un nouveau test :</span><span class="sxs-lookup"><span data-stu-id="93cc2-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="93cc2-170">Vous pouvez corriger le test en redirigeant la séquence filtrée via une opération de mappage pour calculer le carré de chaque nombre impair :</span><span class="sxs-lookup"><span data-stu-id="93cc2-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="93cc2-171">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="93cc2-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="93cc2-172">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="93cc2-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="93cc2-173">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="93cc2-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
