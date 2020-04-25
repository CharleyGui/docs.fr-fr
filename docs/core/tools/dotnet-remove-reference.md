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
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet remove reference`-Supprime les références entre projets (P2P).

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
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

  Supprime la référence uniquement lorsque vous ciblez un [Framework](../../standard/frameworks.md) spécifique à l’aide du format TFM.

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
