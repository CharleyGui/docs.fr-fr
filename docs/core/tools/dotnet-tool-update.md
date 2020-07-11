---
title: Commande dotnet tool update
description: La commande de mise à jour de l’outil dotnet met à jour l’outil .NET Core spécifié sur votre ordinateur.
ms.date: 07/08/2020
ms.openlocfilehash: 7c4bde44ac9964828074baeb1a697ba64ed17887
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226619"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet tool update`-Met à jour l' [outil .net Core](global-tools.md) spécifié sur votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a>Description

La `dotnet tool update` commande vous permet de mettre à jour les outils .net Core sur votre ordinateur vers la dernière version stable du package. La commande désinstalle et réinstalle un outil en le mettant à jour. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour mettre à jour un outil global qui a été installé à l’emplacement par défaut, utilisez l' `--global` option
* Pour mettre à jour un outil global qui a été installé dans un emplacement personnalisé, utilisez l' `--tool-path` option.
* Pour mettre à jour un outil local, utilisez l' `--local` option.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_ID`**

  Nom/ID du package NuGet qui contient l’outil Global .NET Core à mettre à jour. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`--add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`--disable-parallel`**

  Empêcher la restauration en parallèle de plusieurs projets.

- **`--framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md) pour lequel mettre à jour l’outil.

- **`--ignore-failed-sources`**

  Considérer les défaillances de la source du package comme des avertissements.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).

- **`--local`**

  Mettez à jour l’outil et le manifeste de l’outil local. Non combinable avec l’option `--global`.

- **`--no-cache`**

  Ne pas mettre en cache les packages et les requêtes HTTP.

- **`--tool-manifest <PATH>`**

  Chemin d’accès au fichier manifeste.

- **`--tool-path <PATH>`**

  Spécifie l’emplacement d’installation de l’outil Global. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. En omettant les deux `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.

- **`--version <VERSION>`**

  Plage de versions du package d’outils à mettre à jour. Cela ne peut pas être utilisé pour rétrograder des versions, vous devez d’abord disposer d’une `uninstall` version plus récente.

- **`-g|--global`**

  Spécifie que la mise à jour concerne un outil à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. En omettant les deux `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

- **`dotnet tool update -g dotnetsay`**

  Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Windows spécifique.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Linux/MacOS spécifique.

- **`dotnet tool update dotnetsay`**

  Met à jour l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) installé pour le répertoire actif.

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) avec la dernière version du correctif, avec une version principale de `2` et une version mineure de `0` .

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) avec la version la plus basse dans la plage spécifiée `(> 2.0.0 && < 2.1.4)` , la version est `2.1.0` installée. Pour plus d’informations sur les plages de contrôle de version sémantique, consultez [plages de versions d’empaquetage NuGet](/nuget/concepts/package-versioning#version-ranges).

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
- [Gestion sémantique de version](https://semver.org)
- [Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core](global-tools-how-to-use.md)
- [Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core](local-tools-how-to-use.md)
