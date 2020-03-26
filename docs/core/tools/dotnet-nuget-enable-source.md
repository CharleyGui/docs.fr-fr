---
title: dotnet nuget activer la commande source
description: La commande de source d’activation de négète dotnet permet une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148560"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget activer la source

**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget enable source`- Activez une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a>Description

La `dotnet nuget enable source` commande permet une source existante dans vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile`**

  Le fichier de configuration NuGet. Si spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée. Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemples

- Activez une source `mySource`avec le nom de :

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Voir aussi

- [Sections source de paquet dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [commande de sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
