---
title: dotnet-symbol-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-symbol.
ms.date: 08/26/2020
ms.openlocfilehash: feaa64ad756878f85b829ab0cecf6ea2736014ba
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598339"
---
# <a name="symbol-downloader-dotnet-symbol"></a>Téléchargeur de symboles (dotnet-Symbol)

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="install-dotnet-symbol"></a>Installer dotnet-Symbol

Pour installer la dernière version Release du `dotnet-symbol` [package NuGet](https://www.nuget.org/packages/dotnet-symbol), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a>Description

L' `dotnet-symbol` outil Global télécharge les fichiers (symboles, DAC, modules, etc.) nécessaires pour le débogage des vidages et des minidumps principaux. Cela peut être utile lors du débogage des vidages capturés sur un autre ordinateur. `dotnet-symbol` peut télécharger les modules et les symboles nécessaires pour analyser le vidage.

## <a name="options"></a>Options

- **`--microsoft-symbol-server`**

  Ajoutez le http://msdl.microsoft.com/download/symbols chemin d’accès du serveur de symboles' ' (valeur par défaut).

- **`--server-path <symbol server path>`**

  Ajoutez un serveur de symboles au chemin d’accès du serveur.

- **`authenticated-server-path <pat> <server path>`**

  Ajoutez un serveur de symboles authentifié au chemin d’accès du serveur à l’aide d’un jeton d’accès personnel (PAT).

- **`--cache-directory <file cache directory>`**

  Ajoute un répertoire de cache.

- **`--recurse-subdirectories`**

  Traitez les fichiers d’entrée dans tous les sous-répertoires.

- **`--host-only`**

  Téléchargez uniquement le programme hôte (c’est-à-dire dotnet) dont lldb a besoin pour charger les vidages principaux.

- **`--symbols`**

  Télécharger les fichiers de symboles (. pdb,. dbg,. nain).

- **`--modules`**

  Téléchargez les fichiers de module (. dll,. so,. dylib).

- **`--debugging`**

  Téléchargez les modules de débogage spéciaux (DAC, DBI, SOS).

- **`--windows-pdbs`**

  Forcez le téléchargement des fichiers PDB Windows lorsque des fichiers PDB portables sont également disponibles.

- **`-o, --output <output directory>`**

  Définissez le répertoire de sortie. Sinon, écrivez en regard du fichier d’entrée (valeur par défaut).

- **`-d, --diagnostics`**

  Activez la sortie de diagnostic.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="download-symbols"></a>Télécharger des symboles

S’exécuter `dotnet-symbol` sur un fichier dump, par défaut, télécharge tous les modules, les symboles et les fichiers DAC/DBI nécessaires pour déboguer le dump, y compris les assemblys managés. Dans la mesure où SOS peut télécharger des symboles si nécessaire, la plupart des vidages noyau Linux peuvent être analysés à l’aide de lldb avec uniquement les modules d’hôte (dotnet) et de débogage. Pour obtenir ces fichiers nécessaires au diagnostic d’un vidage de base avec lldb, exécutez :

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a>Dépanner

- 404 introuvable lors du téléchargement des symboles.

   Le téléchargement de symboles n’est pris en charge que pour les versions officielles du Runtime .NET Core acquises par le biais de canaux officiels tels que [le site Web officiel](https://dotnet.microsoft.com/download/dotnet-core) et les [sources par défaut dans les scripts d’installation dotnet](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-scripts). Une erreur 404 lors du téléchargement des fichiers de débogage peut indiquer que le dump a été créé avec un Runtime .NET Core à partir d’une autre source, telle que celle générée à partir de la source localement ou pour un distribution Linux particulier, ou à partir de sites de la communauté tels que Archlinux. Dans ce cas, le fichier nécessaire pour le débogage (dotnet, libcoreclr.so et libmscordaccore.so) doit être copié à partir de ces sources ou de l’environnement dans lequel le fichier de vidage a été créé.
