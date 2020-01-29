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
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="9a617-103">utilitaire d’analyse des performances dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="9a617-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9a617-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="9a617-105">Installer dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-105">Install dotnet-trace</span></span>

<span data-ttu-id="9a617-106">Installez `dotnet-trace` [package NuGet](https://www.nuget.org/packages/dotnet-trace) à l’aide de la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="9a617-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="9a617-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a617-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9a617-108">Description</span><span class="sxs-lookup"><span data-stu-id="9a617-108">Description</span></span>

<span data-ttu-id="9a617-109">Outil `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="9a617-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="9a617-110">Est un outil .NET Core multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="9a617-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="9a617-111">Active la collecte des traces .NET Core d’un processus en cours d’exécution sans profileur natif.</span><span class="sxs-lookup"><span data-stu-id="9a617-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="9a617-112">Est conçu autour de la technologie `EventPipe` multiplateforme du Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a617-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="9a617-113">Offre la même expérience sur Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="9a617-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="9a617-114">Options</span><span class="sxs-lookup"><span data-stu-id="9a617-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="9a617-115">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="9a617-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9a617-116">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9a617-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="9a617-117">Commands</span><span class="sxs-lookup"><span data-stu-id="9a617-117">Commands</span></span>

| <span data-ttu-id="9a617-118">Command</span><span class="sxs-lookup"><span data-stu-id="9a617-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="9a617-119">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="9a617-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="9a617-120">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="9a617-121">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="9a617-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="9a617-122">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="9a617-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="9a617-123">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="9a617-123">dotnet-trace collect</span></span>

<span data-ttu-id="9a617-124">Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9a617-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9a617-125">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a617-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="9a617-126">Options</span><span class="sxs-lookup"><span data-stu-id="9a617-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9a617-127">Processus à partir duquel la trace doit être collectée.</span><span class="sxs-lookup"><span data-stu-id="9a617-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="9a617-128">Définit la taille de la mémoire tampon circulaire en mémoire, en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="9a617-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="9a617-129">256 Mo par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a617-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="9a617-130">Chemin de sortie pour les données de trace collectées.</span><span class="sxs-lookup"><span data-stu-id="9a617-130">The output path for the collected trace data.</span></span> <span data-ttu-id="9a617-131">S’il n’est pas spécifié, la valeur par défaut est `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="9a617-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="9a617-132">Liste séparée par des virgules des fournisseurs de `EventPipe` à activer.</span><span class="sxs-lookup"><span data-stu-id="9a617-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="9a617-133">Ces fournisseurs complètent les fournisseurs de `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="9a617-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="9a617-134">S’il existe une incohérence pour un fournisseur particulier, cette configuration est prioritaire par rapport à la configuration implicite à partir du profil.</span><span class="sxs-lookup"><span data-stu-id="9a617-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="9a617-135">Cette liste de fournisseurs se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="9a617-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="9a617-136">`Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="9a617-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="9a617-137">`KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="9a617-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="9a617-138">Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.</span><span class="sxs-lookup"><span data-stu-id="9a617-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="9a617-139">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="9a617-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="9a617-140">La valeur par défaut est `NetTrace`,</span><span class="sxs-lookup"><span data-stu-id="9a617-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="9a617-141">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-141">dotnet-trace convert</span></span>

<span data-ttu-id="9a617-142">Convertit `nettrace` suivis en autres formats pour les utiliser avec d’autres outils d’analyse de trace.</span><span class="sxs-lookup"><span data-stu-id="9a617-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9a617-143">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a617-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="9a617-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a617-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="9a617-145">Fichier de trace d’entrée à convertir.</span><span class="sxs-lookup"><span data-stu-id="9a617-145">Input trace file to be converted.</span></span> <span data-ttu-id="9a617-146">La valeur par défaut est *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="9a617-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="9a617-147">Options</span><span class="sxs-lookup"><span data-stu-id="9a617-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="9a617-148">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="9a617-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="9a617-149">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9a617-149">Output filename.</span></span> <span data-ttu-id="9a617-150">L’extension du format cible sera ajoutée.</span><span class="sxs-lookup"><span data-stu-id="9a617-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="9a617-151">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="9a617-151">dotnet-trace ps</span></span>

<span data-ttu-id="9a617-152">Répertorie les processus dotnet qui peuvent être attachés à.</span><span class="sxs-lookup"><span data-stu-id="9a617-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9a617-153">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a617-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="9a617-154">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="9a617-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="9a617-155">Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.</span><span class="sxs-lookup"><span data-stu-id="9a617-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9a617-156">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a617-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="9a617-157">Collecter une trace avec dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="9a617-158">Pour collecter des traces à l’aide de `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="9a617-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="9a617-159">Obtient l’identificateur de processus (PID) de l’application .NET Core à partir duquel collecter les traces.</span><span class="sxs-lookup"><span data-stu-id="9a617-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="9a617-160">Sur Windows, vous pouvez utiliser le gestionnaire des tâches ou la commande `tasklist`, par exemple.</span><span class="sxs-lookup"><span data-stu-id="9a617-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="9a617-161">Sur Linux, par exemple, la commande `ps`.</span><span class="sxs-lookup"><span data-stu-id="9a617-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="9a617-162">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="9a617-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="9a617-163">Exécutez la commande suivante : .</span><span class="sxs-lookup"><span data-stu-id="9a617-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="9a617-164">La commande précédente génère une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9a617-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="9a617-165">Arrêtez la collecte en appuyant sur la touche `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="9a617-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="9a617-166">`dotnet-trace` terminera la journalisation des événements dans le fichier *trace. NetTrace* .</span><span class="sxs-lookup"><span data-stu-id="9a617-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="9a617-167">Afficher la trace capturée à partir de dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9a617-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="9a617-168">Sur Windows, les fichiers *. NetTrace* peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse : pour les traces collectées sur d’autres plateformes, le fichier de trace peut être déplacé vers un ordinateur Windows à afficher sur PerfView.</span><span class="sxs-lookup"><span data-stu-id="9a617-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="9a617-169">Sur Linux, la trace peut être affichée en modifiant le format de sortie de `dotnet-trace` sur `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9a617-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="9a617-170">Le format du fichier de sortie peut être modifié à l’aide de l’option `-f|--format` `-f speedscope` permet de créer `dotnet-trace` un fichier de `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9a617-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="9a617-171">Vous pouvez choisir entre `nettrace` (option par défaut) et `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9a617-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="9a617-172">`Speedscope` fichiers peuvent être ouverts à <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="9a617-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="9a617-173">Le Runtime .NET Core génère des traces au format `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="9a617-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="9a617-174">Les suivis sont convertis en speedscope (si spécifié) une fois la trace terminée.</span><span class="sxs-lookup"><span data-stu-id="9a617-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="9a617-175">Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier `nettrace` d’origine est conservé en regard du fichier converti.</span><span class="sxs-lookup"><span data-stu-id="9a617-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="9a617-176">Utiliser dotnet-trace pour collecter des valeurs de compteur au fil du temps</span><span class="sxs-lookup"><span data-stu-id="9a617-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="9a617-177">`dotnet-trace` pouvez :</span><span class="sxs-lookup"><span data-stu-id="9a617-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="9a617-178">Utilisez `EventCounter` pour la surveillance de l’intégrité de base dans les environnements sensibles aux performances.</span><span class="sxs-lookup"><span data-stu-id="9a617-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="9a617-179">Par exemple, en production.</span><span class="sxs-lookup"><span data-stu-id="9a617-179">For example, in production.</span></span>
* <span data-ttu-id="9a617-180">Collectez les traces afin qu’elles n’aient pas besoin d’être affichées en temps réel.</span><span class="sxs-lookup"><span data-stu-id="9a617-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="9a617-181">Par exemple, pour collecter les valeurs de compteur de performance du runtime, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9a617-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="9a617-182">La commande précédente indique aux compteurs Runtime de signaler une fois toutes les secondes pour une surveillance de l’intégrité légère.</span><span class="sxs-lookup"><span data-stu-id="9a617-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="9a617-183">Le remplacement d' `EventCounterIntervalSec=1` par une valeur plus élevée (par exemple, 60) permet la collecte d’une trace plus petite avec moins de granularité dans les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="9a617-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="9a617-184">La commande suivante réduit la surcharge et la taille de trace plus grande que la taille précédente :</span><span class="sxs-lookup"><span data-stu-id="9a617-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="9a617-185">La commande précédente désactive les événements d’exécution et le profileur de pile managée.</span><span class="sxs-lookup"><span data-stu-id="9a617-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="9a617-186">Fournisseurs .NET</span><span class="sxs-lookup"><span data-stu-id="9a617-186">.NET Providers</span></span>

<span data-ttu-id="9a617-187">Le Runtime .NET Core prend en charge les fournisseurs .NET suivants.</span><span class="sxs-lookup"><span data-stu-id="9a617-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="9a617-188">.NET Core utilise les mêmes mots clés pour activer les suivis `Event Tracing for Windows (ETW)` et `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="9a617-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="9a617-189">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="9a617-189">Provider name</span></span>                            | <span data-ttu-id="9a617-190">Informations</span><span class="sxs-lookup"><span data-stu-id="9a617-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="9a617-191">Fournisseur du Runtime</span><span class="sxs-lookup"><span data-stu-id="9a617-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="9a617-192">Mots clés du runtime CLR</span><span class="sxs-lookup"><span data-stu-id="9a617-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="9a617-193">Fournisseur d’arrêt</span><span class="sxs-lookup"><span data-stu-id="9a617-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="9a617-194">Mots clés d’arrêt du CLR</span><span class="sxs-lookup"><span data-stu-id="9a617-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="9a617-195">Active l’exemple de profileur.</span><span class="sxs-lookup"><span data-stu-id="9a617-195">Enables the sample profiler.</span></span> |
