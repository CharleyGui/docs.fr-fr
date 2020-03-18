---
title: outil dotnet-trace - .NET Core
description: Installation et utilisation de l’outil de ligne de commande pointnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737646"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="ab33e-103">utilitaire d’analyse de performance pointnet-trace</span><span class="sxs-lookup"><span data-stu-id="ab33e-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="ab33e-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ab33e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="ab33e-105">Installer dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ab33e-105">Install dotnet-trace</span></span>

<span data-ttu-id="ab33e-106">Installer `dotnet-trace` [le paquet NuGet](https://www.nuget.org/packages/dotnet-trace) avec l’outil [dotnet installer](../tools/dotnet-tool-install.md) la commande :</span><span class="sxs-lookup"><span data-stu-id="ab33e-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="ab33e-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ab33e-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="ab33e-108">Description</span><span class="sxs-lookup"><span data-stu-id="ab33e-108">Description</span></span>

<span data-ttu-id="ab33e-109">L’outil `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="ab33e-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="ab33e-110">Est un outil multiplateforme .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab33e-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="ab33e-111">Permet la collecte de traces de base .NET d’un processus en cours d’exécution sans profiler natif.</span><span class="sxs-lookup"><span data-stu-id="ab33e-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="ab33e-112">Est construit autour de `EventPipe` la technologie multi-plateforme du temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab33e-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="ab33e-113">Offre la même expérience sur Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="ab33e-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="ab33e-114">Options</span><span class="sxs-lookup"><span data-stu-id="ab33e-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="ab33e-115">Affiche la version de l’utilitaire dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="ab33e-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ab33e-116">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ab33e-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="ab33e-117">Commandes</span><span class="sxs-lookup"><span data-stu-id="ab33e-117">Commands</span></span>

| <span data-ttu-id="ab33e-118">Commande</span><span class="sxs-lookup"><span data-stu-id="ab33e-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="ab33e-119">dotnet-trace recueillir</span><span class="sxs-lookup"><span data-stu-id="ab33e-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="ab33e-120">converti à la trace dotnet</span><span class="sxs-lookup"><span data-stu-id="ab33e-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="ab33e-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="ab33e-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="ab33e-122">pointnet-trace liste-profils</span><span class="sxs-lookup"><span data-stu-id="ab33e-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="ab33e-123">dotnet-trace recueillir</span><span class="sxs-lookup"><span data-stu-id="ab33e-123">dotnet-trace collect</span></span>

<span data-ttu-id="ab33e-124">Recueille une trace diagnostique à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ab33e-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ab33e-125">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ab33e-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="ab33e-126">Options</span><span class="sxs-lookup"><span data-stu-id="ab33e-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="ab33e-127">Le processus pour recueillir la trace de.</span><span class="sxs-lookup"><span data-stu-id="ab33e-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="ab33e-128">Définit la taille du tampon circulaire en mémoire, en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="ab33e-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="ab33e-129">Par défaut 256 Mo.</span><span class="sxs-lookup"><span data-stu-id="ab33e-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="ab33e-130">La trajectoire de sortie des données de trace recueillies.</span><span class="sxs-lookup"><span data-stu-id="ab33e-130">The output path for the collected trace data.</span></span> <span data-ttu-id="ab33e-131">S’il n’est `trace.nettrace`pas spécifié, il par défaut à .</span><span class="sxs-lookup"><span data-stu-id="ab33e-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="ab33e-132">Une liste de fournisseurs `EventPipe` séparées par virgule à permettre.</span><span class="sxs-lookup"><span data-stu-id="ab33e-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="ab33e-133">Ces fournisseurs complètent `--profile <profile-name>`tous les fournisseurs impliqués par .</span><span class="sxs-lookup"><span data-stu-id="ab33e-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="ab33e-134">S’il y a une incohérence pour un fournisseur particulier, cette configuration prime sur la configuration implicite du profil.</span><span class="sxs-lookup"><span data-stu-id="ab33e-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="ab33e-135">Cette liste de fournisseurs est dans la forme:</span><span class="sxs-lookup"><span data-stu-id="ab33e-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="ab33e-136">`Provider`est dans la `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`forme: .</span><span class="sxs-lookup"><span data-stu-id="ab33e-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="ab33e-137">`KeyValueArgs`est dans la `[key1=value1][;key2=value2]`forme: .</span><span class="sxs-lookup"><span data-stu-id="ab33e-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="ab33e-138">Un ensemble de configurations de fournisseurs prédéfinis qui permet de préciser succinctement les scénarios de traçage courants.</span><span class="sxs-lookup"><span data-stu-id="ab33e-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="ab33e-139">Définit le format de sortie pour la conversion de fichiers traces.</span><span class="sxs-lookup"><span data-stu-id="ab33e-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="ab33e-140">Par défaut, il s’agit de `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="ab33e-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="ab33e-141">converti à la trace dotnet</span><span class="sxs-lookup"><span data-stu-id="ab33e-141">dotnet-trace convert</span></span>

<span data-ttu-id="ab33e-142">Convertit `nettrace` les traces en formats alternatifs pour une utilisation avec d’autres outils d’analyse de traces.</span><span class="sxs-lookup"><span data-stu-id="ab33e-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ab33e-143">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ab33e-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="ab33e-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="ab33e-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="ab33e-145">Fichier de trace d’entrée à convertir.</span><span class="sxs-lookup"><span data-stu-id="ab33e-145">Input trace file to be converted.</span></span> <span data-ttu-id="ab33e-146">Défauts de *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="ab33e-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="ab33e-147">Options</span><span class="sxs-lookup"><span data-stu-id="ab33e-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="ab33e-148">Définit le format de sortie pour la conversion de fichiers traces.</span><span class="sxs-lookup"><span data-stu-id="ab33e-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="ab33e-149">Nom de fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="ab33e-149">Output filename.</span></span> <span data-ttu-id="ab33e-150">L’extension du format cible sera ajoutée.</span><span class="sxs-lookup"><span data-stu-id="ab33e-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="ab33e-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="ab33e-151">dotnet-trace ps</span></span>

<span data-ttu-id="ab33e-152">Répertorie les processus dotnet auxquels on peut s’attacher.</span><span class="sxs-lookup"><span data-stu-id="ab33e-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ab33e-153">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ab33e-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="ab33e-154">pointnet-trace liste-profils</span><span class="sxs-lookup"><span data-stu-id="ab33e-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="ab33e-155">Répertorie les profils de traçage pré-construits avec une description des fournisseurs et des filtres dans chaque profil.</span><span class="sxs-lookup"><span data-stu-id="ab33e-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ab33e-156">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ab33e-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="ab33e-157">Recueillir une trace avec dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ab33e-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="ab33e-158">Pour recueillir des `dotnet-trace`traces à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="ab33e-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="ab33e-159">Obtenez l’identifiant de processus (PID) de l’application .NET Core pour recueillir des traces à partir de.</span><span class="sxs-lookup"><span data-stu-id="ab33e-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="ab33e-160">Sur Windows, vous pouvez utiliser `tasklist` Task Manager ou la commande, par exemple.</span><span class="sxs-lookup"><span data-stu-id="ab33e-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="ab33e-161">Sur Linux, par `ps` exemple, la commande.</span><span class="sxs-lookup"><span data-stu-id="ab33e-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="ab33e-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="ab33e-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="ab33e-163">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ab33e-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="ab33e-164">La commande précédente génère des sorties similaires à celles suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab33e-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="ab33e-165">Arrêtez la collecte `<Enter>` en appuyant sur la clé.</span><span class="sxs-lookup"><span data-stu-id="ab33e-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="ab33e-166">`dotnet-trace`terminera les événements d’enregistrement au fichier *trace.nettrace.*</span><span class="sxs-lookup"><span data-stu-id="ab33e-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="ab33e-167">Voir la trace capturée à partir de dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ab33e-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="ab33e-168">Sur Windows, les fichiers *.nettrace* peuvent être consultés sur [PerfView](https://github.com/microsoft/perfview) pour analyse : Pour les traces collectées sur d’autres plates-formes, le fichier de trace peut être déplacé vers une machine Windows pour être consulté sur PerfView.</span><span class="sxs-lookup"><span data-stu-id="ab33e-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="ab33e-169">Sur Linux, la trace peut être consultée en changeant le format de sortie de `dotnet-trace` . `speedscope`</span><span class="sxs-lookup"><span data-stu-id="ab33e-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="ab33e-170">Le format de fichier de `-f|--format` sortie `-f speedscope` peut `dotnet-trace` être `speedscope` modifié en utilisant l’option - fera produire un fichier.</span><span class="sxs-lookup"><span data-stu-id="ab33e-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="ab33e-171">Vous pouvez `nettrace` choisir entre (l’option par défaut) et `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="ab33e-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="ab33e-172">`Speedscope`fichiers peuvent être <https://www.speedscope.app>ouverts à .</span><span class="sxs-lookup"><span data-stu-id="ab33e-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="ab33e-173">Le runtime .NET Core génère `nettrace` des traces dans le format.</span><span class="sxs-lookup"><span data-stu-id="ab33e-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="ab33e-174">Les traces sont converties en speedscope (si spécifié) une fois la trace terminée.</span><span class="sxs-lookup"><span data-stu-id="ab33e-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="ab33e-175">Étant donné que certaines conversions peuvent `nettrace` entraîner une perte de données, le fichier d’origine est conservé à côté du fichier converti.</span><span class="sxs-lookup"><span data-stu-id="ab33e-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="ab33e-176">Utilisez dotnet-trace pour collecter des valeurs de compteur au fil du temps</span><span class="sxs-lookup"><span data-stu-id="ab33e-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="ab33e-177">`dotnet-trace`Anc:</span><span class="sxs-lookup"><span data-stu-id="ab33e-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="ab33e-178">Utilisation `EventCounter` pour la surveillance de base de la santé dans les environnements sensibles aux performances.</span><span class="sxs-lookup"><span data-stu-id="ab33e-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="ab33e-179">Par exemple, en production.</span><span class="sxs-lookup"><span data-stu-id="ab33e-179">For example, in production.</span></span>
* <span data-ttu-id="ab33e-180">Recueillir des traces afin qu’ils n’aient pas besoin d’être vus en temps réel.</span><span class="sxs-lookup"><span data-stu-id="ab33e-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="ab33e-181">Par exemple, pour collecter les valeurs de compteur de performances en temps d’exécution, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ab33e-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="ab33e-182">La commande précédente indique aux compteurs de temps d’exécution de signaler une fois par seconde pour la surveillance légère de la santé.</span><span class="sxs-lookup"><span data-stu-id="ab33e-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="ab33e-183">Remplacer `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) permet de collecte d’une trace plus petite avec moins de granularité dans les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="ab33e-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="ab33e-184">La commande suivante réduit la surcharge et la taille des traces plus que la précédente :</span><span class="sxs-lookup"><span data-stu-id="ab33e-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="ab33e-185">La commande précédente désactive les événements de temps d’exécution et le profileur de pile géré.</span><span class="sxs-lookup"><span data-stu-id="ab33e-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="ab33e-186">.FOURNISSEURS NET</span><span class="sxs-lookup"><span data-stu-id="ab33e-186">.NET Providers</span></span>

<span data-ttu-id="ab33e-187">Le temps d’exécution .NET Core prend en charge les fournisseurs .NET suivants.</span><span class="sxs-lookup"><span data-stu-id="ab33e-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="ab33e-188">.NET Core utilise les mêmes `Event Tracing for Windows (ETW)` mots `EventPipe` clés pour activer à la fois et des traces.</span><span class="sxs-lookup"><span data-stu-id="ab33e-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="ab33e-189">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="ab33e-189">Provider name</span></span>                            | <span data-ttu-id="ab33e-190">Information</span><span class="sxs-lookup"><span data-stu-id="ab33e-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="ab33e-191">Fournisseur de runtime</span><span class="sxs-lookup"><span data-stu-id="ab33e-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="ab33e-192">Mots-clés CLR Runtime</span><span class="sxs-lookup"><span data-stu-id="ab33e-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="ab33e-193">Fournisseur d’arrêt</span><span class="sxs-lookup"><span data-stu-id="ab33e-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="ab33e-194">Mots-clés CLR Rundown</span><span class="sxs-lookup"><span data-stu-id="ab33e-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="ab33e-195">Permet au profileur d’échantillon.</span><span class="sxs-lookup"><span data-stu-id="ab33e-195">Enables the sample profiler.</span></span> |
