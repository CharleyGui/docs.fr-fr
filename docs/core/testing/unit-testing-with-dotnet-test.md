---
title: Effectuer des tests unitaires du code C# dans .NET Core à l’aide de dotnet test et de xUnit
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240894"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Effectuer des tests unitaires de C# dans .NET Core à l’aide de dotnet test et de xUnit

Ce tutoriel montre comment construire une solution contenant un projet de test unitaire et un projet de code source. Pour suivre le tutoriel à l’aide d’une solution pré-construite, [consultez ou téléchargez le code de l’échantillon](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Créez la solution

Dans cette section, une solution est créée qui contient la source et les projets de test. La solution complétée a la structure d’annuaire suivante :

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

Les instructions suivantes fournissent les étapes pour créer la solution de test. Consultez [les commandes pour créer une solution de test](#create-test-cmd) pour les instructions visant à créer la solution de test en une seule étape.

* Ouvrez une fenêtre d’interpréteur de commandes.
* Exécutez la commande suivante :

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  La [`dotnet new sln`](../tools/dotnet-new.md) commande crée une nouvelle solution dans *l’annuaire de test-test-utilisation-dotnet-test.*
* Changez de répertoire pour le dossier *d’essai-dotnet-test de l’unité.*
* Exécutez la commande suivante :

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   La [`dotnet new classlib`](../tools/dotnet-new.md) commande crée un nouveau projet de bibliothèque de classe dans le dossier *PrimeService.* La nouvelle bibliothèque de classe contiendra le code à tester.
* Renommez *Class1.cs* en *PrimeService.cs*.
* Remplacer le code en *PrimeService.cs* par le code suivant :
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* Le code précédent :
  * Lance un <xref:System.NotImplementedException> avec un message indiquant qu’il n’est pas implémenté.
  * Est mis à jour plus tard dans le tutoriel.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* Dans le répertoire de *test-test-dotnet-test de l’unité,* exécutez la commande suivante pour ajouter le projet de bibliothèque de classe à la solution :

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Créez le projet *PrimeService.Tests* en exécutant la commande suivante :

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* La commande précédente :
  * Crée le projet *PrimeService.Tests* dans le répertoire *PrimeService.Tests.* Le projet d’essai utilise [xUnit](https://xunit.github.io/) comme bibliothèque d’essai.
  * Configure le coureur de test `<PackageReference />`en ajoutant les éléments suivants au fichier du projet :
    * "Microsoft.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.visualstudio"

* Ajoutez le projet de test au fichier de solution en exécutant la commande suivante :

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Ajoutez `PrimeService` la bibliothèque de classe comme dépendance au projet *PrimeService.Tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Commandes pour créer la solution

Cette section résume toutes les commandes de la section précédente. Passez cette section si vous avez terminé les étapes de la section précédente.

Les commandes suivantes créent la solution de test sur une machine windows. Pour macOS et Unix, mettez à jour la `ren` commande à la version OS de `ren` renommer un fichier:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Suivez les instructions pour "Remplacer le code en *PrimeService.cs* avec le code suivant" dans la section précédente.

## <a name="create-a-test"></a>Créer un test

Une approche populaire dans le développement piloté par les tests (TDD) est d’écrire un test avant de mettre en œuvre le code cible. Ce tutoriel utilise l’approche TDD. La `IsPrime` méthode est callable, mais non implémentée. Un appel `IsPrime` de test à échoue. Avec le TDD, un test est écrit qui est connu pour échouer. Le code cible est mis à jour pour faire passer le test. Vous continuez à répéter cette approche, à écrire un test défaillant, puis à mettre à jour le code cible pour passer.

Mettre à jour le projet *PrimeService.Tests* :

* Supprimer *PrimeService.Tests/UnitTest1.cs*.
* Créez un fichier *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*
* Remplacez le code dans *PrimeService_IsPrimeShould.cs* par le code suivant :

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

L’attribut `[Fact]` déclare une méthode de test qui est exécutée par le coureur d’essai. Du dossier *PrimeService.Tests,* `dotnet test`exécutez . La commande [de test dotnet](../tools/dotnet-test.md) construit à la fois des projets et exécute les tests. Le coureur d’essai xUnit contient le point d’entrée du programme pour exécuter les tests. `dotnet test`commence le coureur d’essai à l’aide du projet d’essai unitaire.

Le test `IsPrime` échoue parce que n’a pas été mis en œuvre. En utilisant l’approche TDD, écrivez seulement assez de code pour que ce test passe. Mise `IsPrime` à jour avec le code suivant:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Exécutez `dotnet test`. Le test réussit.

### <a name="add-more-tests"></a>Ajouter plus de tests

Ajoutez des tests de numéros de premier choix pour 0 et -1. Vous pouvez copier le test précédent et modifier le code suivant pour utiliser 0 et -1 :

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Copier le code de test lorsqu’un seul paramètre change entraîne une duplication du code et un ballonnement de test. Les attributs xUnit suivants permettent d’écrire une suite de tests similaires :

- `[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.

- L’attribut `[InlineData]` spécifie des valeurs pour ces entrées.

Plutôt que de créer de nouveaux tests, appliquez les attributs xUnit précédents pour créer une seule théorie. Remplacez le code suivant :

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

par le code suivant :

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Dans le code `[Theory]` `[InlineData]` précédent, et activer le test de plusieurs valeurs de moins de deux. Deux est le plus petit nombre premier.

Exécuter `dotnet test`, deux des tests échouent. Pour que tous les tests passent, mettez à jour la `IsPrime` méthode avec le code suivant :

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Suivant l’approche TDD, ajoutez d’autres tests défaillants, puis mettez à jour le code cible. Voir la [version finie des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et la mise en [œuvre complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

La `IsPrime` méthode terminée n’est pas un algorithme efficace pour tester la primalité.

### <a name="additional-resources"></a>Ressources supplémentaires

- [Site officiel xUnit.net](https://xunit.github.io)
- [Test de la logique de contrôleur dans ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
