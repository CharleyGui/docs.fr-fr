---
title: commande dotnet de la liste de listes NuGet NuGet
description: La commande dotnet NuGet List source répertorie toutes les sources existantes de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537891"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures

## <a name="name"></a>Name

`dotnet nuget list source` -Répertorie toutes les sources NuGet configurées.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget list source` commande répertorie toutes les sources existantes de vos fichiers de configuration NuGet.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet. Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée. Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).

- **`--format [Detailed|Short]`**

  Format de la sortie de la commande list : `Detailed` (valeur par défaut) et `Short` .

## <a name="examples"></a>Exemples

- Répertorier les sources configurées à partir du répertoire actif :

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Voir aussi

- [Sections sources du package dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, commande (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
