---
title: dotnet nuget liste source commande
description: La commande source de la liste de négget dotnet répertorie toutes les sources existantes de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148574"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget liste source

**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget list source`- Répertorie toutes les sources NuGet configurées.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a>Description

La `dotnet nuget list source` commande répertorie toutes les sources existantes de vos fichiers de configuration NuGet.

## <a name="options"></a>Options

- **`--configfile`**

  Le fichier de configuration NuGet. Si spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée. Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`--format`**

  Le format de la `Detailed` sortie de commande `Short`de liste : (la valeur par défaut) et .

## <a name="examples"></a>Exemples

- Liste des sources configurées de l’annuaire actuel :

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Voir aussi

- [Sections source de paquet dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [commande de sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
