---
title: Effectuer des tests unitaires F# dans .NET Core avec dotnet test et NUnit
description: Apprenez les concepts des tests unitaires pour F# dans .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 9a1b4bb7e5e705cf1c71cd44827d4a2e0a3f8cf6
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656473"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="8c7bf-103">Effectuer des tests unitaires des bibliothèques F# dans .NET Core à l’aide de dotnet test et de NUnit</span><span class="sxs-lookup"><span data-stu-id="8c7bf-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="8c7bf-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="8c7bf-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="8c7bf-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="8c7bf-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="8c7bf-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="8c7bf-107">Prerequisites</span></span>

- <span data-ttu-id="8c7bf-108">[Kit SDK .NET Core 2.1](https://dotnet.microsoft.com/download) (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="8c7bf-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="8c7bf-109">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="8c7bf-110">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="8c7bf-110">Creating the source project</span></span>

<span data-ttu-id="8c7bf-111">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-111">Open a shell window.</span></span> <span data-ttu-id="8c7bf-112">Créez un répertoire appelé *unit-testing-with-fsharp* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="8c7bf-113">Dans ce nouveau répertoire, exécutez la commande suivante afin de créer un fichier solution pour la bibliothèque de classes et le projet de test :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="8c7bf-114">Ensuite, créez un répertoire *MathService*.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="8c7bf-115">La structure de répertoire et de fichiers est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="8c7bf-116">Faites de *MathService* le répertoire actif et exécutez la commande suivante pour créer le projet source :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="8c7bf-117">Créez une implémentation défaillante du service Math :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="8c7bf-118">Accédez de nouveau au répertoire *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="8c7bf-119">Exécutez la commande suivante pour ajouter le projet de la bibliothèque de classes à la solution :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="8c7bf-120">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="8c7bf-120">Creating the test project</span></span>

<span data-ttu-id="8c7bf-121">Ensuite, créez le répertoire *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="8c7bf-122">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="8c7bf-123">Faites de *MathService.Tests* le répertoire actif et créez un projet avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="8c7bf-124">Vous obtenez un projet de test qui utilise NUnit comme framework de test.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="8c7bf-125">Le modèle généré configure le Test Runner dans *MathServiceTests.fsproj* :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="8c7bf-126">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="8c7bf-127">`dotnet new` dans l’étape précédente a ajouté NUnit et l’adaptateur de test NUnit.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="8c7bf-128">Maintenant, ajoutez la bibliothèque de classes `MathService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="8c7bf-129">Utiliser la commande `dotnet add reference` :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="8c7bf-130">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="8c7bf-131">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="8c7bf-132">Exécutez la commande suivante dans le répertoire *unit-testing-with-fsharp* :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="8c7bf-133">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="8c7bf-133">Creating the first test</span></span>

<span data-ttu-id="8c7bf-134">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="8c7bf-135">Ouvrez *UnitTest1.fs* et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-135">Open *UnitTest1.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="8c7bf-136">L’attribut `[<TestFixture>]` désigne une classe qui contient des tests.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="8c7bf-137">L’attribut `[<Test>]` désigne une méthode de test qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="8c7bf-138">À partir du répertoire *unit-testing-with-fsharp*, exécutez `dotnet test` pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="8c7bf-139">Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="8c7bf-140">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="8c7bf-141">Ces deux tests illustrent les tests de réussite et d’échec les plus basiques.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="8c7bf-142">`My test` réussit et `Fail every time` échoue.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="8c7bf-143">À présent, créez un test pour la méthode `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="8c7bf-144">La méthode `squaresOfOdds` retourne une séquence des carrés de toutes les valeurs de nombre entier impair qui font partie de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="8c7bf-145">Au lieu d’essayer d’écrire toutes ces fonctions simultanément, vous pouvez créer de manière itérative des tests qui valident les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="8c7bf-146">La réussite de chaque test correspond à la création de la fonctionnalité nécessaire pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="8c7bf-147">Le test le plus simple que nous pouvons écrire consiste à appeler `squaresOfOdds` avec tous les nombres pairs, où le résultat doit être une séquence vide de nombres entiers.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="8c7bf-148">Voici ce test :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c7bf-149">Notez que la séquence `expected` a été convertie en liste.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="8c7bf-150">Le framework NUnit s’appuie sur de nombreux types .NET standard.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="8c7bf-151">Cette dépendance signifie que votre interface publique et les résultats attendus prennent en charge <xref:System.Collections.ICollection> plutôt que <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="8c7bf-152">Lorsque vous exécutez le test, vous constatez que votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="8c7bf-153">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="8c7bf-154">Écrivez le code fonctionnel le plus simple possible dans la classe *Library.fs* de votre projet MathService, de façon à ce que ce test réussisse :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="8c7bf-155">Dans le répertoire *unit-testing-with-fsharp*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="8c7bf-156">La commande `dotnet test` exécute une build pour le projet `MathService` puis pour le projet `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="8c7bf-157">Après avoir créé les deux projets, elle exécute vos tests.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="8c7bf-158">À présent, les deux tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="8c7bf-159">Finalisation des spécifications</span><span class="sxs-lookup"><span data-stu-id="8c7bf-159">Completing the requirements</span></span>

<span data-ttu-id="8c7bf-160">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="8c7bf-161">Le cas simple suivant fonctionne avec une séquence dont le seul nombre impair est `1`.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="8c7bf-162">Le nombre 1 est plus facile, car le carré de 1 est 1.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="8c7bf-163">Voici ce test suivant :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c7bf-164">L’exécution de `dotnet test` fait échouer le nouveau test.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="8c7bf-165">Vous devez mettre à jour la méthode `squaresOfOdds` pour gérer ce nouveau test.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="8c7bf-166">Vous devez filtrer tous les nombres pairs hors de la séquence pour que ce test réussisse.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="8c7bf-167">Pour ce faire, vous pouvez écrire une petite fonction de filtre et utiliser `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="8c7bf-168">Notez l’appel à `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="8c7bf-169">Ceci crée une liste qui implémente l’interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="8c7bf-170">Encore une étape : calculer le carré de chaque nombre impair.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="8c7bf-171">Commencez par écrire un nouveau test :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c7bf-172">Vous pouvez corriger le test en redirigeant la séquence filtrée via une opération de mappage pour calculer le carré de chaque nombre impair :</span><span class="sxs-lookup"><span data-stu-id="8c7bf-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="8c7bf-173">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="8c7bf-174">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="8c7bf-175">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c7bf-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c7bf-176">See also</span></span>

- [<span data-ttu-id="8c7bf-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8c7bf-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="8c7bf-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8c7bf-178">dotnet test</span></span>](../tools/dotnet-test.md)
