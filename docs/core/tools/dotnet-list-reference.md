---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117673"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet list reference` : répertorie des références entre projets.

## <a name="synopsis"></a>Résumé

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet list reference` est pratique pour lister les références à un projet ou à une solution donné.

## <a name="arguments"></a>Arguments

* **`PROJECT | SOLUTION`**

  Spécifie le fichier projet ou le fichier solution à utiliser pour lister les références. Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.

## <a name="options"></a>Options

* **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

* Lister les références de projet pour le projet spécifié :

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Lister les références de projet du projet dans le répertoire actuel :

  ```dotnetcli
  dotnet list reference
  ```
