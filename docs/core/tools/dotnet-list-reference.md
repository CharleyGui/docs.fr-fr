---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802765"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet list reference` : répertorie des références entre projets.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a>Description

La commande `dotnet list reference` est une option pratique pour répertorier des références de projet pour un projet donné.

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Fichier projet à traiter. Si aucun fichier n’est spécifié, la commande effectue une recherche dans le répertoire actif.

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
