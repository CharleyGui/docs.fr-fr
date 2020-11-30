---
title: Commande dotnet remove package
description: La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2020
ms.locfileid: "81463455"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet remove package` : Supprime une référence de package d’un fichier projet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a>Description

La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

`PACKAGE_NAME`

Référence de package à supprimer.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

- Supprimer `Newtonsoft.Json` le package NuGet d’un projet dans le répertoire actif :

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
