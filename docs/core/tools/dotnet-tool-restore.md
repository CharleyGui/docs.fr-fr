---
title: commande de restauration de l’outil dotnet
description: La commande de restauration de l’outil dotnet installe sur votre machine les outils locaux .NET Core qui sont dans l’étendue du répertoire actif.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543907"
---
# <a name="dotnet-tool-restore"></a>restauration de l’outil dotnet

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool restore`-installe sur votre machine les outils locaux .NET Core qui sont dans l’étendue du répertoire actif.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool restore` recherche le fichier de manifeste de l’outil qui est dans la portée du répertoire actif et installe les outils qui y sont répertoriés. Pour plus d’informations sur les fichiers manifestes, consultez [installer un outil local](global-tools.md#install-a-local-tool) et [appeler un outil local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

Nom/ID du package NuGet qui contient l’outil .NET Core à installer.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`--add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`--tool-manifest <PATH>`**

  Chemin d’accès au fichier manifeste.

- **`--disable-parallel`**

  Empêcher la restauration en parallèle de plusieurs projets.

- **`--ignore-failed-sources`**

  Considérer les défaillances de la source du package comme des avertissements.

- **`--no-cache`**

  Ne pas mettre en cache les packages et les requêtes http.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’authentifier).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="example"></a>Exemple

- **`dotnet tool restore`**

  Restaure les outils locaux pour le répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
