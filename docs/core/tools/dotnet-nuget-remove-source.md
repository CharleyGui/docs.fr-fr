---
title: dotnet nuget supprimer la commande source
description: La commande source de sous-vêtements dotnet supprime une source existante de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148539"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget supprimer la source

**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget remove source`- Supprimer une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a>Description

La `dotnet nuget remove source` commande supprime une source existante de vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile`**

  Le fichier de configuration NuGet. Si spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée. Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemples

- Supprimer une source `mySource`avec le nom de :

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Voir aussi

- [Sections source de paquet dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [commande de sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
