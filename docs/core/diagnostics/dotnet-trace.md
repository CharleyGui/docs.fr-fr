---
title: outil dotnet-trace - .NET Core
description: Installation et utilisation de l’outil de ligne de commande pointnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: 6880c3721e4cab12677bd02c82ca944cc9812670
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888083"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>utilitaire d’analyse de performance pointnet-trace

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

## <a name="install-dotnet-trace"></a>Installer dotnet-trace

Installer `dotnet-trace` [le paquet NuGet](https://www.nuget.org/packages/dotnet-trace) avec l’outil [dotnet installer](../tools/dotnet-tool-install.md) la commande :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Description

L’outil `dotnet-trace` :

* Est un outil multiplateforme .NET Core.
* Permet la collecte de traces de base .NET d’un processus en cours d’exécution sans profiler natif.
* Est construit autour de `EventPipe` la technologie multi-plateforme du temps d’exécution .NET Core.
* Offre la même expérience sur Windows, Linux ou macOS.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire pointnet-trace.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                                     |
| ----------------------------------------------------------- |
| [dotnet-trace recueillir](#dotnet-trace-collect)               |
| [converti à la trace dotnet](#dotnet-trace-convert)               |
| [dotnet-trace ps](#dotnet-trace-ps) |
| [pointnet-trace liste-profils](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-trace recueillir

Recueille une trace diagnostique à partir d’un processus en cours d’exécution.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  Le processus pour recueillir la trace de.

- **`--buffersize <size>`**

  Définit la taille du tampon circulaire en mémoire, en mégaoctets. Par défaut 256 Mo.

- **`-o|--output <trace-file-path>`**

  La trajectoire de sortie des données de trace recueillies. S’il n’est `trace.nettrace`pas spécifié, il par défaut à .

- **`--providers <list-of-comma-separated-providers>`**

  Une liste de fournisseurs `EventPipe` séparées par virgule à permettre. Ces fournisseurs complètent `--profile <profile-name>`tous les fournisseurs impliqués par . S’il y a une incohérence pour un fournisseur particulier, cette configuration prime sur la configuration implicite du profil.

  Cette liste de fournisseurs est dans la forme:

  - `Provider[,Provider]`
  - `Provider`est dans la `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`forme: .
  - `KeyValueArgs`est dans la `[key1=value1][;key2=value2]`forme: .

- **`--profile <profile-name>`**

  Un ensemble de configurations de fournisseurs prédéfinis qui permet de préciser succinctement les scénarios de traçage courants.

- **`--format {NetTrace|Speedscope}`**

  Définit le format de sortie pour la conversion de fichiers traces. Par défaut, il s’agit de `NetTrace`.

## <a name="dotnet-trace-convert"></a>converti à la trace dotnet

Convertit `nettrace` les traces en formats alternatifs pour une utilisation avec d’autres outils d’analyse de traces.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Fichier de trace d’entrée à convertir. Défauts de *trace.nettrace*.

### <a name="options"></a>Options

- **`--format <NetTrace|Speedscope>`**

  Définit le format de sortie pour la conversion de fichiers traces.

- **`-o|--output <output-filename>`**

  Nom de fichier de sortie. L’extension du format cible sera ajoutée.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

Répertorie les processus dotnet auxquels on peut s’attacher.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>pointnet-trace liste-profils

Répertorie les profils de traçage pré-construits avec une description des fournisseurs et des filtres dans chaque profil.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Recueillir une trace avec dotnet-trace

Pour recueillir des `dotnet-trace`traces à l’aide de :

- Obtenez l’identifiant de processus (PID) de l’application .NET Core pour recueillir des traces à partir de.

  - Sur Windows, vous pouvez utiliser `tasklist` Task Manager ou la commande, par exemple.
  - Sur Linux, par `ps` exemple, la commande.
  - [dotnet-trace ps](#dotnet-trace-ps)

- Exécutez la commande suivante :

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  La commande précédente génère des sorties similaires à celles suivantes :

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Arrêtez la collecte `<Enter>` en appuyant sur la clé. `dotnet-trace`terminera les événements d’enregistrement au fichier *trace.nettrace.*

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Voir la trace capturée à partir de dotnet-trace

Sur Windows, les fichiers *.nettrace* peuvent être consultés sur [PerfView](https://github.com/microsoft/perfview) pour analyse : Pour les traces collectées sur d’autres plates-formes, le fichier de trace peut être déplacé vers une machine Windows pour être consulté sur PerfView.

Sur Linux, la trace peut être consultée en changeant le format de sortie de `dotnet-trace` . `speedscope` Le format de fichier de `-f|--format` sortie `-f speedscope` peut `dotnet-trace` être `speedscope` modifié en utilisant l’option - fera produire un fichier. Vous pouvez `nettrace` choisir entre (l’option par défaut) et `speedscope`. `Speedscope`fichiers peuvent être <https://www.speedscope.app>ouverts à .

> [!NOTE]
> Le runtime .NET Core génère `nettrace` des traces dans le format. Les traces sont converties en speedscope (si spécifié) une fois la trace terminée. Étant donné que certaines conversions peuvent `nettrace` entraîner une perte de données, le fichier d’origine est conservé à côté du fichier converti.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Utilisez dotnet-trace pour collecter des valeurs de compteur au fil du temps

`dotnet-trace`Anc:

* Utilisation `EventCounter` pour la surveillance de base de la santé dans les environnements sensibles aux performances. Par exemple, en production.
* Recueillir des traces afin qu’ils n’aient pas besoin d’être vus en temps réel.

Par exemple, pour collecter les valeurs de compteur de performances en temps d’exécution, utilisez la commande suivante :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

La commande précédente indique aux compteurs de temps d’exécution de signaler une fois par seconde pour la surveillance légère de la santé. Remplacer `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) permet de collecte d’une trace plus petite avec moins de granularité dans les données de compteur.

La commande suivante réduit la surcharge et la taille des traces plus que la précédente :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

La commande précédente désactive les événements de temps d’exécution et le profileur de pile géré.

## <a name="net-providers"></a>.FOURNISSEURS NET

Le temps d’exécution .NET Core prend en charge les fournisseurs .NET suivants. .NET Core utilise les mêmes `Event Tracing for Windows (ETW)` mots `EventPipe` clés pour activer à la fois et des traces.

| Nom du fournisseur                            | Information |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Fournisseur de runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Mots-clés CLR Runtime](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Fournisseur d’arrêt](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Mots-clés CLR Rundown](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Permet au profileur d’échantillon. |
