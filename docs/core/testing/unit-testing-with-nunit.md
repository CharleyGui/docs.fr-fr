---
title: Effectuer des tests unitaires de C# avec NUnit et .NET Core
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240881"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="4f97f-103">Effectuer des tests unitaires de C# avec NUnit et .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f97f-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="4f97f-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="4f97f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="4f97f-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="4f97f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="4f97f-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4f97f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="4f97f-107">Composants requis</span><span class="sxs-lookup"><span data-stu-id="4f97f-107">Prerequisites</span></span>

- <span data-ttu-id="4f97f-108">[Kit SDK .NET Core 2.1](https://dotnet.microsoft.com/download) (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="4f97f-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="4f97f-109">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="4f97f-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="4f97f-110">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="4f97f-110">Creating the source project</span></span>

<span data-ttu-id="4f97f-111">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="4f97f-111">Open a shell window.</span></span> <span data-ttu-id="4f97f-112">Créez un répertoire appelé *unit-testing-using-nunit* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="4f97f-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="4f97f-113">Dans ce nouveau répertoire, exécutez la commande suivante afin de créer un fichier solution pour la bibliothèque de classes et le projet de test :</span><span class="sxs-lookup"><span data-stu-id="4f97f-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="4f97f-114">Ensuite, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="4f97f-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="4f97f-115">La structure de répertoire et de fichiers est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4f97f-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="4f97f-116">Accédez au répertoire *PrimeService* et exécutez la commande suivante pour créer le projet source :</span><span class="sxs-lookup"><span data-stu-id="4f97f-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib
```

<span data-ttu-id="4f97f-117">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="4f97f-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="4f97f-118">Créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="4f97f-118">You create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="4f97f-119">Accédez de nouveau au répertoire *unit-testing-using-nunit*.</span><span class="sxs-lookup"><span data-stu-id="4f97f-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="4f97f-120">Exécutez la commande suivante pour ajouter le projet de la bibliothèque de classes à la solution :</span><span class="sxs-lookup"><span data-stu-id="4f97f-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="4f97f-121">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="4f97f-121">Creating the test project</span></span>

<span data-ttu-id="4f97f-122">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="4f97f-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="4f97f-123">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="4f97f-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="4f97f-124">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4f97f-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit
```

<span data-ttu-id="4f97f-125">La commande [dotnet new](../tools/dotnet-new.md) crée un projet de test qui utilise NUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="4f97f-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="4f97f-126">Le modèle généré configure Test Runner dans le fichier *PrimeService.Tests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="4f97f-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="4f97f-127">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="4f97f-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="4f97f-128">`dotnet new` dans l’étape précédente a ajouté le kit SDK de test Microsoft, le framework de test NUnit et l’adaptateur de test NUnit.</span><span class="sxs-lookup"><span data-stu-id="4f97f-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="4f97f-129">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="4f97f-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="4f97f-130">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="4f97f-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="4f97f-131">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="4f97f-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="4f97f-132">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="4f97f-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="4f97f-133">Exécutez la commande suivante dans le répertoire *unit-testing-using-nunit* :</span><span class="sxs-lookup"><span data-stu-id="4f97f-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="4f97f-134">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="4f97f-134">Creating the first test</span></span>

<span data-ttu-id="4f97f-135">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="4f97f-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="4f97f-136">Dans le répertoire *PrimeService.Tests*, renommez le fichier *UnitTest1.cs* en *PrimeService_IsPrimeShould.cs*, puis remplacez tout son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4f97f-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

<span data-ttu-id="4f97f-137">L’attribut `[TestFixture]` désigne une classe qui contient des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="4f97f-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="4f97f-138">L’attribut `[Test]` indique une méthode qui est une méthode de test.</span><span class="sxs-lookup"><span data-stu-id="4f97f-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="4f97f-139">Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="4f97f-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="4f97f-140">Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="4f97f-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="4f97f-141">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="4f97f-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="4f97f-142">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="4f97f-142">Your test fails.</span></span> <span data-ttu-id="4f97f-143">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="4f97f-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="4f97f-144">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="4f97f-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="4f97f-145">Dans le répertoire *unit-testing-using-nunit*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="4f97f-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="4f97f-146">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="4f97f-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="4f97f-147">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="4f97f-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="4f97f-148">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="4f97f-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="4f97f-149">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4f97f-149">Adding more features</span></span>

<span data-ttu-id="4f97f-150">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="4f97f-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="4f97f-151">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="4f97f-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="4f97f-152">Vous pouvez ajouter de nouveaux tests avec l’attribut `[Test]`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="4f97f-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="4f97f-153">D’autres attributs NUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="4f97f-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="4f97f-154">Un attribut `[TestCase]` permet de créer une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="4f97f-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="4f97f-155">Vous pouvez utiliser l’attribut `[TestCase]` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="4f97f-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="4f97f-156">Au lieu de créer des tests, appliquez cet attribut pour créer un test unique piloté par les données.</span><span class="sxs-lookup"><span data-stu-id="4f97f-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="4f97f-157">Le test piloté par les données est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="4f97f-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="4f97f-158">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="4f97f-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="4f97f-159">Pour que tous les tests réussissent, changez la clause `if` au début de la méthode `Main` dans le fichier *PrimeService.cs* :</span><span class="sxs-lookup"><span data-stu-id="4f97f-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="4f97f-160">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="4f97f-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="4f97f-161">Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="4f97f-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="4f97f-162">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4f97f-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="4f97f-163">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="4f97f-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="4f97f-164">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="4f97f-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
