---
title: Prise en main F# avec les outils en ligne de commande
description: Apprenez à créer une solution à plusieurs projets simple sur F# à l’aide de l’CLI .net Core sur n’importe quel système d’exploitation (Windows, MacOS ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 1376b6b5384f380c06a96cdc568ad108de8a6e5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855823"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="a19d3-103">Prise en main F# de avec le CLI .net Core</span><span class="sxs-lookup"><span data-stu-id="a19d3-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="a19d3-104">Cet article explique comment vous pouvez commencer avec F# sur n’importe quel système d’exploitation (Windows, MacOS ou Linux) avec le CLI .net core.</span><span class="sxs-lookup"><span data-stu-id="a19d3-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="a19d3-105">Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes appelée par une application console.</span><span class="sxs-lookup"><span data-stu-id="a19d3-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a19d3-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a19d3-106">Prerequisites</span></span>

<span data-ttu-id="a19d3-107">Pour commencer, vous devez installer la dernière [Kit SDK .net Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="a19d3-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="a19d3-108">Cet article suppose que vous savez comment utiliser une ligne de commande et que vous avez un éditeur de texte préféré.</span><span class="sxs-lookup"><span data-stu-id="a19d3-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="a19d3-109">Si vous ne l’utilisez pas déjà, [Visual Studio code](get-started-vscode.md) est une option intéressante en tant qu’éditeur F#de texte pour.</span><span class="sxs-lookup"><span data-stu-id="a19d3-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="a19d3-110">Créer une solution à plusieurs projets simple</span><span class="sxs-lookup"><span data-stu-id="a19d3-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="a19d3-111">Ouvrez une invite de commandes/terminal et utilisez la commande [dotnet New](../../core/tools/dotnet-new.md) pour créer un nouveau fichier `FSNetCore`solution appelé :</span><span class="sxs-lookup"><span data-stu-id="a19d3-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="a19d3-112">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="a19d3-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="a19d3-113">Écrire une bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="a19d3-113">Write a class library</span></span>

<span data-ttu-id="a19d3-114">Remplacez les répertoires par *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="a19d3-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="a19d3-115">Utilisez la `dotnet new` commande, créez un projet de bibliothèque de classes dans le dossier **src** nommé Library.</span><span class="sxs-lookup"><span data-stu-id="a19d3-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="a19d3-116">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="a19d3-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="a19d3-117">Remplacez le contenu de `Library.fs` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a19d3-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="a19d3-118">Ajoutez le package NuGet Newtonsoft. JSON au projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a19d3-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="a19d3-119">Ajoutez le `Library` projet à la `FSNetCore` solution à l’aide de la commande [dotnet sln Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="a19d3-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="a19d3-120">Exécutez `dotnet build` pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="a19d3-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="a19d3-121">Les dépendances non résolues seront restaurées lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="a19d3-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="a19d3-122">Écrire une application console qui utilise la bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="a19d3-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="a19d3-123">Utilisez la `dotnet new` commande, créez une application console dans le dossier **src** nommé App.</span><span class="sxs-lookup"><span data-stu-id="a19d3-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="a19d3-124">La structure de répertoire suivante est générée après l’exécution de la commande précédente :</span><span class="sxs-lookup"><span data-stu-id="a19d3-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="a19d3-125">Remplacez le contenu du fichier `Program.fs` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a19d3-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="a19d3-126">Ajoutez une référence au `Library` projet à l’aide de [dotnet ajouter une référence](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a19d3-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="a19d3-127">Ajoutez le `App` projet à la `FSNetCore` solution à l' `dotnet sln add` aide de la commande :</span><span class="sxs-lookup"><span data-stu-id="a19d3-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="a19d3-128">Restaurez les dépendances `dotnet restore` NuGet et `dotnet build` exécutez pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="a19d3-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="a19d3-129">Accédez au projet de `src/App` console, puis exécutez le projet en `Hello World` passant comme arguments :</span><span class="sxs-lookup"><span data-stu-id="a19d3-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="a19d3-130">Les résultats suivants doivent s’afficher:</span><span class="sxs-lookup"><span data-stu-id="a19d3-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="a19d3-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a19d3-131">Next steps</span></span>

<span data-ttu-id="a19d3-132">Consultez ensuite la [visite guidée de F# ](../tour.md) pour en savoir plus sur les F# différentes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="a19d3-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
