---
title: Commande dotnet tool list
description: La commande dotnet tool list répertorie l’outil global .NET Core spécifié à partir de votre machine.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117559"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool list` - Répertorie tous les [outils globaux .NET Core](global-tools.md) actuellement installés dans le répertoire par défaut de votre machine ou à l’emplacement du chemin spécifié.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool list` vous offre un moyen de lister tous les outils globaux .NET Core installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel) ou à l’emplacement du chemin spécifié. La commande liste le nom du package, la version installée et la commande de l’outil global. Pour utiliser cette commande, vous devez soit indiquer que vous voulez voir tous les outils à l’échelle de l’utilisateur à l’aide de l’option `--global`, soit spécifier un chemin personnalisé à l’aide de l’option `--tool-path`.

## <a name="options"></a>Options

`-g|--global`

Liste les outils globaux à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--tool-path`.

`-h|--help`

Affiche une aide brève pour la commande.

`--tool-path <PATH>`

Spécifie un emplacement personnalisé où trouver les outils globaux. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--global`.

## <a name="examples"></a>Exemples

Liste tous les outils globaux installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel) :

`dotnet tool list -g`

Liste les outils globaux à partir d’un dossier Windows spécifique :

`dotnet tool list --tool-path c:\global-tools`

Liste les outils globaux à partir d’un dossier Linux/macOS spécifique :

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Voir aussi

- [Outils globaux .NET Core](global-tools.md)
