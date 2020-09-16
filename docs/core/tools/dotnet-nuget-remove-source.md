---
title: commande dotnet NuGet Remove source
description: La commande dotnet NuGet Remove source supprime une source existante de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537887"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remove source

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures

## <a name="name"></a>Name

`dotnet nuget remove source` -Supprime une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget remove source` commande supprime une source existante de vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile`**

  Fichier de configuration NuGet. Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée. Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemples

- Supprimer une source portant le nom `mySource` :

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Voir aussi

- [Sections sources du package dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, commande (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
