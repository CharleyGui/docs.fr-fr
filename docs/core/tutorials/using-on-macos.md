---
title: 'Didacticiel : créer une solution .NET Core dans macOS à l’aide de Visual Studio Code'
description: Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de Visual Studio Code.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156593"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Didacticiel : créer une solution .NET Core dans macOS à l’aide de Visual Studio Code

Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core pour macOS. Découvrez comment créer des projets et des tests unitaires, utiliser les outils de débogage et incorporer des bibliothèques tierces à l’aide de [NuGet](https://www.nuget.org/).

> [!NOTE]
> Cet article utilise [Visual Studio Code](https://code.visualstudio.com) sur macOS.

## <a name="prerequisites"></a>Composants requis

Installez le [kit de développement logiciel (SDK) .NET Core](https://dotnet.microsoft.com/download). Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.

Installez [Visual Studio Code](https://code.visualstudio.com). Au cours de cet article, vous allez également installer des extensions Visual Studio Code pour améliorer l’expérience de développement de .NET Core.

Installez l’extension C# de Visual Studio code en ouvrant Visual Studio code et en appuyant sur <kbd>FN</kbd>+<kbd>F1</kbd> pour ouvrir la palette de Visual Studio code. Tapez **ext install** pour afficher la liste des extensions. Sélectionnez l’extension C#. Redémarrez Visual Studio Code pour activer l’extension. Pour plus d’informations, consultez la [documentation sur l’extension C# pour Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Prise en main

Dans ce didacticiel, vous créez trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque. Vous pouvez [afficher ou télécharger la source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) de cet article dans le référentiel dotnet/Samples sur GitHub. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Démarrez Visual Studio Code. Appuyez sur <kbd>Ctrl</kbd> <kbd>\`</kbd> (caractère de soulignement ou caractère de soulignement) ou sélectionnez **Afficher** > **Terminal** dans le menu pour ouvrir un terminal incorporé dans Visual Studio code. Vous pouvez toujours ouvrir un interpréteur de commandes externe à l’aide de la commande **ouvrir dans l’invite de commandes** de l’Explorateur (**ouvrir dans Terminal** sur MacOS ou Linux) si vous préférez travailler en dehors de Visual Studio code.

Commencez par créer un fichier de solution qui servira de conteneur pour un ou plusieurs projets .NET Core. Dans le terminal, exécutez la commande [`dotnet new`](../tools/dotnet-new.md) pour créer une solution *Golden. sln* à l’intérieur d’un nouveau dossier nommé *Golden*:

```dotnetcli
dotnet new sln -o golden
```

Accédez au nouveau dossier *Golden* et exécutez la commande suivante pour créer un projet de bibliothèque, qui génère deux fichiers,*Library. csproj* et *Class1.cs*, dans le dossier de *bibliothèque* :

```dotnetcli
dotnet new classlib -o library
```

Exécutez la commande [`dotnet sln`](../tools/dotnet-sln.md) pour ajouter le projet *library.csproj* que vous venez de créer à la solution :

```dotnetcli
dotnet sln add library/library.csproj
```

Le fichier *library.csproj* contient les informations suivantes :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Les méthodes de la bibliothèque sérialisent et désérialisent les objets au format JSON. Pour prendre en charge la sérialisation et la désérialisation JSON, ajoutez une référence au package NuGet `Newtonsoft.Json`. La commande `dotnet add` ajoute de nouveaux éléments à un projet. Pour ajouter une référence à un package NuGet, utilisez la commande [`dotnet add package`](../tools/dotnet-add-package.md) et spécifiez le nom du package :

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Cette opération ajoute `Newtonsoft.Json` et ses dépendances au projet de bibliothèque. Vous pouvez aussi modifier manuellement le fichier *library.csproj* et ajouter le nœud suivant :

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Exécutez [`dotnet restore`](../tools/dotnet-restore.md), ([voir la remarque](#dotnet-restore-note)) qui restaure les dépendances et crée un dossier *obj* dans *library* avec trois fichiers, notamment un fichier *project.assets.json* :

```dotnetcli
dotnet restore
```

Dans le dossier *library*, renommez le fichier *Class1.cs* en *Thing.cs*. Remplacez le code par ce qui suit :

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

La classe `Thing` contient une méthode publique, `Get`, qui retourne la somme de deux nombres. Pour cela, elle convertit la somme en chaîne, puis la désérialise en entier. Ce code utilise un certain nombre de fonctionnalités C# modernes, comme les [directives `using static`](../../csharp/language-reference/keywords/using-static.md), les [membres expression-bodied](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) et l’[interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md).

Générez la bibliothèque à l’aide de la commande [`dotnet build`](../tools/dotnet-build.md). Un fichier *library.dll* est généré sous *golden/library/bin/Debug/netstandard1.4* :

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Créer le projet de test

Créez un projet de test pour la bibliothèque. À partir du dossier *golden*, créez un projet de test :

```dotnetcli
dotnet new xunit -o test-library
```

Ajoutez le projet de test à la solution :

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Ajoutez une référence de projet à la bibliothèque créée à la section précédente pour que le compilateur puisse trouver et utiliser le projet de bibliothèque. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Vous pouvez aussi modifier manuellement le fichier *test-library.csproj* et ajouter le nœud suivant :

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Maintenant que les dépendances ont été correctement configurées, créez les tests pour votre bibliothèque. Ouvrez *UnitTest1.cs* et remplacez son contenu par le code suivant :

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Le fait de déclarer la valeur 42 n’est pas égal à 19+23 (ou 42) quand vous créez initialement le test unitaire (`Assert.NotEqual`), qui échoue. Lors de la création d’un test unitaire, une étape importante consiste à le faire échouer une fois pour confirmer sa logique.

À partir du dossier *golden*, exécutez les commandes suivantes :

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Ces commandes trouvent de manière récursive tous les projets pour restaurer les dépendances, les générer et activer le Test Runner xUnit pour exécuter les tests. Le test unique échoue comme prévu.

Modifiez le fichier *UnitTest1.cs* et remplacez l’assertion `Assert.NotEqual` par `Assert.Equal`. Exécutez la commande suivante à partir du dossier *golden* pour réexécuter le test, qui réussit cette fois-ci :

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Créer l’application console

L’application console que vous allez créer dans les étapes suivantes est dépendante du projet de bibliothèque créé précédemment et appelle sa méthode de bibliothèque durant l’exécution. Ce modèle de développement vous permet de voir comment créer des bibliothèques réutilisables pour plusieurs projets.

Créez une application console à partir du dossier *golden* :

```dotnetcli
dotnet new console -o app
```

Ajoutez le projet d’application console à la solution :

```dotnetcli
dotnet sln add app/app.csproj
```

Créez la dépendance à la bibliothèque en exécutant la commande `dotnet add reference` :

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Exécutez `dotnet restore` ([voir la remarque](#dotnet-restore-note)) pour restaurer les dépendances des trois projets dans la solution. Ouvrez *program.cs* et remplacez le contenu de la méthode `Main` par la ligne suivante :

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Ajoutez deux directives `using` en haut du fichier *Program.cs* :

```csharp
using static System.Console;
using Library;
```

Lancez la commande suivante `dotnet run` pour exécuter l’exécutable, où l’option `-p` après `dotnet run` spécifie le projet de l’application principale. L’application génère la chaîne « The answer is 42 ».

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Déboguer l’application

Définissez un point d’arrêt au niveau de l’instruction `WriteLine` dans la méthode `Main`. Pour ce faire, appuyez sur la touche <kbd>Fn</kbd>+<kbd>F9</kbd> lorsque le curseur se trouve sur la ligne de `WriteLine` ou en cliquant sur la souris dans la marge de gauche de la ligne où vous souhaitez définir le point d’arrêt. Un cercle rouge apparaît dans la marge à côté de la ligne de code. Quand le point d’arrêt est atteint, l’exécution du code s’arrête *avant* l’exécution de la ligne de point d’arrêt.

Ouvrez l’onglet débogueur en sélectionnant l’icône déboguer dans la barre d’outils Visual Studio code, en sélectionnant **Afficher** > **Déboguer** dans <kbd>&#8679;</kbd> <kbd>&#8984;</kbd>la barre de menus, ou en utilisant le raccourci clavier <kbd>D</kbd>:

![Débogueur Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Appuyez sur le bouton de lecture pour démarrer l’application sous le débogueur. Vous avez créé un projet de test et une application dans ce projet. Le débogueur demande le projet que vous souhaitez démarrer. Sélectionnez le projet « application ». L’application s’exécute jusqu’au point d’arrêt. Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés. Vérifiez que la réponse est 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
