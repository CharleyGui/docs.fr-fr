---
title: dotnet-trace-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-trace.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321581"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>Utilitaire de trace pour l’analyse des performances (`dotnet-trace`)

**Cet article s’applique à :** .net Core 3,0 SDK et versions ultérieures

## <a name="installing-dotnet-trace"></a>Installation de `dotnet-trace`

Pour installer la dernière version Release du [package NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Résumé

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Description

L’outil `dotnet-trace` est un outil global de l’interface CLI multiplateforme qui permet la collecte des traces .NET Core d’un processus en cours d’exécution sans qu’un profileur natif ne soit impliqué. Il est basé sur la technologie multiplateforme `EventPipe` du Runtime .NET Core. `dotnet-trace` offre la même expérience sur Windows, Linux ou macOS.

## <a name="options"></a>Options

- **`--version`**

Affichez la version de l’utilitaire dotnet-Counters.

- **`-h|--help`**

Affichez l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                                     |
| ----------------------------------------------------------- |
| [dotnet-collecte des traces](#dotnet-trace-collect)               |
| [conversion dotnet-trace](#dotnet-trace-convert)               |
| [liste dotnet-trace-processus](#dotnet-trace-list-processes) |
| [liste de suivi dotnet-profils](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-collecte des traces

Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  Processus à partir duquel la trace doit être collectée.

- **`--buffersize <size>`**

  Définit la taille de la mémoire tampon circulaire en mémoire en mégaoctets. 256 Mo par défaut.

- **`-o|--output <trace-file-path>`**

  Chemin de sortie pour les données de trace collectées. S’il n’est pas spécifié, sa valeur par défaut est `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Liste séparée par des virgules des fournisseurs `EventPipe` à activer. Ces fournisseurs complètent tous les fournisseurs implicites par `--profile <profile-name>`. S’il existe une incohérence pour un fournisseur particulier, la configuration est prioritaire par rapport à la configuration implicite à partir du profil.

  Cette liste de fournisseurs se présente sous la forme suivante :

  - `Provider[,Provider]`
  - `Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.

- **`--format <NetTrace|Speedscope>`**

  Définit le format de sortie pour la conversion du fichier de trace.

## <a name="dotnet-trace-convert"></a>conversion dotnet-trace

Convertit les traces `nettrace` en d’autres formats pour les utiliser avec d’autres outils d’analyse de trace.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Fichier de trace d’entrée à convertir. La valeur par défaut est *trace. NetTrace*.

### <a name="options"></a>Options

- **`--format <NetTrace|Speedscope>`**

  Définit le format de sortie pour la conversion du fichier de trace.

- **`-o|--output <output-filename>`**

  Nom du fichier de sortie. L’extension du format cible sera ajoutée.

## <a name="dotnet-trace-list-processes"></a>liste dotnet-trace-processus

Répertorie les processus dotnet qui peuvent être suivis.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>liste de suivi dotnet-profils

Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Collecter une trace avec `dotnet-trace`

- Pour collecter des traces à l’aide de `dotnet-trace`, vous devez d’abord Rechercher l’identificateur de processus (PID) de l’application .NET Core à partir de laquelle collecter les traces.

  - Sous Windows, il existe des options telles que l’utilisation du gestionnaire des tâches ou la commande `tasklist`.
  - Sur Linux, l’option trivial peut utiliser la commande `ps`.

Vous pouvez également utiliser la commande [dotnet-trace List-Processes](#dotnet-trace-list-processes) pour savoir quels sont les processus .net core en cours d’exécution, ainsi que leurs PID.

- Exécutez ensuite la commande suivante :

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- Enfin, arrêtez la collecte en appuyant sur la touche `<Enter>`, et `dotnet-trace` terminera la journalisation des événements dans le fichier `trace.nettrace`.

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>Affichage de la trace capturée à partir de `dotnet-trace`

Sur Windows, les fichiers `.nettrace` peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse, tout comme les traces collectées avec ETW ou LTTng. Pour les traces collectées sur Linux, vous pouvez déplacer la trace vers un ordinateur Windows à afficher sur PerfView.

Vous pouvez également afficher le suivi sur un ordinateur Linux en modifiant le format de sortie de `dotnet-trace` à `speedscope`. Vous pouvez modifier le format du fichier de sortie à l’aide de l’option `-f|--format`-`-f speedscope` fera `dotnet-trace` pour produire un fichier `speedscope`. Vous pouvez actuellement choisir entre `nettrace` (option par défaut) et `speedscope`. `Speedscope` fichiers peuvent être ouverts à <https://www.speedscope.app>.

> [!NOTE]
> Le Runtime .NET Core génère des traces au format `nettrace`, et elles sont converties en speedscope (si spécifié) une fois la trace terminée. Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier d’origine `nettrace` est conservé en regard du fichier converti.

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>Utilisation de `dotnet-trace` pour collecter des valeurs de compteur au fil du temps

Si vous essayez d’utiliser `EventCounter` pour la surveillance de l’intégrité de base dans des paramètres sensibles aux performances comme des environnements de production et que vous souhaitez collecter des traces au lieu de les regarder en temps réel, vous pouvez le faire avec `dotnet-trace`.

Par exemple, si vous souhaitez collecter les valeurs des compteurs de performance du runtime, vous pouvez utiliser la commande suivante :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Cette commande indique aux compteurs Runtime d’être signalés une fois par seconde pour une surveillance de l’intégrité légère. Le remplacement de `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) vous permet de collecter une trace plus petite avec moins de granularité dans les données de compteur.

Si vous souhaitez désactiver les événements d’exécution pour réduire encore davantage la surcharge (et la taille de la trace), vous pouvez utiliser la commande suivante pour désactiver les événements d’exécution et Managed Stack Profiler.

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>Fournisseurs .NET

Le Runtime .NET Core prend en charge les fournisseurs .NET suivants. .NET Core utilise les mêmes mots clés pour activer à la fois les traces `Event Tracing for Windows (ETW)` et `EventPipe`.

| Nom du fournisseur                            | Informations |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Fournisseur du Runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Mots clés du runtime CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Fournisseur d’arrêt](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Mots clés d’arrêt du CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Active l’exemple de profileur. |
