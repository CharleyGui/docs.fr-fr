---
title: Effectuer des tests unitaires sur Visual Basic dans .NET Core avec dotnet test et NUnit
description: Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de NUnit.
author: rprouse
ms.date: 10/04/2018
ms.custom: seodec18
ms.openlocfilehash: 84287a94504594c731c0fbccf2e61a957a15a36f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626402"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="c5e97-103">Effectuer des tests unitaires sur les bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de NUnit</span><span class="sxs-lookup"><span data-stu-id="c5e97-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="c5e97-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="c5e97-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="c5e97-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="c5e97-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="c5e97-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c5e97-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c5e97-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="c5e97-107">Prerequisites</span></span>

- <span data-ttu-id="c5e97-108">[Kit SDK .NET Core 2.1](https://www.microsoft.com/net/download) (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="c5e97-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="c5e97-109">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="c5e97-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="c5e97-110">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="c5e97-110">Creating the source project</span></span>

<span data-ttu-id="c5e97-111">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="c5e97-111">Open a shell window.</span></span> <span data-ttu-id="c5e97-112">Créez un répertoire appelé *unit-testing-vb-nunit* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="c5e97-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="c5e97-113">Dans ce nouveau répertoire, exécutez la commande suivante afin de créer un fichier solution pour la bibliothèque de classes et le projet de test :</span><span class="sxs-lookup"><span data-stu-id="c5e97-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="c5e97-114">Ensuite, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="c5e97-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="c5e97-115">La structure de fichiers est pour le moment la suivante :</span><span class="sxs-lookup"><span data-stu-id="c5e97-115">The following outline shows the file structure so far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="c5e97-116">Accédez au répertoire *PrimeService* et exécutez la commande suivante pour créer le projet source :</span><span class="sxs-lookup"><span data-stu-id="c5e97-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="c5e97-117">Renommez *Class1.VB* en *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="c5e97-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="c5e97-118">Créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="c5e97-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="c5e97-119">Remplacez de nouveau le répertoire par le répertoire *unit-testing-vb-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="c5e97-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="c5e97-120">Exécutez la commande suivante pour ajouter le projet de la bibliothèque de classes à la solution :</span><span class="sxs-lookup"><span data-stu-id="c5e97-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="c5e97-121">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="c5e97-121">Creating the test project</span></span>

<span data-ttu-id="c5e97-122">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="c5e97-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="c5e97-123">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="c5e97-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="c5e97-124">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c5e97-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="c5e97-125">La commande [dotnet new](../tools/dotnet-new.md) crée un projet de test qui utilise NUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="c5e97-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="c5e97-126">Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.vbproj* :</span><span class="sxs-lookup"><span data-stu-id="c5e97-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="c5e97-127">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="c5e97-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="c5e97-128">`dotnet new` dans l’étape précédente a ajouté NUnit et l’adaptateur de test NUnit.</span><span class="sxs-lookup"><span data-stu-id="c5e97-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="c5e97-129">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="c5e97-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="c5e97-130">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="c5e97-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="c5e97-131">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="c5e97-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="c5e97-132">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c5e97-132">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="c5e97-133">Exécutez la commande suivante dans le répertoire *unit-testing-vb-nunit* :</span><span class="sxs-lookup"><span data-stu-id="c5e97-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="c5e97-134">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="c5e97-134">Creating the first test</span></span>

<span data-ttu-id="c5e97-135">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="c5e97-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="c5e97-136">Dans le répertoire *PrimeService.Tests*, renommez le fichier *UnitTest1.vb* en *PrimeService_IsPrimeShould.VB*, puis remplacez tout son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c5e97-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="c5e97-137">L’attribut `<TestFixture>` désigne une classe qui contient des tests.</span><span class="sxs-lookup"><span data-stu-id="c5e97-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="c5e97-138">L’attribut `<Test>` désigne une méthode qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="c5e97-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="c5e97-139">À partir de *unit-testing-vb-nunit*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="c5e97-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="c5e97-140">Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="c5e97-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="c5e97-141">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="c5e97-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="c5e97-142">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="c5e97-142">Your test fails.</span></span> <span data-ttu-id="c5e97-143">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="c5e97-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="c5e97-144">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="c5e97-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="c5e97-145">Dans le répertoire *unit-testing-vb-nunit*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="c5e97-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="c5e97-146">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="c5e97-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="c5e97-147">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="c5e97-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="c5e97-148">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="c5e97-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="c5e97-149">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c5e97-149">Adding more features</span></span>

<span data-ttu-id="c5e97-150">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="c5e97-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="c5e97-151">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="c5e97-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="c5e97-152">Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `<Test>`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="c5e97-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="c5e97-153">D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="c5e97-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="c5e97-154">L’attribut `<TestCase>` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="c5e97-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="c5e97-155">Vous pouvez utiliser l’attribut `<TestCase>` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="c5e97-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="c5e97-156">Au lieu de créer des tests, appliquez ces deux attributs pour créer une série de tests qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="c5e97-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="c5e97-157">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="c5e97-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="c5e97-158">Pour que tous les tests réussissent, changez la clause `if` au début de la méthode `Main` dans le fichier *PrimeServices.cs* :</span><span class="sxs-lookup"><span data-stu-id="c5e97-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="c5e97-159">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="c5e97-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="c5e97-160">Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="c5e97-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="c5e97-161">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="c5e97-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="c5e97-162">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="c5e97-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="c5e97-163">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="c5e97-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
