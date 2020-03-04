---
title: Commande dotnet tool update
description: La commande de mise à jour de l’outil dotnet met à jour l’outil .NET Core spécifié sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156944"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet tool update` : met à jour l' [outil .net Core](global-tools.md) spécifié sur votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool update` vous permet de mettre à jour les outils .NET Core sur votre ordinateur vers la dernière version stable du package. La commande désinstalle et réinstalle un outil en le mettant à jour. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour mettre à jour un outil global qui a été installé à l’emplacement par défaut, utilisez l’option `--global`
* Pour mettre à jour un outil global qui a été installé dans un emplacement personnalisé, utilisez l’option `--tool-path`.
* Pour mettre à jour un outil local, omettez les options `--global` et `--tool-path`.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du package NuGet qui contient l’outil Global .NET Core à mettre à jour. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`--add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`--framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md) pour lequel mettre à jour l’outil.

- **`-g|--global`**

  Spécifie que la mise à jour concerne un outil à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission de `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie l’emplacement d’installation de l’outil Global. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission de `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.

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

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
