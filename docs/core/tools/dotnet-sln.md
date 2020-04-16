---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463400"
---
# <a name="dotnet-sln"></a><span data-ttu-id="85418-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="85418-103">dotnet sln</span></span>

<span data-ttu-id="85418-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="85418-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="85418-105">Nom</span><span class="sxs-lookup"><span data-stu-id="85418-105">Name</span></span>

<span data-ttu-id="85418-106">`dotnet sln`- Listes ou modifications des projets dans un fichier de solution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85418-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85418-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="85418-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="85418-108">Description</span><span class="sxs-lookup"><span data-stu-id="85418-108">Description</span></span>

<span data-ttu-id="85418-109">La `dotnet sln` commande fournit un moyen pratique d’énumérer et de modifier des projets dans un fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="85418-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="85418-110">Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister.</span><span class="sxs-lookup"><span data-stu-id="85418-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="85418-111">Si vous avez besoin d’en créer un, utilisez la nouvelle commande [dotnet,](dotnet-new.md) comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="85418-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="85418-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="85418-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="85418-113">Le fichier de solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="85418-113">The solution file to use.</span></span> <span data-ttu-id="85418-114">Si cet argument est omis, la commande recherche l’annuaire actuel pour un.</span><span class="sxs-lookup"><span data-stu-id="85418-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="85418-115">S’il ne trouve aucun fichier de solution ou plusieurs fichiers de solution, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="85418-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="85418-116">Options</span><span class="sxs-lookup"><span data-stu-id="85418-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="85418-117">Imprime une description de la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="85418-118">Commandes</span><span class="sxs-lookup"><span data-stu-id="85418-118">Commands</span></span>

### `list`

<span data-ttu-id="85418-119">Liste tous les projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="85418-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85418-120">Synopsis</span><span class="sxs-lookup"><span data-stu-id="85418-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="85418-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="85418-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="85418-122">Le fichier de solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="85418-122">The solution file to use.</span></span> <span data-ttu-id="85418-123">Si cet argument est omis, la commande recherche l’annuaire actuel pour un.</span><span class="sxs-lookup"><span data-stu-id="85418-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="85418-124">S’il ne trouve aucun fichier de solution ou plusieurs fichiers de solution, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="85418-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="85418-125">Options</span><span class="sxs-lookup"><span data-stu-id="85418-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="85418-126">Imprime une description de la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="85418-127">Ajoute un ou plusieurs projets au fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="85418-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85418-128">Synopsis</span><span class="sxs-lookup"><span data-stu-id="85418-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="85418-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="85418-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="85418-130">Le fichier de solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="85418-130">The solution file to use.</span></span> <span data-ttu-id="85418-131">S’il n’est pas précisé, la commande recherche l’annuaire actuel pour un et échoue s’il ya plusieurs fichiers de solution.</span><span class="sxs-lookup"><span data-stu-id="85418-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="85418-132">Le chemin vers le projet ou les projets à ajouter à la solution.</span><span class="sxs-lookup"><span data-stu-id="85418-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="85418-133">Les extensions [de motifs de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) `dotnet sln` de coquilles Unix/Linux sont traitées correctement par la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="85418-134">Options</span><span class="sxs-lookup"><span data-stu-id="85418-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="85418-135">Imprime une description de la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="85418-136">Place les projets à la racine de la solution, plutôt que de créer un dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="85418-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="85418-137">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="85418-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="85418-138">Le chemin de dossier de solution de destination pour ajouter les projets à.</span><span class="sxs-lookup"><span data-stu-id="85418-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="85418-139">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="85418-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="85418-140">Supprime un ou plusieurs projets du fichier solution.</span><span class="sxs-lookup"><span data-stu-id="85418-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85418-141">Synopsis</span><span class="sxs-lookup"><span data-stu-id="85418-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="85418-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="85418-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="85418-143">Le fichier de solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="85418-143">The solution file to use.</span></span> <span data-ttu-id="85418-144">Si elle n’est pas précisée, la commande recherche l’annuaire actuel pour un et échoue s’il existe plusieurs fichiers de solutions.</span><span class="sxs-lookup"><span data-stu-id="85418-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="85418-145">Le chemin vers le projet ou les projets à ajouter à la solution.</span><span class="sxs-lookup"><span data-stu-id="85418-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="85418-146">Les extensions [de motifs de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) `dotnet sln` de coquilles Unix/Linux sont traitées correctement par la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="85418-147">Options</span><span class="sxs-lookup"><span data-stu-id="85418-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="85418-148">Imprime une description de la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="85418-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="85418-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="85418-149">Examples</span></span>

- <span data-ttu-id="85418-150">Énumérez les projets dans une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="85418-151">Ajouter un projet C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="85418-152">Supprimer un projet C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="85418-153">Ajoutez plusieurs projets C à la racine d’une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="85418-154">Ajouter plusieurs projets C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="85418-155">Supprimer plusieurs projets C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="85418-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="85418-156">Ajoutez plusieurs projets C à une solution à l’aide d’un modèle de glisse (Unix/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="85418-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="85418-157">Ajoutez plusieurs projets C à une solution à l’aide d’un modèle de glisse (Windows PowerShell uniquement) :</span><span class="sxs-lookup"><span data-stu-id="85418-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- <span data-ttu-id="85418-158">Supprimer plusieurs projets C d’une solution à l’aide d’un modèle de globbing (Unix/Linux uniquement) :</span><span class="sxs-lookup"><span data-stu-id="85418-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="85418-159">Supprimer plusieurs projets C d’une solution à l’aide d’un modèle de globbing (Windows PowerShell seulement):</span><span class="sxs-lookup"><span data-stu-id="85418-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
