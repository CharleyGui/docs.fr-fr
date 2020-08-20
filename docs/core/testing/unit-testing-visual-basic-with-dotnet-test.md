---
title: Effectuer des tests unitaires sur Visual Basic dans .NET Core avec dotnet test et xUnit
description: Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de dotnet test et de xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d384bf08f0b6031a519a8430c876eafc05d03a2e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656421"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="4e27c-103">Effectuer des tests unitaires sur les bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de xUnit</span><span class="sxs-lookup"><span data-stu-id="4e27c-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="4e27c-104">Ce didacticiel montre comment générer une solution contenant un projet de test unitaire et un projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4e27c-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="4e27c-105">Pour suivre le didacticiel à l’aide d’une solution prédéfinie, [Affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="4e27c-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="4e27c-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="4e27c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="4e27c-107">Créez la solution</span><span class="sxs-lookup"><span data-stu-id="4e27c-107">Create the solution</span></span>

<span data-ttu-id="4e27c-108">Dans cette section, une solution qui contient les projets source et de test est créée.</span><span class="sxs-lookup"><span data-stu-id="4e27c-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="4e27c-109">La solution terminée présente la structure de répertoire suivante :</span><span class="sxs-lookup"><span data-stu-id="4e27c-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="4e27c-110">Les instructions suivantes fournissent les étapes permettant de créer la solution de test.</span><span class="sxs-lookup"><span data-stu-id="4e27c-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="4e27c-111">Consultez [commandes pour créer une solution de test](#create-test-cmd) pour obtenir des instructions sur la création d’une solution de test en une seule étape.</span><span class="sxs-lookup"><span data-stu-id="4e27c-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="4e27c-112">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="4e27c-112">Open a shell window.</span></span>
* <span data-ttu-id="4e27c-113">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e27c-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="4e27c-114">La [`dotnet new sln`](../tools/dotnet-new.md) commande crée une nouvelle solution dans le répertoire *Unit-testing-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="4e27c-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="4e27c-115">Remplacez le répertoire par le dossier *Unit-testing-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="4e27c-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="4e27c-116">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e27c-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="4e27c-117">La [`dotnet new classlib`](../tools/dotnet-new.md) commande crée un projet de bibliothèque de classes dans le dossier *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="4e27c-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="4e27c-118">La nouvelle bibliothèque de classes contiendra le code à tester.</span><span class="sxs-lookup"><span data-stu-id="4e27c-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="4e27c-119">Renommez *Class1. vb* en *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="4e27c-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="4e27c-120">Remplacez le code dans *PrimeService. vb* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="4e27c-121">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="4e27c-121">The preceding code:</span></span>
  * <span data-ttu-id="4e27c-122">Lève une exception <xref:System.NotImplementedException> avec un message indiquant qu’elle n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="4e27c-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="4e27c-123">Est mis à jour ultérieurement dans le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="4e27c-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="4e27c-124">Dans le répertoire *Unit-testing-using-dotnet-test* , exécutez la commande suivante pour ajouter le projet de bibliothèque de classes à la solution :</span><span class="sxs-lookup"><span data-stu-id="4e27c-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="4e27c-125">Créez le projet *PrimeService. tests* en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e27c-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="4e27c-126">La commande précédente :</span><span class="sxs-lookup"><span data-stu-id="4e27c-126">The preceding command:</span></span>
  * <span data-ttu-id="4e27c-127">Crée le projet *PrimeService. tests* dans le répertoire *PrimeService. tests* .</span><span class="sxs-lookup"><span data-stu-id="4e27c-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="4e27c-128">Le projet de test utilise [xUnit](https://xunit.net/) comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="4e27c-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="4e27c-129">Configure Test Runner en ajoutant les `<PackageReference />` éléments suivants au fichier projet :</span><span class="sxs-lookup"><span data-stu-id="4e27c-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="4e27c-130">« Microsoft. NET. test. Sdk »</span><span class="sxs-lookup"><span data-stu-id="4e27c-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="4e27c-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="4e27c-131">"xunit"</span></span>
    * <span data-ttu-id="4e27c-132">« xUnit. Runner. VisualStudio »</span><span class="sxs-lookup"><span data-stu-id="4e27c-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="4e27c-133">Ajoutez le projet de test au fichier solution en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e27c-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="4e27c-134">Ajoutez la `PrimeService` bibliothèque de classes en tant que dépendance au projet *PrimeService. tests* :</span><span class="sxs-lookup"><span data-stu-id="4e27c-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="4e27c-135">Commandes pour créer la solution</span><span class="sxs-lookup"><span data-stu-id="4e27c-135">Commands to create the solution</span></span>

<span data-ttu-id="4e27c-136">Cette section résume toutes les commandes de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="4e27c-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="4e27c-137">Ignorez cette section si vous avez effectué les étapes décrites dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="4e27c-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="4e27c-138">Les commandes suivantes créent la solution de test sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="4e27c-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="4e27c-139">Pour macOS et UNIX, mettez à jour la `ren` commande vers la version du système d’exploitation de `ren` pour renommer un fichier :</span><span class="sxs-lookup"><span data-stu-id="4e27c-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="4e27c-140">Suivez les instructions pour « remplacez le code dans *PrimeService. vb* par le code suivant » dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="4e27c-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="4e27c-141">Créer un test</span><span class="sxs-lookup"><span data-stu-id="4e27c-141">Create a test</span></span>

<span data-ttu-id="4e27c-142">Une approche courante du développement piloté par les tests (TDD) consiste à écrire un test avant d’implémenter le code cible.</span><span class="sxs-lookup"><span data-stu-id="4e27c-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="4e27c-143">Ce didacticiel utilise l’approche TDD.</span><span class="sxs-lookup"><span data-stu-id="4e27c-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="4e27c-144">La `IsPrime` méthode peut être appelée, mais elle n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="4e27c-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="4e27c-145">Un appel de test à `IsPrime` échoue.</span><span class="sxs-lookup"><span data-stu-id="4e27c-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="4e27c-146">Avec TDD, un test est écrit et connu comme ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="4e27c-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="4e27c-147">Le code cible est mis à jour pour que le test réussisse.</span><span class="sxs-lookup"><span data-stu-id="4e27c-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="4e27c-148">Vous continuez à répéter cette approche, en écrivant un test qui a échoué, puis en mettant à jour le code cible pour qu’il réussisse.</span><span class="sxs-lookup"><span data-stu-id="4e27c-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="4e27c-149">Mettez à jour le projet *PrimeService. tests* :</span><span class="sxs-lookup"><span data-stu-id="4e27c-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="4e27c-150">Supprimez *PrimeService. tests/UnitTest1. vb*.</span><span class="sxs-lookup"><span data-stu-id="4e27c-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="4e27c-151">Créez un fichier *PrimeService. tests/PrimeService_IsPrimeShould. vb*  .</span><span class="sxs-lookup"><span data-stu-id="4e27c-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="4e27c-152">Remplacez le code dans *PrimeService_IsPrimeShould. vb* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="4e27c-153">L' `[Fact]` attribut déclare une méthode de test qui est exécutée par Test Runner.</span><span class="sxs-lookup"><span data-stu-id="4e27c-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="4e27c-154">À partir du dossier *PrimeService. tests* , exécutez `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="4e27c-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="4e27c-155">La commande [dotnet test](../tools/dotnet-test.md) génère les deux projets et exécute les tests.</span><span class="sxs-lookup"><span data-stu-id="4e27c-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="4e27c-156">Le test Runner xUnit contient le point d’entrée de programme pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="4e27c-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="4e27c-157">`dotnet test` démarre le testeur de test à l’aide du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="4e27c-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="4e27c-158">Le test échoue car `IsPrime` n’a pas été implémenté.</span><span class="sxs-lookup"><span data-stu-id="4e27c-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="4e27c-159">À l’aide de l’approche TDD, écrivez uniquement le code suffisant pour que ce test soit réussi.</span><span class="sxs-lookup"><span data-stu-id="4e27c-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="4e27c-160">Mettez à jour `IsPrime` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="4e27c-161">Exécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="4e27c-161">Run `dotnet test`.</span></span> <span data-ttu-id="4e27c-162">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="4e27c-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="4e27c-163">Ajouter d’autres tests</span><span class="sxs-lookup"><span data-stu-id="4e27c-163">Add more tests</span></span>

<span data-ttu-id="4e27c-164">Ajoutez des tests de nombre premier pour 0 et-1.</span><span class="sxs-lookup"><span data-stu-id="4e27c-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="4e27c-165">Vous pouvez copier le test précédent et modifier le code suivant pour utiliser 0 et-1 :</span><span class="sxs-lookup"><span data-stu-id="4e27c-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="4e27c-166">La copie du code de test lorsque seul un paramètre change entraîne la duplication du code et l’augmentation des tests.</span><span class="sxs-lookup"><span data-stu-id="4e27c-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="4e27c-167">Les attributs xUnit suivants permettent d’écrire une suite de tests similaires :</span><span class="sxs-lookup"><span data-stu-id="4e27c-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="4e27c-168">`[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="4e27c-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="4e27c-169">L’attribut `[InlineData]` spécifie des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="4e27c-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="4e27c-170">Au lieu de créer de nouveaux tests, appliquez les attributs xUnit précédents pour créer une théorie unique.</span><span class="sxs-lookup"><span data-stu-id="4e27c-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="4e27c-171">Remplacez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="4e27c-172">par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="4e27c-173">Dans le code précédent, `[Theory]` et `[InlineData]` permettent de tester plusieurs valeurs inférieures à deux.</span><span class="sxs-lookup"><span data-stu-id="4e27c-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="4e27c-174">Deux est le plus petit nombre premier.</span><span class="sxs-lookup"><span data-stu-id="4e27c-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="4e27c-175">Exécuter `dotnet test` , deux des tests échouent.</span><span class="sxs-lookup"><span data-stu-id="4e27c-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="4e27c-176">Pour que tous les tests réussissent, mettez à jour la `IsPrime` méthode avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4e27c-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="4e27c-177">Après l’approche TDD, ajoutez d’autres tests ayant échoué, puis mettez à jour le code cible.</span><span class="sxs-lookup"><span data-stu-id="4e27c-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="4e27c-178">Consultez la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et l' [implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="4e27c-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="4e27c-179">La `IsPrime` méthode terminée n’est pas un algorithme efficace pour tester primality.</span><span class="sxs-lookup"><span data-stu-id="4e27c-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4e27c-180">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4e27c-180">Additional resources</span></span>

- [<span data-ttu-id="4e27c-181">Site officiel xUnit.net</span><span class="sxs-lookup"><span data-stu-id="4e27c-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="4e27c-182">Test de la logique de contrôleur dans ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4e27c-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
