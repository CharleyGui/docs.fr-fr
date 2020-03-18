---
title: Commande dotnet remove reference
description: La commande dotnet remove reference est une option pratique pour supprimer des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503625"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet remove reference` - Supprime des références entre projets.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet remove reference` est une option pratique pour supprimer des références de projet d’un projet.

## <a name="arguments"></a>Arguments

`PROJECT`

Fichier projet cible. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

`PROJECT_REFERENCES`

Références entre projets (P2P) à supprimer. Vous pouvez spécifier un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-f|--framework <FRAMEWORK>`**

  Ne supprime une référence que quand [framework](../../standard/frameworks.md) spécifique est ciblé.

## <a name="examples"></a>Exemples

- Supprimer une référence de projet du projet spécifié :

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Supprimer plusieurs références de projet du projet dans le répertoire actuel :

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Supprimer plusieurs références de projet à l’aide du modèle Glob sous Unix/Linux :

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
