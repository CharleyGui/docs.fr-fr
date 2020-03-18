---
title: Commande dotnet tool install
description: La commande d’installation d’outils dotnet installe l’outil net Core spécifié sur votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146461"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool install`- Installe [l’outil net core](global-tools.md) spécifié sur votre machine.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a>Description

La `dotnet tool install` commande vous permet d’installer des outils .NET Core sur votre machine. Pour utiliser la commande, vous spécifiez l’une des options d’installation suivantes :

* Pour installer un outil global dans `--global` l’emplacement par défaut, utilisez l’option.
* Pour installer un outil global dans `--tool-path` un emplacement personnalisé, utilisez l’option.
* Pour installer un outil local, `--tool-path` omettre les options et les `--global` options.

**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**

Les outils globaux sont installés dans les répertoires `--global` suivants par défaut lorsque vous spécifiez l’option ou l’option `-g` :

| Système d''exploitation          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
|  Windows     | `%USERPROFILE%\.dotnet\tools` |

Les outils locaux sont ajoutés à un fichier *tool-manifest.json* dans un répertoire *.config* sous l’annuaire actuel. Si un fichier manifeste n’existe pas encore, créez-le en exécutant la commande suivante :

```dotnetcli
dotnet new tool-manifest
```

Pour plus d’informations, voir [Installer un outil local](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du paquet NuGet qui contient l’outil .NET Core à installer.

## <a name="options"></a>Options

- **`add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md) pour lequel installer l’outil. Par défaut, le SDK .NET Core essaie de choisir le framework cible le plus approprié.

- **`-g|--global`**

  Spécifie que l’installation est à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission `--global` à `--tool-path` la fois et spécifie une installation d’outils local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`tool-path <PATH>`**

  Spécifie l’emplacement d’installation de l’outil global. Le chemin peut être absolu ou relatif. Si le chemin n’existe pas, la commande essaie de le créer. L’omission `--global` à `--tool-path` la fois et spécifie une installation d’outils local.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Version de l’outil à installer. Par défaut, la dernière version stable du package est installée. Utilisez cette option pour installer la préversion ou des versions antérieures de l’outil.

## <a name="examples"></a>Exemples

- **`dotnet tool install -g dotnetsay`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil global dans l’emplacement par défaut.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil global dans un répertoire Windows spécifique.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil global dans un répertoire Linux/macOS spécifique.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Installe la version 2.0.0 de [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme outil global.

- **`dotnet tool install dotnetsay`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil local pour l’annuaire actuel.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core](global-tools-how-to-use.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
