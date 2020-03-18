---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847870"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool list`- Répertorie tous les [outils .NET Core](global-tools.md) du type spécifié actuellement installé sur votre machine.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a>Description

La `dotnet tool list` commande vous permet d’énumérer tous les outils globaux.NET Core, tool-path ou locaux installés sur votre machine. La commande répertorie le nom du paquet, la version installée et la commande de l’outil.  Pour utiliser la commande, vous spécifiez l’un des éléments suivants :

* Un outil global installé dans l’emplacement par défaut. Utiliser `--global` l’option
* Un outil global installé dans un emplacement personnalisé. Utilisez l'option `--tool-path`.
* Un outil local. Omettre `--global` `--tool-path` les options et les options.

**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**

## <a name="options"></a>Options

- **`-g|--global`**

  Répertorie les outils mondiaux à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission `--global` des `--tool-path` deux et la liste des outils locaux.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie un emplacement personnalisé où trouver des outils globaux. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission `--global` des `--tool-path` deux et la liste des outils locaux.

## <a name="examples"></a>Exemples

- **`dotnet tool list -g`**

  Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel).

- **`dotnet tool list --tool-path c:\global-tools`**

  Répertorie les outils globaux à partir d’un répertoire Windows spécifique.

- **`dotnet tool list --tool-path ~/bin`**

  Répertorie les outils globaux à partir d’un répertoire Linux/macOS spécifique.

- **`dotnet tool list`**

  Répertorie tous les outils locaux disponibles dans l’annuaire actuel.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core](global-tools-how-to-use.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
