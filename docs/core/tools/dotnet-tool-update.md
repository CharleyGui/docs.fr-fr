---
title: Commande dotnet tool update
description: La commande de mise à jour d’outil pointnet met à jour l’outil net Core spécifié sur votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463298"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool update`- Mise à jour de [l’outil net Core](global-tools.md) spécifié sur votre machine.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a>Description

La `dotnet tool update` commande vous permet de mettre à jour les outils .NET Core de votre machine à la dernière version stable du paquet. La commande désinstalle et réinstalle un outil en le mettant à jour. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour mettre à jour un outil global qui `--global` a été installé dans l’emplacement par défaut, utilisez l’option
* Pour mettre à jour un outil global qui `--tool-path` a été installé dans un emplacement personnalisé, utilisez l’option.
* Pour mettre à jour un `--global` `--tool-path` outil local, omettre les options et les options.

**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du paquet NuGet qui contient l’outil mondial .NET Core à mettre à jour. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`--add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`--framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md) pour lequel mettre à jour l’outil.

- **`-g|--global`**

  Spécifie que la mise à jour concerne un outil à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission `--global` à `--tool-path` la fois et précise que l’outil à mettre à jour est un outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Précise l’emplacement où l’outil global est installé. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission `--global` à `--tool-path` la fois et précise que l’outil à mettre à jour est un outil local.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

- **`dotnet tool update -g dotnetsay`**

  Mise à jour de l’outil mondial [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Mise à jour de [l’outil global dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Windows spécifique.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Mise à jour de [l’outil mondial dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Linux/macOS spécifique.

- **`dotnet tool update dotnetsay`**

  Mise à jour de [l’outil local dotnetsay](https://www.nuget.org/packages/dotnetsay/) installé pour l’annuaire actuel.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core](global-tools-how-to-use.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
