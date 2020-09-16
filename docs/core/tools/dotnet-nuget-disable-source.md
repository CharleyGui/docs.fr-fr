---
title: commande dotnet NuGet Disable source
description: La commande dotnet NuGet Disable source désactive une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: af37a6589cebaf0501ee5647ebadb83125d0f56e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537949"
---
# <a name="dotnet-nuget-disable-source"></a>dotnet nuget disable source

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures

## <a name="name"></a>Name

`dotnet nuget disable source` -Désactivez une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget disable source` commande désactive une source existante dans vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet. Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée. Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemples

- Désactivez une source portant le nom `mySource` :

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a>Voir aussi

- [Sections sources du package dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, commande (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
