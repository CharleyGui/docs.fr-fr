---
title: Commande dotnet remove reference
description: La commande dotnet remove reference est une option pratique pour supprimer des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503625"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="b0994-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="b0994-103">dotnet remove reference</span></span>

<span data-ttu-id="b0994-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b0994-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b0994-105">Name</span><span class="sxs-lookup"><span data-stu-id="b0994-105">Name</span></span>

<span data-ttu-id="b0994-106">`dotnet remove reference` - Supprime des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="b0994-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0994-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b0994-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b0994-108">Description</span><span class="sxs-lookup"><span data-stu-id="b0994-108">Description</span></span>

<span data-ttu-id="b0994-109">La commande `dotnet remove reference` est une option pratique pour supprimer des références de projet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="b0994-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b0994-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0994-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b0994-111">Fichier projet cible.</span><span class="sxs-lookup"><span data-stu-id="b0994-111">Target project file.</span></span> <span data-ttu-id="b0994-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="b0994-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="b0994-113">Références entre projets (P2P) à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b0994-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="b0994-114">Vous pouvez spécifier un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="b0994-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="b0994-115">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="b0994-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="b0994-116">Options</span><span class="sxs-lookup"><span data-stu-id="b0994-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="b0994-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="b0994-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b0994-118">Ne supprime une référence que quand [framework](../../standard/frameworks.md) spécifique est ciblé.</span><span class="sxs-lookup"><span data-stu-id="b0994-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="b0994-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="b0994-119">Examples</span></span>

- <span data-ttu-id="b0994-120">Supprimer une référence de projet du projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="b0994-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="b0994-121">Supprimer plusieurs références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="b0994-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="b0994-122">Supprimer plusieurs références de projet à l’aide du modèle Glob sous Unix/Linux :</span><span class="sxs-lookup"><span data-stu-id="b0994-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
