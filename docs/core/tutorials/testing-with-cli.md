---
title: Organisation et test de projets avec l’interface de commande .NET
description: Ce didacticiel explique comment organiser et tester des projets .NET à partir de la ligne de commande.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 93e8a6b8afd9f9405bf21488998a61c2e761bf1e
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512253"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a>Organisation et test de projets avec l’interface de commande .NET

Ce didacticiel suit le [Didacticiel : créer une application console avec .net à l’aide de Visual Studio code](with-visual-studio-code.md), en allant au-delà de la création d’une application console simple pour développer des applications avancées et bien organisées. Après une présentation des dossiers disponibles pour organiser votre code, ce didacticiel vous montre comment étendre une application console avec le framework de tests [xUnit](https://xunit.github.io/).

## <a name="using-folders-to-organize-code"></a>Utilisation de dossiers pour organiser le code

Si vous souhaitez introduire de nouveaux types dans une application console, ajoutez des fichiers contenant les types à l’application. Par exemple, si vous ajoutez des fichiers contenant les types `AccountInformation` et `MonthlyReportRecords` à votre projet, la structure du fichier projet est plate et facile à parcourir :

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Toutefois, cela ne fonctionne bien que si la taille de votre projet est relativement petite. Imaginez ce qui se passerait si vous ajoutiez 20 types au projet : avec autant de fichiers alourdissant le répertoire racine du projet, la navigation et la maintenance seraient particulièrement difficiles.

Pour organiser le projet, créez un dossier et nommez-le *Models* pour stocker les fichiers de types. Placez les fichiers de types dans le dossier *Models* :

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Les projets qui regroupent logiquement les fichiers dans des dossiers simplifient la navigation et la gestion. Dans la section suivante, vous allez créer un exemple plus complexe avec des dossiers et des tests unitaires.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organisation et test du code à l’aide de l’exemple NewTypes Pets

### <a name="prerequisites"></a>Prérequis

* [.Net 5,0 SDK](https://dotnet.microsoft.com/download) ou une version ultérieure.

### <a name="building-the-sample"></a>Génération de l’exemple

Pour les étapes suivantes, vous pouvez soit suivre [l’exemple NewTypes Pets](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild), soit créer vos propres fichiers et dossiers. Les types et les tests sont logiquement organisés dans une structure de dossiers qui autorise l’ajout d’autres types et tests par la suite.

L’exemple contient deux types, `Dog` et `Cat`, qui implémentent une interface commune `IPet`. Pour le projet `NewTypes`, votre objectif est d’organiser les types liés aux animaux domestiques dans un dossier *Pets*. Si un autre jeu de types est ajouté par la suite, *WildAnimals* par exemple, il est placé dans le dossier *NewTypes* aux côtés du dossier *Pets*. Le dossier *WildAnimals* peut contenir des types pour des animaux non domestiques, par exemple `Squirrel` et `Rabbit`. De cette façon, à mesure que vous ajoutez des types, le projet reste bien organisé.

Créez la structure de dossiers suivante avec le contenu de fichier indiqué :

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs* :

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs* :

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs* :

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes.csproj* :

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Exécutez la commande suivante :

```dotnetcli
dotnet run
```

Observez la sortie suivante :

```console
Woof!
Meow!
```

Exercice facultatif : Vous pouvez ajouter un nouveau type d’animal domestique, par exemple `Bird`, en étendant ce projet. Faites en sorte que la méthode `TalkToOwner` du type Bird envoie un `Tweet!` au propriétaire. Réexécutez l’application. La sortie inclut `Tweet!`

### <a name="testing-the-sample"></a>Test de l’exemple

Le projet `NewTypes` est en place et vous l’avez organisé en conservant les types liés aux animaux domestiques dans un dossier. Créez à présent votre projet de test et commencez à écrire des tests à l’aide du framework de tests [xUnit](https://xunit.github.io/). Les tests unitaires vous permettent de vérifier automatiquement le comportement de vos types d’animaux domestiques et de vous assurer qu’ils fonctionnent correctement.

Accédez au dossier *src*, puis créez un dossier *test* et un sous-dossier *NewTypesTests*. À une invite de commandes à partir du dossier *NewTypesTests*, exécutez `dotnet new xunit`. Deux fichiers sont générés : *NewTypesTests.csproj* et *UnitTest1.cs*.

Le projet de test ne peut pas actuellement tester les types dans `NewTypes` et nécessite une référence de projet au projet `NewTypes`. Pour ajouter une référence de projet, utilisez la [`dotnet add reference`](../tools/dotnet-add-reference.md) commande :

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Vous pouvez également ajouter manuellement la référence de projet en ajoutant un nœud `<ItemGroup>` au fichier *NewTypesTests.csproj* :

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj* :

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

Le fichier *NewTypesTests.csproj* contient les éléments suivants :

* Référence de package à `Microsoft.NET.Test.Sdk` (infrastructure de tests .NET)
* Référence de package à `xunit` (framework de tests xUnit)
* Référence de package à `xunit.runner.visualstudio` (Test Runner)
* Référence de projet à `NewTypes` (code à tester)

Renommez *UnitTest1.cs* en *PetTests.cs* et remplacez le code dans le fichier par le suivant :

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

Exercice facultatif : Si vous avez précédemment ajouté un type `Bird` qui envoie un `Tweet!` au propriétaire, ajoutez une méthode de test au fichier *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, pour vérifier que la méthode `TalkToOwner` fonctionne correctement pour le type `Bird`.

> [!NOTE]
> Bien que l’on s’attende à ce que les valeurs `expected` et `actual` soient identiques, une assertion initiale avec les vérifications `Assert.NotEqual` spécifie que ces valeurs *ne sont pas égales*. Commencez toujours par créer un test en le faisant échouer pour vérifier sa logique. Après avoir vérifié que le test échoue, modifiez l’assertion pour que le test réussisse.

Le code suivant montre la structure complète du projet :

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Démarrez dans le répertoire *test/NewTypesTests*. Exécutez les tests avec la [`dotnet test`](../tools/dotnet-test.md) commande. Cette commande démarre le Test Runner spécifié dans le fichier projet.

Comme prévu, les tests échouent et la console affiche la sortie suivante :

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

Remplacez les assertions de vos tests `Assert.NotEqual` par `Assert.Equal` :

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Réexécutez les tests avec la commande `dotnet test` et observez la sortie suivante :

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

Les tests réussissent. Les méthodes des types d’animaux domestiques retournent des valeurs correctes quand elles communiquent avec le propriétaire.

Vous avez appris les techniques permettant d’organiser et de tester des projets à l’aide de xUnit. Vous pouvez maintenant les mettre en pratique dans vos propres projets. *Codez bien !*
