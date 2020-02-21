---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543454"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool list`-répertorie tous les [outils .net Core](global-tools.md) du type spécifié actuellement installé sur votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool list` vous permet de répertorier tous les outils globaux .NET Core, les outils de chemin d’accès d’outils ou les outils locaux installés sur votre ordinateur. La commande répertorie le nom du package, la version installée et la commande d’outil.  Pour utiliser la commande, vous spécifiez l’un des éléments suivants :

* Outil Global installé à l’emplacement par défaut. Utiliser l’option `--global`
* Outil Global installé dans un emplacement personnalisé. Utilisez l'option `--tool-path`.
* Outil local. Omettez les options `--global` et `--tool-path`.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="options"></a>Options

- **`-g|--global`**

  Répertorie les outils globaux à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission des `--global` et des `--tool-path` répertorie les outils locaux. 

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie un emplacement personnalisé où trouver les outils globaux. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission des `--global` et des `--tool-path` répertorie les outils locaux. 

## <a name="examples"></a>Exemples

- **`dotnet tool list -g`**

  Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre ordinateur (profil utilisateur actuel).

- **`dotnet tool list --tool-path c:\global-tools`**

  Répertorie les outils globaux d’un répertoire Windows spécifique.

- **`dotnet tool list --tool-path ~/bin`**

  Répertorie les outils globaux d’un répertoire Linux/macOS spécifique.

- **`dotnet tool list`**

  Répertorie tous les outils locaux disponibles dans le répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
