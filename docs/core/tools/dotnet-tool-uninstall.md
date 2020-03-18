---
title: Commande dotnet tool uninstall
description: L’outil dotnet désinstalle la commande désinstalle l’outil spécifié .NET Core de votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 82799404c40baa3a39f4e2a5fdb414fb745ef448
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847831"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool uninstall`- Désinstalle [l’outil spécifié .NET Core](global-tools.md) de votre machine.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>

dotnet tool uninstall <PACKAGE_NAME> <--tool-path>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Description

La `dotnet tool uninstall` commande vous permet de désinstaller les outils .NET Core de votre machine. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour désinstaller un outil global qui a été `--global` installé dans l’emplacement par défaut, utilisez l’option.
* Pour désinstaller un outil global qui a été `--tool-path` installé dans un emplacement personnalisé, utilisez l’option.
* Pour désinstaller un outil local, `--tool-path` omettre les options et les `--global` options.

**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du paquet NuGet qui contient l’outil .NET Core pour désinstaller. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`-g|--global`**

  Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission `--global` à `--tool-path` la fois et précise que l’outil à supprimer est un outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie l’emplacement où désinstaller l’outil. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission `--global` à `--tool-path` la fois et précise que l’outil à supprimer est un outil local.

## <a name="examples"></a>Exemples

- **`dotnet tool uninstall -g dotnetsay`**

  Désinstalle l’outil mondial [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Désinstalle l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Windows spécifique.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Désinstalle l’outil mondial [dotnetsay](https://www.nuget.org/packages/dotnetsay/) à partir d’un répertoire Linux/macOS spécifique.

- **`dotnet tool uninstall dotnetsay`**

  Désinstalle l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de l’annuaire actuel.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core](global-tools-how-to-use.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
