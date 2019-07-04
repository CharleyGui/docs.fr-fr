---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421828"
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

  ```console
  dotnet list app/app.csproj reference
  ```

* Lister les références de projet du projet dans le répertoire actuel :

  ```console
  dotnet list reference
  ```
