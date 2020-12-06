---
title: 'Prise en main de F # avec les outils en ligne de commande'
description: 'Découvrez comment créer une solution multiprojet simple sur F # à l’aide de l’CLI .NET Core sur n’importe quel système d’exploitation (Windows, macOS ou Linux).'
ms.date: 08/15/2020
ms.openlocfilehash: f890e31fe8c665874dc3034aebfae32e38b9031a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739913"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Prise en main de F # avec le CLI .NET Core

Cet article explique comment vous pouvez commencer à utiliser F # sur n’importe quel système d’exploitation (Windows, macOS ou Linux) avec le CLI .NET Core. Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes appelée par une application console.

## <a name="prerequisites"></a>Prérequis

Pour commencer, vous devez installer la dernière [Kit SDK .net Core](https://dotnet.microsoft.com/download).

Cet article suppose que vous savez comment utiliser une ligne de commande et que vous avez un éditeur de texte préféré. Si vous ne l’utilisez pas déjà, [Visual Studio code](get-started-vscode.md) est une option intéressante en tant qu’éditeur de texte pour F #.

## <a name="build-a-simple-multi-project-solution"></a>Créer une solution à plusieurs projets simple

Ouvrez une invite de commandes/terminal et utilisez la commande [dotnet New](../../core/tools/dotnet-new.md) pour créer un nouveau fichier solution appelé `FSNetCore` :

```dotnetcli
dotnet new sln -o FSNetCore
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Écrire une bibliothèque de classes

Remplacez les répertoires par *FSNetCore*.

Utilisez la `dotnet new` commande, créez un projet de bibliothèque de classes dans le dossier **src** nommé Library.

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Remplacez le contenu de `Library.fs` par le code suivant :

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    $"I used to be {value} but now I'm {json} thanks to JSON.NET!"
```

Ajoutez le Newtonsoft.Jssur le package NuGet au projet de bibliothèque.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ajoutez le `Library` projet à la `FSNetCore` solution à l’aide de la commande [dotnet sln Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Exécutez `dotnet build` pour générer le projet. Les dépendances non résolues seront restaurées lors de la génération.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Écrire une application console qui utilise la bibliothèque de classes

Utilisez la `dotnet new` commande, créez une application console dans le dossier **src** nommé App.

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Remplacez le contenu du fichier `Program.fs` par le code suivant :

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn $"{value}"

    0 // return an integer exit code
```

Ajoutez une référence au `Library` projet à l’aide de [dotnet ajouter une référence](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ajoutez le `App` projet à la `FSNetCore` solution à l’aide de la `dotnet sln add` commande :

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Restaurez les dépendances NuGet `dotnet restore` et exécutez `dotnet build` pour générer le projet.

Accédez au projet de `src/App` console, puis exécutez le projet `Hello World` en passant comme arguments :

```dotnetcli
cd src/App
dotnet run Hello World
```

Les résultats suivants doivent s’afficher :

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Étapes suivantes

Consultez ensuite la [visite guidée de f #](../tour.md) pour en savoir plus sur les différentes fonctionnalités de f #.
