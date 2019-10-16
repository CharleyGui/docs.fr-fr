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
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="7b24e-103">Utilitaire de trace pour l’analyse des performances (`dotnet-trace`)</span><span class="sxs-lookup"><span data-stu-id="7b24e-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="7b24e-104">**Cet article s’applique à :** .net Core 3,0 SDK et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="7b24e-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="7b24e-105">Installation de `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="7b24e-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="7b24e-106">Pour installer la dernière version Release du [package NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="7b24e-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="7b24e-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="7b24e-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="7b24e-108">Description</span><span class="sxs-lookup"><span data-stu-id="7b24e-108">Description</span></span>

<span data-ttu-id="7b24e-109">L’outil `dotnet-trace` est un outil global de l’interface CLI multiplateforme qui permet la collecte des traces .NET Core d’un processus en cours d’exécution sans qu’un profileur natif ne soit impliqué.</span><span class="sxs-lookup"><span data-stu-id="7b24e-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="7b24e-110">Il est basé sur la technologie multiplateforme `EventPipe` du Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b24e-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="7b24e-111">`dotnet-trace` offre la même expérience sur Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="7b24e-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="7b24e-112">Options</span><span class="sxs-lookup"><span data-stu-id="7b24e-112">Options</span></span>

- **`--version`**

<span data-ttu-id="7b24e-113">Affichez la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="7b24e-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="7b24e-114">Affichez l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7b24e-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="7b24e-115">Commandes</span><span class="sxs-lookup"><span data-stu-id="7b24e-115">Commands</span></span>

| <span data-ttu-id="7b24e-116">Commande</span><span class="sxs-lookup"><span data-stu-id="7b24e-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="7b24e-117">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="7b24e-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="7b24e-118">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="7b24e-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="7b24e-119">liste dotnet-trace-processus</span><span class="sxs-lookup"><span data-stu-id="7b24e-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="7b24e-120">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="7b24e-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="7b24e-121">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="7b24e-121">dotnet-trace collect</span></span>

<span data-ttu-id="7b24e-122">Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7b24e-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b24e-123">Résumé</span><span class="sxs-lookup"><span data-stu-id="7b24e-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="7b24e-124">Options</span><span class="sxs-lookup"><span data-stu-id="7b24e-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7b24e-125">Processus à partir duquel la trace doit être collectée.</span><span class="sxs-lookup"><span data-stu-id="7b24e-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="7b24e-126">Définit la taille de la mémoire tampon circulaire en mémoire en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="7b24e-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="7b24e-127">256 Mo par défaut.</span><span class="sxs-lookup"><span data-stu-id="7b24e-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="7b24e-128">Chemin de sortie pour les données de trace collectées.</span><span class="sxs-lookup"><span data-stu-id="7b24e-128">The output path for the collected trace data.</span></span> <span data-ttu-id="7b24e-129">S’il n’est pas spécifié, sa valeur par défaut est `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="7b24e-130">Liste séparée par des virgules des fournisseurs `EventPipe` à activer.</span><span class="sxs-lookup"><span data-stu-id="7b24e-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="7b24e-131">Ces fournisseurs complètent tous les fournisseurs implicites par `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="7b24e-132">S’il existe une incohérence pour un fournisseur particulier, la configuration est prioritaire par rapport à la configuration implicite à partir du profil.</span><span class="sxs-lookup"><span data-stu-id="7b24e-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="7b24e-133">Cette liste de fournisseurs se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="7b24e-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="7b24e-134">`Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="7b24e-135">`KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="7b24e-136">Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.</span><span class="sxs-lookup"><span data-stu-id="7b24e-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="7b24e-137">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="7b24e-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="7b24e-138">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="7b24e-138">dotnet-trace convert</span></span>

<span data-ttu-id="7b24e-139">Convertit les traces `nettrace` en d’autres formats pour les utiliser avec d’autres outils d’analyse de trace.</span><span class="sxs-lookup"><span data-stu-id="7b24e-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b24e-140">Résumé</span><span class="sxs-lookup"><span data-stu-id="7b24e-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="7b24e-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="7b24e-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="7b24e-142">Fichier de trace d’entrée à convertir.</span><span class="sxs-lookup"><span data-stu-id="7b24e-142">Input trace file to be converted.</span></span> <span data-ttu-id="7b24e-143">La valeur par défaut est *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="7b24e-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="7b24e-144">Options</span><span class="sxs-lookup"><span data-stu-id="7b24e-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="7b24e-145">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="7b24e-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="7b24e-146">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="7b24e-146">Output filename.</span></span> <span data-ttu-id="7b24e-147">L’extension du format cible sera ajoutée.</span><span class="sxs-lookup"><span data-stu-id="7b24e-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="7b24e-148">liste dotnet-trace-processus</span><span class="sxs-lookup"><span data-stu-id="7b24e-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="7b24e-149">Répertorie les processus dotnet qui peuvent être suivis.</span><span class="sxs-lookup"><span data-stu-id="7b24e-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b24e-150">Résumé</span><span class="sxs-lookup"><span data-stu-id="7b24e-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="7b24e-151">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="7b24e-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="7b24e-152">Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.</span><span class="sxs-lookup"><span data-stu-id="7b24e-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b24e-153">Résumé</span><span class="sxs-lookup"><span data-stu-id="7b24e-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="7b24e-154">Collecter une trace avec `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="7b24e-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="7b24e-155">Pour collecter des traces à l’aide de `dotnet-trace`, vous devez d’abord Rechercher l’identificateur de processus (PID) de l’application .NET Core à partir de laquelle collecter les traces.</span><span class="sxs-lookup"><span data-stu-id="7b24e-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="7b24e-156">Sous Windows, il existe des options telles que l’utilisation du gestionnaire des tâches ou la commande `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="7b24e-157">Sur Linux, l’option trivial peut utiliser la commande `ps`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="7b24e-158">Vous pouvez également utiliser la commande [dotnet-trace List-Processes](#dotnet-trace-list-processes) pour savoir quels sont les processus .net core en cours d’exécution, ainsi que leurs PID.</span><span class="sxs-lookup"><span data-stu-id="7b24e-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="7b24e-159">Exécutez ensuite la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7b24e-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="7b24e-160">Enfin, arrêtez la collecte en appuyant sur la touche `<Enter>`, et `dotnet-trace` terminera la journalisation des événements dans le fichier `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="7b24e-161">Affichage de la trace capturée à partir de `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="7b24e-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="7b24e-162">Sur Windows, les fichiers `.nettrace` peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse, tout comme les traces collectées avec ETW ou LTTng.</span><span class="sxs-lookup"><span data-stu-id="7b24e-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="7b24e-163">Pour les traces collectées sur Linux, vous pouvez déplacer la trace vers un ordinateur Windows à afficher sur PerfView.</span><span class="sxs-lookup"><span data-stu-id="7b24e-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="7b24e-164">Vous pouvez également afficher le suivi sur un ordinateur Linux en modifiant le format de sortie de `dotnet-trace` à `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="7b24e-165">Vous pouvez modifier le format du fichier de sortie à l’aide de l’option `-f|--format`-`-f speedscope` fera `dotnet-trace` pour produire un fichier `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="7b24e-166">Vous pouvez actuellement choisir entre `nettrace` (option par défaut) et `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="7b24e-167">`Speedscope` fichiers peuvent être ouverts à <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="7b24e-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="7b24e-168">Le Runtime .NET Core génère des traces au format `nettrace`, et elles sont converties en speedscope (si spécifié) une fois la trace terminée.</span><span class="sxs-lookup"><span data-stu-id="7b24e-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="7b24e-169">Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier d’origine `nettrace` est conservé en regard du fichier converti.</span><span class="sxs-lookup"><span data-stu-id="7b24e-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="7b24e-170">Utilisation de `dotnet-trace` pour collecter des valeurs de compteur au fil du temps</span><span class="sxs-lookup"><span data-stu-id="7b24e-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="7b24e-171">Si vous essayez d’utiliser `EventCounter` pour la surveillance de l’intégrité de base dans des paramètres sensibles aux performances comme des environnements de production et que vous souhaitez collecter des traces au lieu de les regarder en temps réel, vous pouvez le faire avec `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="7b24e-172">Par exemple, si vous souhaitez collecter les valeurs des compteurs de performance du runtime, vous pouvez utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7b24e-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="7b24e-173">Cette commande indique aux compteurs Runtime d’être signalés une fois par seconde pour une surveillance de l’intégrité légère.</span><span class="sxs-lookup"><span data-stu-id="7b24e-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="7b24e-174">Le remplacement de `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) vous permet de collecter une trace plus petite avec moins de granularité dans les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="7b24e-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="7b24e-175">Si vous souhaitez désactiver les événements d’exécution pour réduire encore davantage la surcharge (et la taille de la trace), vous pouvez utiliser la commande suivante pour désactiver les événements d’exécution et Managed Stack Profiler.</span><span class="sxs-lookup"><span data-stu-id="7b24e-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="7b24e-176">Fournisseurs .NET</span><span class="sxs-lookup"><span data-stu-id="7b24e-176">.NET Providers</span></span>

<span data-ttu-id="7b24e-177">Le Runtime .NET Core prend en charge les fournisseurs .NET suivants.</span><span class="sxs-lookup"><span data-stu-id="7b24e-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="7b24e-178">.NET Core utilise les mêmes mots clés pour activer à la fois les traces `Event Tracing for Windows (ETW)` et `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="7b24e-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="7b24e-179">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="7b24e-179">Provider name</span></span>                            | <span data-ttu-id="7b24e-180">Informations</span><span class="sxs-lookup"><span data-stu-id="7b24e-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="7b24e-181">Fournisseur du Runtime</span><span class="sxs-lookup"><span data-stu-id="7b24e-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="7b24e-182">Mots clés du runtime CLR</span><span class="sxs-lookup"><span data-stu-id="7b24e-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="7b24e-183">Fournisseur d’arrêt</span><span class="sxs-lookup"><span data-stu-id="7b24e-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="7b24e-184">Mots clés d’arrêt du CLR</span><span class="sxs-lookup"><span data-stu-id="7b24e-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="7b24e-185">Active l’exemple de profileur.</span><span class="sxs-lookup"><span data-stu-id="7b24e-185">Enables the sample profiler.</span></span> |
