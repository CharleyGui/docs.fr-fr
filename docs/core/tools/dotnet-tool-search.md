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
# <a name="dotnet-tool-search"></a>recherche d’outils dotnet

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5,0 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool search` -Recherche tous les [outils .net](global-tools.md) publiés dans NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a>Description

La `dotnet tool search` commande vous permet de rechercher dans NuGet des outils qui peuvent être utilisés en tant qu’outils globaux .net, de chemin d’accès d’outils ou locaux. La commande recherche les noms d’outils et les métadonnées, tels que les titres, les descriptions et les balises.

La commande utilise l' [API de recherche NuGet](/nuget/api/search-query-service-resource#search-for-packages). Il filtre sur `packageType=dotnettool` pour sélectionner uniquement les packages d’outils .net.

## <a name="options"></a>Options

- **`--detail`**

  Affiche les résultats détaillés de la requête.

- **`--prerelease`**

  Comprend des packages de préversion.

- **`--skip <NUMBER>`**

  Spécifie le nombre de résultats de requête à ignorer. Utilisé pour la pagination.

- **`--take <NUMBER>`**

  Spécifie le nombre de résultats de requête à afficher. Utilisé pour la pagination.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="examples"></a>Exemples

- Recherchez dans NuGet.org les outils .NET dont le nom ou la description du package a le format suivant :

  ```dotnetcli
  dotnet tool search format
  ```

  La sortie ressemble à l’exemple suivant :

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- Recherchez dans NuGet.org les outils .NET dont le nom ou les métadonnées du package ont le même format, Affichez uniquement le premier résultat et affichez une vue détaillée.

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  La sortie ressemble à l’exemple suivant :

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

## <a name="see-also"></a>Voir aussi

- [Outils .NET](global-tools.md)
- [Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET](global-tools-how-to-use.md)
- [Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET](local-tools-how-to-use.md)
