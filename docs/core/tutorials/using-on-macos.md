---
title: 'Tutorial: Créer une solution .NET Core dans macOS en utilisant Visual Studio Code'
description: Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de Visual Studio Code.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156593"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Tutorial: Créer une solution .NET Core dans macOS en utilisant Visual Studio Code

Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core pour macOS. Découvrez comment créer des projets et des tests unitaires, utiliser les outils de débogage et incorporer des bibliothèques tierces à l’aide de [NuGet](https://www.nuget.org/).

> [!NOTE]
> Cet article utilise [Visual Studio Code](https://code.visualstudio.com) sur macOS.

## <a name="prerequisites"></a>Conditions préalables requises

Installer le [.NET Core SDK](https://dotnet.microsoft.com/download). Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.

Installer [Visual Studio Code](https://code.visualstudio.com). Au cours de cet article, vous allez également installer des extensions Visual Studio Code pour améliorer l’expérience de développement de .NET Core.

Installez l’extension Visual Studio Code CMD en ouvrant Visual Studio Code et en appuyant sur <kbd>Fn</kbd>+<kbd>F1</kbd> pour ouvrir la palette de code Visual Studio. Tapez **ext install** pour afficher la liste des extensions. Sélectionnez l’extension C#. Redémarrez Visual Studio Code pour activer l’extension. Pour plus d’informations, consultez la [documentation sur l’extension C# pour Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Bien démarrer

Dans ce didacticiel, vous créez trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque. Vous pouvez [afficher ou télécharger la source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) de cet article sur le référentiel dotnet/échantillons sur GitHub. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Démarrez Visual Studio Code. Appuyez sur <kbd>Ctrl</kbd> <kbd>\`</kbd> (le personnage backquote ou backtick) ou sélectionnez **View** > **Terminal** dans le menu pour ouvrir un terminal intégré dans Visual Studio Code. Vous pouvez toujours ouvrir une coque externe avec la commande Explorer **Open in Command Prompt** **(Ouvrez en terminal** sur macOS ou Linux) si vous préférez travailler en dehors du code Visual Studio.

Commencez par créer un fichier de solution qui servira de conteneur pour un ou plusieurs projets .NET Core. Dans le terminal, [`dotnet new`](../tools/dotnet-new.md) exécuter la commande pour créer une nouvelle solution *golden.sln* à l’intérieur d’un nouveau dossier nommé *d’or:*

```dotnetcli
dotnet new sln -o golden
```

Naviguez vers le nouveau dossier *d’or* et exécutez la commande suivante pour créer un projet de bibliothèque, qui produit deux fichiers,*library.csproj* et *Class1.cs*, dans le dossier de la *bibliothèque:*

```dotnetcli
dotnet new classlib -o library
```

Exécutez [`dotnet sln`](../tools/dotnet-sln.md) la commande pour ajouter le nouveau projet *library.csproj* à la solution :

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

Les méthodes de la bibliothèque sérialisent et désérialisent les objets au format JSON. Pour prendre en charge la sérialisation et la désérialisation JSON, ajoutez une référence au package NuGet `Newtonsoft.Json`. La commande `dotnet add` ajoute de nouveaux éléments à un projet. Pour ajouter une référence à un [`dotnet add package`](../tools/dotnet-add-package.md) package NuGet, utilisez la commande et spécifiez le nom du paquet :

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Cette opération ajoute `Newtonsoft.Json` et ses dépendances au projet de bibliothèque. Vous pouvez aussi modifier manuellement le fichier *library.csproj* et ajouter le nœud suivant :

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Exécuter [`dotnet restore`](../tools/dotnet-restore.md), ([voir note](#dotnet-restore-note)) qui restaure les dépendances et crée un dossier *obj* à l’intérieur *de la bibliothèque* avec trois fichiers en elle, y compris un fichier *project.assets.json:*

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

La classe `Thing` contient une méthode publique, `Get`, qui retourne la somme de deux nombres. Pour cela, elle convertit la somme en chaîne, puis la désérialise en entier. Cela fait usage d’un certain nombre de fonctionnalités modernes de C, telles que [ `using static` les directives,](../../csharp/language-reference/keywords/using-static.md) [les membres d’expression-corps,](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)et [l’interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md).

Construisez la [`dotnet build`](../tools/dotnet-build.md) bibliothèque avec la commande. Un fichier *library.dll* est généré sous *golden/library/bin/Debug/netstandard1.4* :

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

Ajoutez une référence de projet à la bibliothèque créée à la section précédente pour que le compilateur puisse trouver et utiliser le projet de bibliothèque. Utilisez [`dotnet add reference`](../tools/dotnet-add-reference.md) la commande :

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

Définissez un point d’arrêt au niveau de l’instruction `WriteLine` dans la méthode `Main`. Faites-le en appuyant soit sur la clé <kbd>Fn</kbd>+ `WriteLine` <kbd>F9</kbd> lorsque le curseur est au-dessus de la ligne ou en cliquant sur la souris dans la marge gauche sur la ligne où vous voulez définir le point d’arrêt. Un cercle rouge apparaît dans la marge à côté de la ligne de code. Quand le point d’arrêt est atteint, l’exécution du code s’arrête *avant* l’exécution de la ligne de point d’arrêt.

Ouvrez l’onglet débbugger en sélectionnant l’icône Debug dans la barre d’outils Visual Studio Code, en sélectionnant **View** > **Debug** à partir de la barre de menu, ou en utilisant le raccourci clavier <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>:

![Débogueur Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Appuyez sur le bouton de lecture pour démarrer l’application sous le débogueur. Vous avez créé à la fois un projet de test et une application dans ce projet. Le débbuggeur demande quel projet vous voulez démarrer. Sélectionnez le projet «app». L’application s’exécute jusqu’au point d’arrêt. Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés. Vérifiez que la réponse est 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
