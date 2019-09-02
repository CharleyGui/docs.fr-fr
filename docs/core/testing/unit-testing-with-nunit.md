---
title: Effectuer des tests unitaires de C# avec NUnit et .NET Core
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de NUnit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 22475fcbd9e971f4c544c020d9198fadee4548b1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168126"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Effectuer des tests unitaires de C# avec NUnit et .NET Core

Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires. Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) avant de commencer. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prérequis

- [Kit SDK .NET Core 2.1](https://www.microsoft.com/net/download) (ou version ultérieure).
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="creating-the-source-project"></a>Création du projet source

Ouvrez une fenêtre d’interpréteur de commandes. Créez un répertoire appelé *unit-testing-using-nunit* qui contiendra la solution. Dans ce nouveau répertoire, exécutez la commande suivante afin de créer un fichier solution pour la bibliothèque de classes et le projet de test :

```console
dotnet new sln
```
 
Ensuite, créez un répertoire *PrimeService*. La structure de répertoire et de fichiers est la suivante :

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Accédez au répertoire *PrimeService* et exécutez la commande suivante pour créer le projet source :

```console
dotnet new classlib
```

Renommez *Class1.cs* en *PrimeService.cs*. Créez une implémentation défaillante de la classe `PrimeService` :

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

Accédez de nouveau au répertoire *unit-testing-using-nunit*. Exécutez la commande suivante pour ajouter le projet de la bibliothèque de classes à la solution :

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Création du projet de test

Ensuite, créez le répertoire *PrimeService.Tests*. La structure du répertoire est illustrée ci-dessous :

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de la commande suivante :

```console
dotnet new nunit
```

La commande [dotnet new](../tools/dotnet-new.md) crée un projet de test qui utilise NUnit comme bibliothèque de test. Le modèle généré configure Test Runner dans le fichier *PrimeService.Tests.csproj* :

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires. `dotnet new` dans l’étape précédente a ajouté le kit SDK de test Microsoft, le framework de test NUnit et l’adaptateur de test NUnit. Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.

La solution finale se présente comme suit :

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

Exécutez la commande suivante dans le répertoire *unit-testing-using-nunit* :

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Création du premier test

Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus. Dans le répertoire *PrimeService.Tests*, renommez le fichier *UnitTest1.cs* en *PrimeService_IsPrimeShould.cs*, puis remplacez tout son contenu par le code suivant :

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        [Test]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            PrimeService primeService = CreatePrimeService();
            var result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
        
        /*
        More tests
        */
        
        private PrimeService CreatePrimeService()
        {
             return new PrimeService();
        }
    }
}
```

L’attribut `[TestFixture]` désigne une classe qui contient des tests unitaires. L’attribut `[Test]` indique une méthode qui est une méthode de test.

Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests. Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests. `dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.

Votre test échoue. Vous n’avez pas encore créé l’implémentation. Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :

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

Dans le répertoire *unit-testing-using-nunit*, réexécutez `dotnet test`. La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`. Après la création des deux projets, il exécute ce test unique. Le test réussit.

## <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code. Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez ajouter de nouveaux tests avec l’attribut `[Test]`, mais cela devient vite fastidieux. D’autres attributs NUnit vous permettent d’écrire une suite de tests similaires.  Un attribut `[TestCase]` permet de créer une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents. Vous pouvez utiliser l’attribut `[TestCase]` pour spécifier des valeurs pour ces entrées.

Au lieu de créer des tests, appliquez cet attribut pour créer un test unique piloté par les données. Le test piloté par les données est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Exécutez `dotnet test`, et deux de ces tests échouent. Pour que tous les tests réussissent, changez la clause `if` au début de la méthode `Main` dans le fichier *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque. Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal. Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.
