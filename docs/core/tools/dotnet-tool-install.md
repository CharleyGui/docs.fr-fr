---
title: Commande dotnet tool install
description: La commande d’installation de l’outil dotnet installe l’outil .NET spécifié sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 1dd870a8f91e557a2f59919682616aa8817fc070
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634322"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool install` -Installe l' [outil .net](global-tools.md) spécifié sur votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Description

La `dotnet tool install` commande vous permet d’installer les outils .net sur votre ordinateur. Pour utiliser la commande, vous spécifiez l’une des options d’installation suivantes :

* Pour installer un outil Global dans l’emplacement par défaut, utilisez l' `--global` option.
* Pour installer un outil Global dans un emplacement personnalisé, utilisez l' `--tool-path` option.
* Pour installer un outil local, omettez les `--global` `--tool-path` options et.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

Les outils globaux sont installés par défaut dans les répertoires suivants lorsque vous spécifiez l' `-g` `--global` option ou :

| Système d’exploitation          | Chemin d’accès                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Les outils locaux sont ajoutés à un *dotnet-tools.jssur* un fichier dans un répertoire *. config* sous le répertoire actif. Si un fichier manifeste n’existe pas encore, créez-le en exécutant la commande suivante :

```dotnetcli
dotnet new tool-manifest
```

Pour plus d’informations, consultez [installer un outil local](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du package NuGet qui contient l’outil .NET à installer.

## <a name="options"></a>Options

- **`add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`configfile <FILE>`**

  Fichier de configuration NuGet ( *nuget.config* ) à utiliser.

- **`framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md) pour lequel installer l’outil. Par défaut, le kit de développement logiciel (SDK) .NET tente de choisir le Framework cible le plus approprié.

- **`-g|--global`**

  Spécifie que l’installation est à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. En omettant les deux `--global` et `--tool-path` spécifie une installation de l’outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`tool-path <PATH>`**

  Spécifie l’emplacement d’installation de l’outil global. Le chemin peut être absolu ou relatif. Si le chemin n’existe pas, la commande essaie de le créer. En omettant les deux `--global` et `--tool-path` spécifie une installation de l’outil local.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Version de l’outil à installer. Par défaut, la dernière version stable du package est installée. Utilisez cette option pour installer la préversion ou des versions antérieures de l’outil.

## <a name="examples"></a>Exemples

- **`dotnet tool install -g dotnetsay`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans l’emplacement par défaut.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Windows spécifique.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Linux/MacOS spécifique.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Installe la version 2.0.0 de [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil Global.

- **`dotnet tool install dotnetsay`**

  Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil local pour le répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET](global-tools.md)
- [Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET](global-tools-how-to-use.md)
- [Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET](local-tools-how-to-use.md)
