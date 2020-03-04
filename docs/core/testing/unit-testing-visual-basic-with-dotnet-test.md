---
title: Effectuer des tests unitaires sur Visual Basic dans .NET Core avec dotnet test et xUnit
description: Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de dotnet test et de xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240946"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="279b0-103">Effectuer des tests unitaires sur les bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de xUnit</span><span class="sxs-lookup"><span data-stu-id="279b0-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="279b0-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="279b0-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="279b0-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="279b0-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="279b0-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="279b0-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="279b0-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="279b0-107">Creating the source project</span></span>

<span data-ttu-id="279b0-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="279b0-108">Open a shell window.</span></span> <span data-ttu-id="279b0-109">Créez un répertoire appelé *unit-testing-vb-using-dotnet-test* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="279b0-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="279b0-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution.</span><span class="sxs-lookup"><span data-stu-id="279b0-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="279b0-111">Cette méthode permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="279b0-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="279b0-112">Dans le répertoire de la solution, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="279b0-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="279b0-113">Vous disposez de la structure du répertoire et des fichiers suivante :</span><span class="sxs-lookup"><span data-stu-id="279b0-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="279b0-114">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="279b0-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="279b0-115">Renommez *Class1.VB* en *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="279b0-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="279b0-116">Créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="279b0-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="279b0-117">Accédez de nouveau au répertoire *unit-testing-vb-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="279b0-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="279b0-118">Exécutez [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="279b0-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="279b0-119">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="279b0-119">Creating the test project</span></span>

<span data-ttu-id="279b0-120">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="279b0-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="279b0-121">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="279b0-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="279b0-122">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="279b0-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="279b0-123">Cette commande crée un projet de test qui utilise xUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="279b0-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="279b0-124">Le modèle généré configure le Test Runner dans *PrimeServiceTests.vbproj* :</span><span class="sxs-lookup"><span data-stu-id="279b0-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="279b0-125">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="279b0-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="279b0-126">`dotnet new` a ajouté xUnit et le Test Runner xUnit à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="279b0-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="279b0-127">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="279b0-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="279b0-128">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="279b0-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="279b0-129">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="279b0-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="279b0-130">Le dossier final se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="279b0-130">You have the following final folder layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="279b0-131">Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-vb-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="279b0-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="279b0-132">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="279b0-132">Creating the first test</span></span>

<span data-ttu-id="279b0-133">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="279b0-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="279b0-134">Supprimez *UnitTest1.vb* du répertoire *PrimeService.Tests* et créez un fichier Visual Basic nommé *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="279b0-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="279b0-135">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="279b0-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="279b0-136">L’attribut `<Fact>` désigne une méthode de test qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="279b0-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="279b0-137">À partir de *unit-testing-using-dotnet-test*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="279b0-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="279b0-138">Le Test Runner xUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="279b0-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="279b0-139">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="279b0-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="279b0-140">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="279b0-140">Your test fails.</span></span> <span data-ttu-id="279b0-141">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="279b0-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="279b0-142">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="279b0-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="279b0-143">Dans le répertoire *unit-testing-vb-using-dotnet-test*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="279b0-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="279b0-144">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="279b0-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="279b0-145">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="279b0-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="279b0-146">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="279b0-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="279b0-147">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="279b0-147">Adding more features</span></span>

<span data-ttu-id="279b0-148">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="279b0-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="279b0-149">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="279b0-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="279b0-150">Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `<Fact>`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="279b0-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="279b0-151">D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="279b0-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="279b0-152">L’attribut `<Theory>` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="279b0-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="279b0-153">Vous pouvez utiliser l’attribut `<InlineData>` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="279b0-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="279b0-154">Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer une théorie unique.</span><span class="sxs-lookup"><span data-stu-id="279b0-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="279b0-155">La théorie est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="279b0-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="279b0-156">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="279b0-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="279b0-157">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="279b0-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="279b0-158">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="279b0-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="279b0-159">Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="279b0-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="279b0-160">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="279b0-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="279b0-161">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="279b0-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="279b0-162">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="279b0-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
