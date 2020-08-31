---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 02/14/2020
ms.openlocfilehash: efe52f64a29c8825070bae9ee96b430b32176ffa
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053029"
---
# <a name="dotnet-sln"></a><span data-ttu-id="3887b-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3887b-103">dotnet sln</span></span>

<span data-ttu-id="3887b-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3887b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3887b-105">Nom</span><span class="sxs-lookup"><span data-stu-id="3887b-105">Name</span></span>

<span data-ttu-id="3887b-106">`dotnet sln` -Répertorie ou modifie les projets dans un fichier solution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3887b-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3887b-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3887b-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="3887b-108">Description</span><span class="sxs-lookup"><span data-stu-id="3887b-108">Description</span></span>

<span data-ttu-id="3887b-109">La `dotnet sln` commande offre un moyen pratique de répertorier et de modifier des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="3887b-110">Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="3887b-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="3887b-111">Si vous devez en créer un, utilisez la commande [dotnet New](dotnet-new.md) , comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3887b-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="3887b-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="3887b-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="3887b-113">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3887b-113">The solution file to use.</span></span> <span data-ttu-id="3887b-114">Si cet argument est omis, la commande recherche un dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3887b-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="3887b-115">S’il ne trouve aucun fichier solution ou plusieurs fichiers solution, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="3887b-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="3887b-116">Options</span><span class="sxs-lookup"><span data-stu-id="3887b-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3887b-117">Imprime une description de l’utilisation de la commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="3887b-118">Commandes</span><span class="sxs-lookup"><span data-stu-id="3887b-118">Commands</span></span>

### `list`

<span data-ttu-id="3887b-119">Liste tous les projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3887b-120">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3887b-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="3887b-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="3887b-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="3887b-122">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3887b-122">The solution file to use.</span></span> <span data-ttu-id="3887b-123">Si cet argument est omis, la commande recherche un dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3887b-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="3887b-124">S’il ne trouve aucun fichier solution ou plusieurs fichiers solution, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="3887b-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="3887b-125">Options</span><span class="sxs-lookup"><span data-stu-id="3887b-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3887b-126">Imprime une description de l’utilisation de la commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="3887b-127">Ajoute un ou plusieurs projets au fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3887b-128">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3887b-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="3887b-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="3887b-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="3887b-130">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3887b-130">The solution file to use.</span></span> <span data-ttu-id="3887b-131">Si elle n’est pas spécifiée, la commande recherche un répertoire actif et échoue s’il existe plusieurs fichiers solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="3887b-132">Chemin d’accès au projet ou aux projets à ajouter à la solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="3887b-133">Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la `dotnet sln` commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="3887b-134">Options</span><span class="sxs-lookup"><span data-stu-id="3887b-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3887b-135">Imprime une description de l’utilisation de la commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="3887b-136">Place les projets à la racine de la solution, plutôt que de créer un dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="3887b-137">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="3887b-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="3887b-138">Chemin d’accès du dossier de solution de destination auquel ajouter les projets.</span><span class="sxs-lookup"><span data-stu-id="3887b-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="3887b-139">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="3887b-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="3887b-140">Supprime un ou plusieurs projets du fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="3887b-141">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3887b-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="3887b-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="3887b-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="3887b-143">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3887b-143">The solution file to use.</span></span> <span data-ttu-id="3887b-144">Si n’est pas spécifié, la commande recherche un répertoire actif et échoue s’il existe plusieurs fichiers solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="3887b-145">Chemin d’accès au projet ou aux projets à ajouter à la solution.</span><span class="sxs-lookup"><span data-stu-id="3887b-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="3887b-146">Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la `dotnet sln` commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="3887b-147">Options</span><span class="sxs-lookup"><span data-stu-id="3887b-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3887b-148">Imprime une description de l’utilisation de la commande.</span><span class="sxs-lookup"><span data-stu-id="3887b-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="3887b-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="3887b-149">Examples</span></span>

- <span data-ttu-id="3887b-150">Répertorier les projets dans une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="3887b-151">Ajouter un projet C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="3887b-152">Supprimer un projet C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="3887b-153">Ajoutez plusieurs projets C# à la racine d’une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="3887b-154">Ajouter plusieurs projets C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="3887b-155">Supprimer plusieurs projets C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="3887b-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="3887b-156">Ajouter plusieurs projets C# à une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="3887b-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="3887b-157">Ajouter plusieurs projets C# à une solution à l’aide d’un modèle globbing (Windows PowerShell uniquement) :</span><span class="sxs-lookup"><span data-stu-id="3887b-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="3887b-158">Supprimer plusieurs projets C# d’une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="3887b-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="3887b-159">Supprimer plusieurs projets C# d’une solution à l’aide d’un modèle globbing (Windows PowerShell uniquement) :</span><span class="sxs-lookup"><span data-stu-id="3887b-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
