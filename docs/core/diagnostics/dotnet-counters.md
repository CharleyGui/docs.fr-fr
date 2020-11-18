---
title: outil de diagnostic dotnet-Counters-.NET CLI
description: Découvrez comment installer et utiliser l’outil CLI dotnet-Counter pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.
ms.date: 11/17/2020
ms.openlocfilehash: 7dd4c06f3abe423552ba1d3eb82f6d0c35a84d0b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822215"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="26c4e-103">Examiner les compteurs de performance (dotnet-Counters)</span><span class="sxs-lookup"><span data-stu-id="26c4e-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="26c4e-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="26c4e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="26c4e-105">Installer</span><span class="sxs-lookup"><span data-stu-id="26c4e-105">Install</span></span>

<span data-ttu-id="26c4e-106">Il existe deux façons de télécharger et d’installer `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="26c4e-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="26c4e-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="26c4e-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="26c4e-108">Pour installer la dernière version Release du `dotnet-counters` [package NuGet](https://www.nuget.org/packages/dotnet-counters), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="26c4e-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="26c4e-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="26c4e-109">**Direct download:**</span></span>

  <span data-ttu-id="26c4e-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="26c4e-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="26c4e-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="26c4e-111">OS</span></span>  | <span data-ttu-id="26c4e-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="26c4e-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="26c4e-113">Windows</span><span class="sxs-lookup"><span data-stu-id="26c4e-113">Windows</span></span> | <span data-ttu-id="26c4e-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="26c4e-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="26c4e-115">macOS</span><span class="sxs-lookup"><span data-stu-id="26c4e-115">macOS</span></span>   | [<span data-ttu-id="26c4e-116">x64</span><span class="sxs-lookup"><span data-stu-id="26c4e-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="26c4e-117">Linux</span><span class="sxs-lookup"><span data-stu-id="26c4e-117">Linux</span></span>   | <span data-ttu-id="26c4e-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="26c4e-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="26c4e-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="26c4e-119">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="26c4e-120">Description</span><span class="sxs-lookup"><span data-stu-id="26c4e-120">Description</span></span>

<span data-ttu-id="26c4e-121">`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="26c4e-121">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="26c4e-122">Il peut observer les valeurs des compteurs de performance publiées via l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="26c4e-122">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="26c4e-123">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide `PerfView` de ou de `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="26c4e-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="26c4e-124">Options</span><span class="sxs-lookup"><span data-stu-id="26c4e-124">Options</span></span>

- **`--version`**

  <span data-ttu-id="26c4e-125">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="26c4e-125">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="26c4e-126">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="26c4e-126">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="26c4e-127">Commandes</span><span class="sxs-lookup"><span data-stu-id="26c4e-127">Commands</span></span>

| <span data-ttu-id="26c4e-128">Commande</span><span class="sxs-lookup"><span data-stu-id="26c4e-128">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="26c4e-129">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="26c4e-129">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="26c4e-130">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="26c4e-130">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="26c4e-131">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="26c4e-131">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="26c4e-132">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="26c4e-132">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="26c4e-133">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="26c4e-133">dotnet-counters collect</span></span>

<span data-ttu-id="26c4e-134">Collectez périodiquement les valeurs de compteur sélectionnées et exportez-les dans un format de fichier spécifié pour le retraitement.</span><span class="sxs-lookup"><span data-stu-id="26c4e-134">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="26c4e-135">Synopsis</span><span class="sxs-lookup"><span data-stu-id="26c4e-135">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="26c4e-136">Options</span><span class="sxs-lookup"><span data-stu-id="26c4e-136">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="26c4e-137">ID du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="26c4e-137">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="26c4e-138">Nom du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="26c4e-138">The name of the process to be collect counter data from.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="26c4e-139">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="26c4e-139">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="26c4e-140">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="26c4e-140">A comma-separated list of counters.</span></span> <span data-ttu-id="26c4e-141">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="26c4e-141">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="26c4e-142">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="26c4e-142">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="26c4e-143">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="26c4e-143">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="26c4e-144">Format à exporter.</span><span class="sxs-lookup"><span data-stu-id="26c4e-144">The format to be exported.</span></span> <span data-ttu-id="26c4e-145">Actuellement disponible : CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="26c4e-145">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="26c4e-146">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="26c4e-146">The name of the output file.</span></span>

- <span data-ttu-id="26c4e-147">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="26c4e-147">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="26c4e-148">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="26c4e-148">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="26c4e-149">`dotnet-counters` lance un processus avec la commande fournie et collecte les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="26c4e-149">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="26c4e-150">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="26c4e-150">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="26c4e-151">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="26c4e-151">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="26c4e-152">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="26c4e-152">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="26c4e-153">Exemples</span><span class="sxs-lookup"><span data-stu-id="26c4e-153">Examples</span></span>

- <span data-ttu-id="26c4e-154">Collecter tous les compteurs à un intervalle d’actualisation de 3 secondes et générer un CSV en tant que sortie :</span><span class="sxs-lookup"><span data-stu-id="26c4e-154">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="26c4e-155">Démarrez `dotnet mvc.dll` en tant que processus enfant et commencez à collecter des compteurs Runtime et ASP.net Core des compteurs d’hébergement à partir du démarrage, puis enregistrez-le en tant que sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="26c4e-155">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="26c4e-156">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="26c4e-156">dotnet-counters list</span></span>

<span data-ttu-id="26c4e-157">Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="26c4e-157">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="26c4e-158">Synopsis</span><span class="sxs-lookup"><span data-stu-id="26c4e-158">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="26c4e-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="26c4e-159">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="26c4e-160">Les `Microsoft.AspNetCore.Hosting` compteurs s’affichent lorsque des processus identifiés prennent en charge ces compteurs, par exemple, quand une application ASP.net Core s’exécute sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="26c4e-160">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="26c4e-161">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="26c4e-161">dotnet-counters monitor</span></span>

<span data-ttu-id="26c4e-162">Affiche régulièrement les valeurs des compteurs sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="26c4e-162">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="26c4e-163">Synopsis</span><span class="sxs-lookup"><span data-stu-id="26c4e-163">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="26c4e-164">Options</span><span class="sxs-lookup"><span data-stu-id="26c4e-164">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="26c4e-165">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="26c4e-165">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="26c4e-166">Nom du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="26c4e-166">The name of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="26c4e-167">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="26c4e-167">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="26c4e-168">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="26c4e-168">A comma-separated list of counters.</span></span> <span data-ttu-id="26c4e-169">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="26c4e-169">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="26c4e-170">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="26c4e-170">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="26c4e-171">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="26c4e-171">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="26c4e-172">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="26c4e-172">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="26c4e-173">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="26c4e-173">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="26c4e-174">`dotnet-counters` lance un processus avec la commande fournie et surveille les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="26c4e-174">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="26c4e-175">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="26c4e-175">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="26c4e-176">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="26c4e-176">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="26c4e-177">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="26c4e-177">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="26c4e-178">Exemples</span><span class="sxs-lookup"><span data-stu-id="26c4e-178">Examples</span></span>

- <span data-ttu-id="26c4e-179">Surveiller tous les compteurs à partir d' `System.Runtime` un intervalle d’actualisation de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="26c4e-179">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="26c4e-180">Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="26c4e-180">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="26c4e-181">Surveiller `EventCounter` les valeurs de définies par l’utilisateur `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="26c4e-181">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="26c4e-182">Pour plus d’informations, consultez [Didacticiel : mesurer les performances à l’aide de EventCounters dans .net Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="26c4e-182">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="26c4e-183">Lancer `my-aspnet-server.exe` et surveiller le nombre d’assemblys chargés à partir de leur démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="26c4e-183">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="26c4e-184">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="26c4e-184">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="26c4e-185">Lancer `my-aspnet-server.exe` avec `arg1` et `arg2` en tant qu’arguments de ligne de commande et surveiller sa plage de travail et sa taille de tas GC depuis son démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="26c4e-185">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="26c4e-186">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="26c4e-186">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="26c4e-187">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="26c4e-187">dotnet-counters ps</span></span>

<span data-ttu-id="26c4e-188">Affiche la liste des processus dotnet qui peuvent être analysés.</span><span class="sxs-lookup"><span data-stu-id="26c4e-188">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="26c4e-189">Synopsis</span><span class="sxs-lookup"><span data-stu-id="26c4e-189">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="26c4e-190">Exemple</span><span class="sxs-lookup"><span data-stu-id="26c4e-190">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
