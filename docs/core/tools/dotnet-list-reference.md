---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503715"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet list reference` : répertorie des références entre projets.

## <a name="synopsis"></a>Synopsis

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
