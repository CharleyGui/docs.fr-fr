---
title: Effectuer des tests unitaires de C# avec MSTest et .NET Core
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240907"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="72021-103">Effectuer des tests unitaires de C# avec MSTest et .NET Core</span><span class="sxs-lookup"><span data-stu-id="72021-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="72021-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="72021-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="72021-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="72021-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="72021-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="72021-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="72021-107">Créer le projet source</span><span class="sxs-lookup"><span data-stu-id="72021-107">Create the source project</span></span>

<span data-ttu-id="72021-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="72021-108">Open a shell window.</span></span> <span data-ttu-id="72021-109">Créez un répertoire appelé *unit-testing-using-nunit* pour contenir la solution.</span><span class="sxs-lookup"><span data-stu-id="72021-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="72021-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer un fichier de solution pour la bibliothèque de classes et le projet de test.</span><span class="sxs-lookup"><span data-stu-id="72021-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="72021-111">Ensuite, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="72021-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="72021-112">Vous disposez de la structure de répertoire et de fichiers suivante :</span><span class="sxs-lookup"><span data-stu-id="72021-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="72021-113">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="72021-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="72021-114">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="72021-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="72021-115">Créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="72021-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="72021-116">Accédez de nouveau au répertoire *unit-testing-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="72021-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="72021-117">Exécutez [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="72021-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="72021-118">Créer le projet de test</span><span class="sxs-lookup"><span data-stu-id="72021-118">Create the test project</span></span>

<span data-ttu-id="72021-119">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="72021-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="72021-120">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="72021-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="72021-121">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new mstest`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="72021-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="72021-122">La commande dotnet new crée un projet de test qui utilise MSTest comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="72021-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="72021-123">Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="72021-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="72021-124">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="72021-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="72021-125">À l’étape précédente, `dotnet new` a ajouté le SDK MSTest, le framework de test MSTest et le Test Runner MSTest.</span><span class="sxs-lookup"><span data-stu-id="72021-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="72021-126">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="72021-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="72021-127">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="72021-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="72021-128">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="72021-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="72021-129">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="72021-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="72021-130">Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="72021-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="72021-131">Créer le premier test</span><span class="sxs-lookup"><span data-stu-id="72021-131">Create the first test</span></span>

<span data-ttu-id="72021-132">Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="72021-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="72021-133">Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="72021-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="72021-134">L’[attribut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) désigne une classe qui contient des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="72021-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="72021-135">L’[attribut TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indique une méthode qui est une méthode de test.</span><span class="sxs-lookup"><span data-stu-id="72021-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="72021-136">Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="72021-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="72021-137">Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="72021-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="72021-138">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="72021-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="72021-139">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="72021-139">Your test fails.</span></span> <span data-ttu-id="72021-140">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="72021-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="72021-141">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="72021-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="72021-142">Dans le répertoire *unit-testing-using-mstest*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="72021-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="72021-143">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="72021-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="72021-144">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="72021-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="72021-145">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="72021-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="72021-146">Ajouter des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="72021-146">Add more features</span></span>

<span data-ttu-id="72021-147">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="72021-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="72021-148">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="72021-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="72021-149">Vous pouvez ajouter de nouveaux tests avec l’[attribut TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="72021-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="72021-150">D’autres attributs MSTest vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="72021-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="72021-151">L’[attribut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="72021-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="72021-152">Vous pouvez utiliser l’[attribut DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="72021-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="72021-153">Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer un test unique piloté par les données.</span><span class="sxs-lookup"><span data-stu-id="72021-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="72021-154">Le test piloté par les données est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="72021-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="72021-155">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="72021-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="72021-156">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="72021-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="72021-157">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="72021-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="72021-158">Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="72021-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="72021-159">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="72021-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="72021-160">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="72021-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="72021-161">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="72021-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="72021-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72021-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="72021-163">Utiliser le framework MSTest dans les tests unitaires</span><span class="sxs-lookup"><span data-stu-id="72021-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="72021-164">Documentation du framework de test MSTest V2</span><span class="sxs-lookup"><span data-stu-id="72021-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
