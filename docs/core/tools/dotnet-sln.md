---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733085"
---
# <a name="dotnet-sln"></a><span data-ttu-id="0f588-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0f588-103">dotnet sln</span></span>

<span data-ttu-id="0f588-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0f588-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="0f588-105">Name</span><span class="sxs-lookup"><span data-stu-id="0f588-105">Name</span></span>

<span data-ttu-id="0f588-106">`dotnet sln` : Modifie un fichier solution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f588-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f588-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="0f588-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0f588-108">Description</span><span class="sxs-lookup"><span data-stu-id="0f588-108">Description</span></span>

<span data-ttu-id="0f588-109">La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="0f588-110">Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="0f588-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="0f588-111">Si vous devez en créer un, utilisez la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0f588-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="0f588-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f588-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="0f588-113">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0f588-113">The solution file to use.</span></span> <span data-ttu-id="0f588-114">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="0f588-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0f588-115">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f588-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="0f588-116">Options</span><span class="sxs-lookup"><span data-stu-id="0f588-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f588-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0f588-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="0f588-118">Commands</span><span class="sxs-lookup"><span data-stu-id="0f588-118">Commands</span></span>

### `add`

<span data-ttu-id="0f588-119">Ajoute un ou plusieurs projets au fichier solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0f588-120">Résumé</span><span class="sxs-lookup"><span data-stu-id="0f588-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="0f588-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f588-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="0f588-122">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0f588-122">The solution file to use.</span></span> <span data-ttu-id="0f588-123">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="0f588-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0f588-124">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f588-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="0f588-125">Chemin d’accès au projet à ajouter à la solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="0f588-126">Ajoutez plusieurs projets en en ajoutant un après l’autre en les séparant par des espaces.</span><span class="sxs-lookup"><span data-stu-id="0f588-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="0f588-127">Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la commande `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="0f588-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="0f588-128">Options</span><span class="sxs-lookup"><span data-stu-id="0f588-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f588-129">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0f588-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="0f588-130">Place les projets à la racine de la solution, plutôt que de créer un dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="0f588-131">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0f588-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="0f588-132">Chemin d’accès du dossier de solution de destination auquel ajouter les projets.</span><span class="sxs-lookup"><span data-stu-id="0f588-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="0f588-133">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0f588-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="0f588-134">Supprime un ou plusieurs projets du fichier solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0f588-135">Résumé</span><span class="sxs-lookup"><span data-stu-id="0f588-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="0f588-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f588-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="0f588-137">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0f588-137">The solution file to use.</span></span> <span data-ttu-id="0f588-138">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="0f588-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0f588-139">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f588-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="0f588-140">Chemin d’accès au projet à supprimer de la solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="0f588-141">Pour supprimer plusieurs projets, ajoutez-en un après l’autre, en les séparant par des espaces.</span><span class="sxs-lookup"><span data-stu-id="0f588-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="0f588-142">Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la commande `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="0f588-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="0f588-143">Options</span><span class="sxs-lookup"><span data-stu-id="0f588-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f588-144">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0f588-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="0f588-145">Liste tous les projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="0f588-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="0f588-146">Résumé</span><span class="sxs-lookup"><span data-stu-id="0f588-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="0f588-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f588-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="0f588-148">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0f588-148">The solution file to use.</span></span> <span data-ttu-id="0f588-149">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="0f588-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0f588-150">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f588-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="0f588-151">Options</span><span class="sxs-lookup"><span data-stu-id="0f588-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f588-152">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0f588-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="0f588-153">Exemples</span><span class="sxs-lookup"><span data-stu-id="0f588-153">Examples</span></span>

- <span data-ttu-id="0f588-154">Ajouter un projet C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="0f588-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="0f588-155">Supprimer un projet C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="0f588-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="0f588-156">Ajouter plusieurs projets C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="0f588-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="0f588-157">Supprimer plusieurs projets C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="0f588-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="0f588-158">Ajouter plusieurs C# projets à une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="0f588-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="0f588-159">Supprimer plusieurs C# projets d’une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="0f588-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
