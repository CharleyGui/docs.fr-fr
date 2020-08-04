---
title: outil dotnet-trace-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517306"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>utilitaire d’analyse des performances dotnet-trace

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="install-dotnet-trace"></a>Installer dotnet-trace

Installez `dotnet-trace` le [package NuGet](https://www.nuget.org/packages/dotnet-trace) à l’aide de la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Description

L' `dotnet-trace` outil :

* Est un outil .NET Core multiplateforme.
* Active la collecte des traces .NET Core d’un processus en cours d’exécution sans profileur natif.
* Repose `EventPipe` sur la technologie multiplateforme du Runtime .net core.
* Offre la même expérience sur Windows, Linux ou macOS.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`--version`**

  Affiche la version de l’utilitaire dotnet-trace.

## <a name="commands"></a>Commandes

| Commande                                                   |
|-----------------------------------------------------------|
| [dotnet-collecte des traces](#dotnet-trace-collect)             |
| [conversion dotnet-trace](#dotnet-trace-convert)             |
| [dotnet-trace PS](#dotnet-trace-ps)                       |
| [liste de suivi dotnet-profils](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-collecte des traces

Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a>Options

- **`--buffersize <size>`**

  Définit la taille de la mémoire tampon circulaire en mémoire, en mégaoctets. 256 Mo par défaut.

- **`--clreventlevel <clreventlevel>`**

  Commentaires des événements CLR à émettre.

- **`--clrevents <clrevents>`**

  Liste des événements du runtime CLR à émettre.

- **`--format {Chromium|NetTrace|Speedscope}`**

  Définit le format de sortie pour la conversion du fichier de trace. Par défaut, il s’agit de `NetTrace`.

- **`-n, --name <name>`**

  Nom du processus à partir duquel la trace doit être collectée.

- **`-o|--output <trace-file-path>`**

  Chemin de sortie pour les données de trace collectées. S’il n’est pas spécifié, la valeur par défaut est `trace.nettrace` .

- **`-p|--process-id <PID>`**

  ID de processus à partir duquel la trace doit être collectée.

- **`--profile <profile-name>`**

  Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.

- **`--providers <list-of-comma-separated-providers>`**

  Liste séparée par des virgules des `EventPipe` fournisseurs à activer. Ces fournisseurs complètent tous les fournisseurs implicites par `--profile <profile-name>` . S’il existe une incohérence pour un fournisseur particulier, cette configuration est prioritaire par rapport à la configuration implicite à partir du profil.

  Cette liste de fournisseurs se présente sous la forme suivante :

  - `Provider[,Provider]`
  - `Provider`se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .
  - `KeyValueArgs`se présente sous la forme : `[key1=value1][;key2=value2]` .

## <a name="dotnet-trace-convert"></a>conversion dotnet-trace

Convertit les `nettrace` traces en d’autres formats pour les utiliser avec d’autres outils d’analyse de trace.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Fichier de trace d’entrée à convertir. La valeur par défaut est *trace. NetTrace*.

### <a name="options"></a>Options

- **`--format <Chromium|NetTrace|Speedscope>`**

  Définit le format de sortie pour la conversion du fichier de trace.

- **`-o|--output <output-filename>`**

  Nom du fichier de sortie. L’extension du format cible sera ajoutée.

## <a name="dotnet-trace-ps"></a>dotnet-trace PS

 Répertorie les processus dotnet à partir desquels les traces peuvent être collectées.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>liste de suivi dotnet-profils

Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Collecter une trace avec dotnet-trace

Pour collecter des traces à l’aide de `dotnet-trace` :

- Obtient l’identificateur de processus (PID) de l’application .NET Core à partir duquel collecter les traces.

  - Sur Windows, vous pouvez utiliser le gestionnaire des tâches ou la `tasklist` commande, par exemple.
  - Sur Linux, par exemple, la `ps` commande.
  - [dotnet-trace PS](#dotnet-trace-ps)

- Exécutez la commande suivante :

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  La commande précédente génère une sortie similaire à ce qui suit :

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Arrêtez la collecte en appuyant sur la `<Enter>` touche. `dotnet-trace`terminera la journalisation des événements dans le fichier *trace. NetTrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Afficher la trace capturée à partir de dotnet-trace

Sur Windows, les fichiers *. NetTrace* peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse : pour les traces collectées sur d’autres plateformes, le fichier de trace peut être déplacé vers un ordinateur Windows à afficher sur PerfView.

Sur Linux, la trace peut être affichée en modifiant le format de sortie de `dotnet-trace` en `speedscope` . Le format du fichier de sortie peut être modifié à l’aide de l' `-f|--format` option : crée `-f speedscope` `dotnet-trace` un `speedscope` fichier. Vous pouvez choisir entre `nettrace` (option par défaut) et `speedscope` . `Speedscope`les fichiers peuvent être ouverts à l’adresse <https://www.speedscope.app> .

> [!NOTE]
> Le Runtime .NET Core génère des traces au `nettrace` format. Les suivis sont convertis en speedscope (si spécifié) une fois la trace terminée. Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier d’origine `nettrace` est conservé en regard du fichier converti.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Utiliser dotnet-trace pour collecter des valeurs de compteur au fil du temps

`dotnet-trace`puissiez

* Utilisez `EventCounter` pour la surveillance de l’intégrité de base dans les environnements sensibles aux performances. Par exemple, en production.
* Collectez les traces afin qu’elles n’aient pas besoin d’être affichées en temps réel.

Par exemple, pour collecter les valeurs de compteur de performance du runtime, utilisez la commande suivante :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

La commande précédente indique aux compteurs Runtime de signaler une fois toutes les secondes pour une surveillance de l’intégrité légère. Le remplacement d' `EventCounterIntervalSec=1` une valeur supérieure (par exemple, 60) permet la collecte d’une trace plus petite avec moins de granularité dans les données du compteur.

La commande suivante réduit la surcharge et la taille de trace plus grande que la taille précédente :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

La commande précédente désactive les événements d’exécution et le profileur de pile managée.

## <a name="net-providers"></a>Fournisseurs .NET

Le Runtime .NET Core prend en charge les fournisseurs .NET suivants. .NET Core utilise les mêmes mots clés pour activer `Event Tracing for Windows (ETW)` et les `EventPipe` suivis.

| Nom du fournisseur                            | Informations |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Fournisseur de runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Mots clés du runtime CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Fournisseur d’arrêt](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Mots clés d’arrêt du CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Active l’exemple de profileur. |
