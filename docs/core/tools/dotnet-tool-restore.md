---
title: commande de restauration de l’outil dotnet
description: La commande de restauration de l’outil dotnet installe sur votre machine les outils locaux .NET qui sont dans l’étendue du répertoire actif.
ms.date: 02/14/2020
ms.openlocfilehash: 87bdfb77cda361b800f107c565cbbed6ad75ec78
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794858"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="name"></a>Nom

`dotnet tool restore` -Installe les outils locaux .NET qui sont dans l’étendue du répertoire actif.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [--tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>Description

La `dotnet tool restore` commande recherche le fichier de manifeste de l’outil qui est dans la portée du répertoire actif et installe les outils qui y sont répertoriés. Pour plus d’informations sur les fichiers manifestes, consultez [installer un outil local](global-tools.md#install-a-local-tool) et [appeler un outil local](global-tools.md#invoke-a-local-tool).

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

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="example"></a>Exemple

- **`dotnet tool restore`**

  Restaure les outils locaux pour le répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET](global-tools.md)
- [Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET](local-tools-how-to-use.md)
