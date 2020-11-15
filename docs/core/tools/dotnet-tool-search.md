---
title: commande de recherche d’outil dotnet
description: La commande de recherche de l’outil dotnet recherche les outils .NET qui sont publiés sur NuGet.org.
ms.date: 11/11/2020
ms.openlocfilehash: e0289e651ec4a439c791c8c948bef2d85d9c3794
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634140"
---
# <a name="dotnet-tool-search"></a><span data-ttu-id="57a95-103">recherche d’outils dotnet</span><span class="sxs-lookup"><span data-stu-id="57a95-103">dotnet tool search</span></span>

<span data-ttu-id="57a95-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="57a95-104">**This article applies to:** ✔️ .NET 5.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="57a95-105">Name</span><span class="sxs-lookup"><span data-stu-id="57a95-105">Name</span></span>

<span data-ttu-id="57a95-106">`dotnet tool search` -Recherche tous les [outils .net](global-tools.md) publiés dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="57a95-106">`dotnet tool search` - Searches all [.NET tools](global-tools.md) that are published to NuGet.</span></span>

## <a name="synopsis"></a><span data-ttu-id="57a95-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="57a95-107">Synopsis</span></span>

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a><span data-ttu-id="57a95-108">Description</span><span class="sxs-lookup"><span data-stu-id="57a95-108">Description</span></span>

<span data-ttu-id="57a95-109">La `dotnet tool search` commande vous permet de rechercher dans NuGet des outils qui peuvent être utilisés en tant qu’outils globaux .net, de chemin d’accès d’outils ou locaux.</span><span class="sxs-lookup"><span data-stu-id="57a95-109">The `dotnet tool search` command provides a way for you to search NuGet for tools that can be used as .NET global, tool-path, or local tools.</span></span> <span data-ttu-id="57a95-110">La commande recherche les noms d’outils et les métadonnées, tels que les titres, les descriptions et les balises.</span><span class="sxs-lookup"><span data-stu-id="57a95-110">The command searches the tool names and metadata such as titles, descriptions, and tags.</span></span>

<span data-ttu-id="57a95-111">La commande utilise l' [API de recherche NuGet](/nuget/api/search-query-service-resource#search-for-packages).</span><span class="sxs-lookup"><span data-stu-id="57a95-111">The command uses the [NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages).</span></span> <span data-ttu-id="57a95-112">Il filtre sur `packageType=dotnettool` pour sélectionner uniquement les packages d’outils .net.</span><span class="sxs-lookup"><span data-stu-id="57a95-112">It filters on `packageType=dotnettool` to select only .NET tool packages.</span></span>

## <a name="options"></a><span data-ttu-id="57a95-113">Options</span><span class="sxs-lookup"><span data-stu-id="57a95-113">Options</span></span>

- **`--detail`**

  <span data-ttu-id="57a95-114">Affiche les résultats détaillés de la requête.</span><span class="sxs-lookup"><span data-stu-id="57a95-114">Shows detailed results from the query.</span></span>

- **`--prerelease`**

  <span data-ttu-id="57a95-115">Comprend des packages de préversion.</span><span class="sxs-lookup"><span data-stu-id="57a95-115">Includes pre-release packages.</span></span>

- **`--skip <NUMBER>`**

  <span data-ttu-id="57a95-116">Spécifie le nombre de résultats de requête à ignorer.</span><span class="sxs-lookup"><span data-stu-id="57a95-116">Specifies the number of query results to skip.</span></span> <span data-ttu-id="57a95-117">Utilisé pour la pagination.</span><span class="sxs-lookup"><span data-stu-id="57a95-117">Used for pagination.</span></span>

- **`--take <NUMBER>`**

  <span data-ttu-id="57a95-118">Spécifie le nombre de résultats de requête à afficher.</span><span class="sxs-lookup"><span data-stu-id="57a95-118">Specifies the number of query results to show.</span></span> <span data-ttu-id="57a95-119">Utilisé pour la pagination.</span><span class="sxs-lookup"><span data-stu-id="57a95-119">Used for pagination.</span></span>

- **`-h|--help`**

  <span data-ttu-id="57a95-120">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="57a95-120">Shows command-line help.</span></span>

## <a name="examples"></a><span data-ttu-id="57a95-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="57a95-121">Examples</span></span>

- <span data-ttu-id="57a95-122">Recherchez dans NuGet.org les outils .NET dont le nom ou la description du package a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="57a95-122">Search NuGet.org for .NET tools that have "format" in their package name or description:</span></span>

  ```dotnetcli
  dotnet tool search format
  ```

  <span data-ttu-id="57a95-123">La sortie ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="57a95-123">The output looks like the following example:</span></span>

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- <span data-ttu-id="57a95-124">Recherchez dans NuGet.org les outils .NET dont le nom ou les métadonnées du package ont le même format, Affichez uniquement le premier résultat et affichez une vue détaillée.</span><span class="sxs-lookup"><span data-stu-id="57a95-124">Search NuGet.org for .NET tools that have "format" in their package name or metadata, show only the first result, and show a detailed view.</span></span>

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  <span data-ttu-id="57a95-125">La sortie ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="57a95-125">The output looks like the following example:</span></span>

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a><span data-ttu-id="57a95-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57a95-126">See also</span></span>

- [<span data-ttu-id="57a95-127">Outils .NET</span><span class="sxs-lookup"><span data-stu-id="57a95-127">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="57a95-128">Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="57a95-128">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="57a95-129">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="57a95-129">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
