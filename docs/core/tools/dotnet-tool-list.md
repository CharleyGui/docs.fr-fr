---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 7ca894ab0f5daf0118ff92fb39e0118b952b3d83
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768272"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet tool list`-Répertorie tous les [outils .net Core](global-tools.md) du type spécifié actuellement installé sur votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Description

La `dotnet tool list` commande vous permet de répertorier tous les outils globaux, de chemin d’accès d’outil ou d’outils locaux .net Core installés sur votre ordinateur. La commande répertorie le nom du package, la version installée et la commande d’outil.  Pour utiliser la commande, vous spécifiez l’un des éléments suivants :

* Pour répertorier les outils globaux installés à l’emplacement par défaut, utilisez l' `--global` option
* Pour répertorier les outils globaux installés dans un emplacement personnalisé, utilisez l' `--tool-path` option.
* Pour répertorier les outils locaux, un outil local. Utilisez l' `--local` option ou omettez les `--global` `--tool-path` options, et `--local` .

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="options"></a>Options

- **`-g|--global`**

  Répertorie les outils globaux à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission `--global` de et `--tool-path` répertorie les outils locaux.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--local`**

  Répertorie les outils locaux pour le répertoire actif. Ne peut pas être combiné avec les `--global` `--tool-path` options ou. L’omission `--global` de et `--tool-path` répertorie les outils locaux même si `--local` n’est pas spécifié.

- **`--tool-path <PATH>`**

  Spécifie un emplacement personnalisé où trouver les outils globaux. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission `--global` de et `--tool-path` répertorie les outils locaux.

## <a name="examples"></a>Exemples

- **`dotnet tool list -g`**

  Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre ordinateur (profil utilisateur actuel).

- **`dotnet tool list --tool-path c:\global-tools`**

  Répertorie les outils globaux d’un répertoire Windows spécifique.

- **`dotnet tool list --tool-path ~/bin`**

  Répertorie les outils globaux d’un répertoire Linux/macOS spécifique.

- **`dotnet tool list`** ni**`dotnet tool list --local`**

  Répertorie tous les outils locaux disponibles dans le répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
- [Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core](global-tools-how-to-use.md)
- [Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core](local-tools-how-to-use.md)
