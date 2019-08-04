---
title: Effectuer des tests unitaires sur Visual Basic dans .NET Core avec dotnet test et MSTest
description: Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: 6081e7b6b52d85615cfde701e364eb87d69f42bf
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626428"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>Effectuer des tests unitaires pour des bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de MSTest

Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires. Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) avant de commencer. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Création du projet source

Ouvrez une fenêtre d’interpréteur de commandes. Créez un répertoire appelé *unit-testing-vb-mstest* qui contiendra la solution.
Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution. Cette méthode permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.
Dans le répertoire de la solution, créez un répertoire *PrimeService*. Vous disposez de la structure du répertoire et des fichiers suivante :

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) pour créer le projet source. Renommez *Class1.VB* en *PrimeService.VB*. Créez une implémentation défaillante de la classe `PrimeService` :

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Remplacez de nouveau le répertoire par le répertoire *unit-testing-vb-using-mstest*. Exécutez [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.

## <a name="creating-the-test-project"></a>Création du projet de test

Ensuite, créez le répertoire *PrimeService.Tests*. La structure du répertoire est illustrée ci-dessous :

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new mstest -lang VB`](../tools/dotnet-new.md). Cette commande crée un projet de test qui utilise MSTest comme bibliothèque de test. Le modèle généré configure le Test Runner dans *PrimeServiceTests.vbproj* :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires. `dotnet new` a ajouté MSTest et le Runner MSTest à l’étape précédente. Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) sur GitHub.

La solution finale se présente comme suit :

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-vb-mstest*.

## <a name="creating-the-first-test"></a>Création du premier test

Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus. Supprimez *UnitTest1.vb* du répertoire *PrimeService.Tests* et créez un fichier Visual Basic nommé *PrimeService_IsPrimeShould.VB*. Ajoutez le code suivant :

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

L’attribut `<TestClass>` désigne une classe qui contient des tests. L’attribut `<TestMethod>` désigne une méthode qui est exécutée par le Test Runner. À partir de *unit-testing-vb-mstest*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests. Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests. `dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.

Votre test échoue. Vous n’avez pas encore créé l’implémentation. Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

Dans le répertoire *unit-testing-vb-mstest*, réexécutez `dotnet test`. La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`. Après la création des deux projets, il exécute ce test unique. Le test réussit.

## <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code. Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `<TestMethod>`, mais cela devient vite fastidieux. D’autres attributs MSTest vous permettent d’écrire une suite de tests similaires.  L’attribut `<DataTestMethod>` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents. Vous pouvez utiliser l’attribut `<DataRow>` pour spécifier des valeurs pour ces entrées.

Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer une théorie unique. La théorie est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Exécutez `dotnet test`, et deux de ces tests échouent. Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :

```vb
if candidate < 2
```

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).

Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque. Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal. Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.
