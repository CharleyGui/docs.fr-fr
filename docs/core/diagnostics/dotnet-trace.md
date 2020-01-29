---
title: outil dotnet-trace-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737646"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>utilitaire d’analyse des performances dotnet-trace

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="install-dotnet-trace"></a>Installer dotnet-trace

Installez `dotnet-trace` [package NuGet](https://www.nuget.org/packages/dotnet-trace) à l’aide de la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Résumé

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Description

Outil `dotnet-trace` :

* Est un outil .NET Core multiplateforme.
* Active la collecte des traces .NET Core d’un processus en cours d’exécution sans profileur natif.
* Est conçu autour de la technologie `EventPipe` multiplateforme du Runtime .NET Core.
* Offre la même expérience sur Windows, Linux ou macOS.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-Counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commands

| Command                                                     |
| ----------------------------------------------------------- |
| [dotnet-collecte des traces](#dotnet-trace-collect)               |
| [conversion dotnet-trace](#dotnet-trace-convert)               |
| [dotnet-trace PS](#dotnet-trace-ps) |
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

  Définit la taille de la mémoire tampon circulaire en mémoire, en mégaoctets. 256 Mo par défaut.

- **`-o|--output <trace-file-path>`**

  Chemin de sortie pour les données de trace collectées. S’il n’est pas spécifié, la valeur par défaut est `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Liste séparée par des virgules des fournisseurs de `EventPipe` à activer. Ces fournisseurs complètent les fournisseurs de `--profile <profile-name>`. S’il existe une incohérence pour un fournisseur particulier, cette configuration est prioritaire par rapport à la configuration implicite à partir du profil.

  Cette liste de fournisseurs se présente sous la forme suivante :

  - `Provider[,Provider]`
  - `Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.

- **`--format {NetTrace|Speedscope}`**

  Définit le format de sortie pour la conversion du fichier de trace. La valeur par défaut est `NetTrace`,

## <a name="dotnet-trace-convert"></a>conversion dotnet-trace

Convertit `nettrace` suivis en autres formats pour les utiliser avec d’autres outils d’analyse de trace.

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

## <a name="dotnet-trace-ps"></a>dotnet-trace PS

Répertorie les processus dotnet qui peuvent être attachés à.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>liste de suivi dotnet-profils

Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.

### <a name="synopsis"></a>Résumé

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Collecter une trace avec dotnet-trace

Pour collecter des traces à l’aide de `dotnet-trace`:

- Obtient l’identificateur de processus (PID) de l’application .NET Core à partir duquel collecter les traces.

  - Sur Windows, vous pouvez utiliser le gestionnaire des tâches ou la commande `tasklist`, par exemple.
  - Sur Linux, par exemple, la commande `ps`.
  - [dotnet-trace PS](#dotnet-trace-ps)

- Exécutez la commande suivante : .

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

- Arrêtez la collecte en appuyant sur la touche `<Enter>`. `dotnet-trace` terminera la journalisation des événements dans le fichier *trace. NetTrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Afficher la trace capturée à partir de dotnet-trace

Sur Windows, les fichiers *. NetTrace* peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse : pour les traces collectées sur d’autres plateformes, le fichier de trace peut être déplacé vers un ordinateur Windows à afficher sur PerfView.

Sur Linux, la trace peut être affichée en modifiant le format de sortie de `dotnet-trace` sur `speedscope`. Le format du fichier de sortie peut être modifié à l’aide de l’option `-f|--format` `-f speedscope` permet de créer `dotnet-trace` un fichier de `speedscope`. Vous pouvez choisir entre `nettrace` (option par défaut) et `speedscope`. `Speedscope` fichiers peuvent être ouverts à <https://www.speedscope.app>.

> [!NOTE]
> Le Runtime .NET Core génère des traces au format `nettrace`. Les suivis sont convertis en speedscope (si spécifié) une fois la trace terminée. Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier `nettrace` d’origine est conservé en regard du fichier converti.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Utiliser dotnet-trace pour collecter des valeurs de compteur au fil du temps

`dotnet-trace` pouvez :

* Utilisez `EventCounter` pour la surveillance de l’intégrité de base dans les environnements sensibles aux performances. Par exemple, en production.
* Collectez les traces afin qu’elles n’aient pas besoin d’être affichées en temps réel.

Par exemple, pour collecter les valeurs de compteur de performance du runtime, utilisez la commande suivante :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

La commande précédente indique aux compteurs Runtime de signaler une fois toutes les secondes pour une surveillance de l’intégrité légère. Le remplacement d' `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) permet la collecte d’une trace plus petite avec moins de granularité dans les données de compteur.

La commande suivante réduit la surcharge et la taille de trace plus grande que la taille précédente :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

La commande précédente désactive les événements d’exécution et le profileur de pile managée.

## <a name="net-providers"></a>Fournisseurs .NET

Le Runtime .NET Core prend en charge les fournisseurs .NET suivants. .NET Core utilise les mêmes mots clés pour activer les suivis `Event Tracing for Windows (ETW)` et `EventPipe`.

| Nom du fournisseur                            | Informations |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Fournisseur du Runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Mots clés du runtime CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Fournisseur d’arrêt](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Mots clés d’arrêt du CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Active l’exemple de profileur. |
