---
title: Prise en main F# avec les outils en ligne de commande
description: Apprenez à créer une solution à plusieurs projets simple sur F# à l’aide de l’CLI .net Core sur n’importe quel système d’exploitation (Windows, MacOS ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 6f67314f49150e20b18734f21f24daa3ce856922
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504147"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="8397b-103">Prise en main F# de avec le CLI .net Core</span><span class="sxs-lookup"><span data-stu-id="8397b-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="8397b-104">Cet article explique comment vous pouvez commencer avec F# sur n’importe quel système d’exploitation (Windows, MacOS ou Linux) avec le CLI .net core.</span><span class="sxs-lookup"><span data-stu-id="8397b-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="8397b-105">Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes appelée par une application console.</span><span class="sxs-lookup"><span data-stu-id="8397b-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8397b-106">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="8397b-106">Prerequisites</span></span>

<span data-ttu-id="8397b-107">Pour commencer, vous devez installer la dernière [Kit SDK .net Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="8397b-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="8397b-108">Cet article suppose que vous savez comment utiliser une ligne de commande et que vous avez un éditeur de texte préféré.</span><span class="sxs-lookup"><span data-stu-id="8397b-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="8397b-109">Si vous ne l’utilisez pas déjà, [Visual Studio code](get-started-vscode.md) est une option intéressante en tant qu’éditeur F#de texte pour.</span><span class="sxs-lookup"><span data-stu-id="8397b-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="8397b-110">Créer une solution à plusieurs projets simple</span><span class="sxs-lookup"><span data-stu-id="8397b-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="8397b-111">Ouvrez une invite de commandes/terminal et utilisez la commande [dotnet New](../../core/tools/dotnet-new.md) pour créer un nouveau fichier solution appelé `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="8397b-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="8397b-112">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="8397b-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="8397b-113">Écrire une bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="8397b-113">Write a class library</span></span>

<span data-ttu-id="8397b-114">Remplacez les répertoires par *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="8397b-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="8397b-115">Utilisez la commande `dotnet new`, créez un projet de bibliothèque de classes dans le dossier **src** nommé Library.</span><span class="sxs-lookup"><span data-stu-id="8397b-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="8397b-116">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="8397b-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="8397b-117">Remplacez le contenu de `Library.fs` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8397b-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="8397b-118">Ajoutez le package NuGet Newtonsoft. JSON au projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8397b-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="8397b-119">Ajoutez le projet `Library` à la solution `FSNetCore` à l’aide de la commande [dotnet sln Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="8397b-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="8397b-120">Exécutez `dotnet build` pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="8397b-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="8397b-121">Les dépendances non résolues seront restaurées lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="8397b-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="8397b-122">Écrire une application console qui utilise la bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="8397b-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="8397b-123">Utilisez la commande `dotnet new`, créez une application console dans le dossier **src** nommé App.</span><span class="sxs-lookup"><span data-stu-id="8397b-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="8397b-124">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="8397b-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="8397b-125">Remplacez le contenu du fichier `Program.fs` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8397b-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

<span data-ttu-id="8397b-126">Ajoutez une référence au projet `Library` à l’aide de [dotnet ajouter une référence](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8397b-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="8397b-127">Ajoutez le projet `App` à la solution `FSNetCore` à l’aide de la commande `dotnet sln add` :</span><span class="sxs-lookup"><span data-stu-id="8397b-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="8397b-128">Restaurez les dépendances NuGet, `dotnet restore` et exécutez `dotnet build` pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="8397b-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="8397b-129">Remplacez le répertoire par le projet de console `src/App` et exécutez le projet en passant `Hello World` en tant qu’arguments :</span><span class="sxs-lookup"><span data-stu-id="8397b-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="8397b-130">Les résultats suivants doivent s’afficher :</span><span class="sxs-lookup"><span data-stu-id="8397b-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="8397b-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8397b-131">Next steps</span></span>

<span data-ttu-id="8397b-132">Consultez ensuite la [visite guidée de F# ](../tour.md) pour en savoir plus sur les F# différentes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8397b-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
