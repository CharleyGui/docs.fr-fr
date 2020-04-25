---
title: Commande dotnet remove reference
description: La commande dotnet remove reference est une option pratique pour supprimer des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158331"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="14139-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="14139-103">dotnet remove reference</span></span>

<span data-ttu-id="14139-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="14139-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="14139-105">Nom</span><span class="sxs-lookup"><span data-stu-id="14139-105">Name</span></span>

<span data-ttu-id="14139-106">`dotnet remove reference`-Supprime les références entre projets (P2P).</span><span class="sxs-lookup"><span data-stu-id="14139-106">`dotnet remove reference` - Removes project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="14139-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="14139-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="14139-108">Description</span><span class="sxs-lookup"><span data-stu-id="14139-108">Description</span></span>

<span data-ttu-id="14139-109">La commande `dotnet remove reference` est une option pratique pour supprimer des références de projet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="14139-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="14139-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="14139-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="14139-111">Fichier projet cible.</span><span class="sxs-lookup"><span data-stu-id="14139-111">Target project file.</span></span> <span data-ttu-id="14139-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="14139-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="14139-113">Références entre projets (P2P) à supprimer.</span><span class="sxs-lookup"><span data-stu-id="14139-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="14139-114">Vous pouvez spécifier un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="14139-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="14139-115">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="14139-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="14139-116">Options</span><span class="sxs-lookup"><span data-stu-id="14139-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="14139-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="14139-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="14139-118">Supprime la référence uniquement lorsque vous ciblez un [Framework](../../standard/frameworks.md) spécifique à l’aide du format TFM.</span><span class="sxs-lookup"><span data-stu-id="14139-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

## <a name="examples"></a><span data-ttu-id="14139-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="14139-119">Examples</span></span>

- <span data-ttu-id="14139-120">Supprimer une référence de projet du projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="14139-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="14139-121">Supprimer plusieurs références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="14139-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="14139-122">Supprimer plusieurs références de projet à l’aide du modèle Glob sous Unix/Linux :</span><span class="sxs-lookup"><span data-stu-id="14139-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
