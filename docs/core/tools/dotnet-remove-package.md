---
title: Commande dotnet remove package
description: La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503634"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet remove package` : Supprime une référence de package d’un fichier projet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
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

- Supprimer `Newtonsoft.Json` le paquet NuGet d’un projet dans l’annuaire actuel :

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
