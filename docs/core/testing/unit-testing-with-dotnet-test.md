---
title: Effectuer des tests unitaires du code C# dans .NET Core à l’aide de dotnet test et de xUnit
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 1013e14690bb3cfc17e339bfd5045e6d10bc3d3e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168149"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Effectuer des tests unitaires de C# dans .NET Core à l’aide de dotnet test et de xUnit

Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires. Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) avant de commencer. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Création du projet source

Ouvrez une fenêtre d’interpréteur de commandes. Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution.
Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution. Le fait d’avoir une solution simplifie la gestion de la bibliothèque de classes et du projet de test unitaire.
Dans le répertoire de la solution, créez un répertoire *PrimeService*. La structure du répertoire et des fichiers jusqu’ici doit être la suivante :

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source. Renommez *Class1.cs* en *PrimeService.cs*. Créez d’abord une implémentation défaillante de la classe `PrimeService` :

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

Accédez de nouveau au répertoire *unit-testing-using-dotnet-test*.

Exécutez la commande [dotnet sln](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution :

```console
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Création du projet de test

Ensuite, créez le répertoire *PrimeService.Tests*. La structure du répertoire est illustrée ci-dessous :

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new xunit`](../tools/dotnet-new.md). Cette commande crée un projet de test qui utilise [xUnit](https://xunit.github.io/) comme bibliothèque de test. Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.csproj*. Le résultat est semblable au code suivant :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires. `dotnet new` a ajouté xUnit et le Test Runner xUnit à l’étape précédente. Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.

La solution finale se présente comme suit :

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Pour ajouter le projet de test à la solution, exécutez la commande [dotnet sln](../tools/dotnet-sln.md) dans le répertoire *unit-testing-using-dotnet-test* :

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Création du premier test

Vous allez écrire un test défaillant, le corriger pour qu’il réussisse, puis répéter le processus. Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs*. Ajoutez le code suivant :

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

L’attribut `[Fact]` désigne une méthode de test qui est exécutée par le Test Runner. À partir du dossier *PrimeService.Tests*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests. Le Test Runner xUnit contient le point d’entrée de programme qui permet d’exécuter vos tests. `dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.

Votre test échoue. Vous n’avez pas encore créé l’implémentation. Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne. Remplacez l’implémentation de la méthode `IsPrime` existante par le code suivant :

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

Dans le répertoire *PrimeService.Tests*, réexécutez `dotnet test`. La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`. Après la création des deux projets, il exécute ce test unique. Le test réussit.

## <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code. Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `[Fact]`, mais cela devient vite fastidieux. D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires :

- `[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.

- L’attribut `[InlineData]` spécifie des valeurs pour ces entrées.

Au lieu de créer des tests, appliquez ces deux attributs, `[Theory]` et `[InlineData]`, pour créer une théorie unique dans le fichier *PrimeService_IsPrimeShould.cs*. La théorie est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Réexécutez `dotnet test`. Deux de ces tests doivent échouer. Pour que tous les tests réussissent, changez la clause `if` au début de la méthode `IsPrime` dans le fichier *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous disposez de la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Ressources supplémentaires

- [Site officiel xUnit.net](https://xunit.github.io)
- [Test de la logique de contrôleur dans ASP.NET Core](/aspnet/core/mvc/controllers/testing)
