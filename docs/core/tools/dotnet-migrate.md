---
title: Commande dotnet migrate
description: La commande dotnet migrate permet de migrer un projet et l’ensemble de ses dépendances.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463637"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK

## <a name="name"></a>Nom

`dotnet migrate` : migre un projet .NET Core Preview 2 vers un projet de style SDK .NET Core.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a>Description

Cette commande est dépréciée. La `dotnet migrate` commande n’est plus disponible à partir de .NET Core 3.0 SDK. Il ne peut migrer un projet Preview 2 .NET Core vers un projet 1.x .NET Core, qui est hors de support.

Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient. Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution.

La migration peut être effectuée sur les ressources suivantes :

* Un projet unique en spécifiant le fichier *project.json* à migrer.
* Tous les répertoires spécifiés dans le fichier *global.json* en passant un chemin du fichier *global.json*.
* Un fichier *solution.sln*, où il migre les projets référencés dans la solution.
* Sur tous les sous-répertoires du répertoire donné de manière récursive.

La commande `dotnet migrate` conserve le fichier *project.json* migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas. Ce comportement est remplacé à l’aide de l’option `--skip-backup`.

Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT). Si vous utilisez l’option `--report-file <REPORT_FILE>`, la sortie est enregistrée dans le fichier spécifié.

La commande `dotnet migrate` prend en charge uniquement les projets *project.json* Preview 2 valides. Cela signifie que vous ne pouvez pas l’utiliser pour migrer des projets *project.json* DNX ou Preview 1 directement vers des projets MSBuild/csproj. Vous devez tout d’abord migrer manuellement le projet vers un projet *project.json* Preview 2, puis utiliser la commande `dotnet migrate` pour migrer le projet.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Le chemin d’accès à l’un des éléments suivants :

* Un fichier *project.json* à migrer.
* Un fichier *global.json* : les dossiers spécifiés dans *global.json* sont migrés.
* Un fichier *solution.sln* : les projets référencés dans la solution sont migrés.
* Un répertoire à migrer : recherche de manière récursive des fichiers *project.json* à migrer à l’intérieur du répertoire spécifié.

Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

`--format-report-file-json <REPORT_FILE>`

Génère le fichier de rapport de migration au format JSON plutôt que sous la forme de messages utilisateur.

`-h|--help`

Affiche une aide brève pour la commande.

`-r|--report-file <REPORT_FILE>`

Génère un rapport de migration dans un fichier, en plus de le faire dans la console.

`-s|--skip-project-references [Debug|Release]`

Ignore la migration des références de projet. Par défaut, les références de projet sont migrées de manière récursive.

`--skip-backup`

Ignore le déplacement de *project.json*, *global.json* et *\*.xproj* vers un répertoire `backup` après la migration.

`-t|--template-file <TEMPLATE_FILE>`

Fichier csproj de modèle à utiliser pour la migration. Par défaut, le même modèle que celui déposé par `dotnet new console` est utilisé.

`-v|--sdk-package-version <VERSION>`

Version du package de SDK à référencer dans l’application migrée. La valeur par défaut est la version du SDK dans `dotnet new`.

`-x|--xproj-file <FILE>`

Chemin du fichier xproj à utiliser. Requis quand il existe plusieurs xproj dans un répertoire de projet.

## <a name="examples"></a>Exemples

Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :

`dotnet migrate`

Migrer tous les projets que le fichier *global.json* contient :

`dotnet migrate path/to/global.json`

Migrer uniquement le projet actuel et aucune dépendance de projet à projet (P2P). En outre, utilisez une version de Kit de développement logiciel (SDK) spécifique :

`dotnet migrate -s -v 1.0.0-preview4`
