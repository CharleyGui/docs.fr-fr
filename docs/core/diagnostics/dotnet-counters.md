---
title: dotnet-Counters-.NET Core
description: Découvrez comment installer et utiliser l’outil en ligne de commande dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 6a4fd92540dbc16173dfa3a10ff9dfaa1f31f7d0
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062897"
---
# <a name="dotnet-counters"></a><span data-ttu-id="dbf41-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-103">dotnet-counters</span></span>

<span data-ttu-id="dbf41-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="dbf41-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="dbf41-105">Installer dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-105">Install dotnet-counters</span></span>

<span data-ttu-id="dbf41-106">Pour installer la dernière version Release du `dotnet-counters` [package NuGet](https://www.nuget.org/packages/dotnet-counters), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="dbf41-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="dbf41-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dbf41-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="dbf41-108">Description</span><span class="sxs-lookup"><span data-stu-id="dbf41-108">Description</span></span>

<span data-ttu-id="dbf41-109">`dotnet-counters`est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="dbf41-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="dbf41-110">Il peut observer les valeurs des compteurs de performance publiées via l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="dbf41-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="dbf41-111">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide `PerfView` de ou de `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="dbf41-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="dbf41-112">Options</span><span class="sxs-lookup"><span data-stu-id="dbf41-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="dbf41-113">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="dbf41-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="dbf41-114">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dbf41-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="dbf41-115">Commandes</span><span class="sxs-lookup"><span data-stu-id="dbf41-115">Commands</span></span>

| <span data-ttu-id="dbf41-116">Commande</span><span class="sxs-lookup"><span data-stu-id="dbf41-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="dbf41-117">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="dbf41-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="dbf41-118">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="dbf41-119">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="dbf41-120">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="dbf41-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="dbf41-121">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="dbf41-121">dotnet-counters collect</span></span>

<span data-ttu-id="dbf41-122">Collectez périodiquement les valeurs de compteur sélectionnées et exportez-les dans un format de fichier spécifié pour le retraitement.</span><span class="sxs-lookup"><span data-stu-id="dbf41-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dbf41-123">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dbf41-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="dbf41-124">Options</span><span class="sxs-lookup"><span data-stu-id="dbf41-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="dbf41-125">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="dbf41-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="dbf41-126">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="dbf41-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="dbf41-127">Liste séparée par des espaces des compteurs.</span><span class="sxs-lookup"><span data-stu-id="dbf41-127">A space separated list of counters.</span></span> <span data-ttu-id="dbf41-128">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="dbf41-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="dbf41-129">Si le `provider_name` est utilisé sans qualification `counter_name` , tous les compteurs sont affichés.</span><span class="sxs-lookup"><span data-stu-id="dbf41-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="dbf41-130">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="dbf41-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="dbf41-131">Format à exporter.</span><span class="sxs-lookup"><span data-stu-id="dbf41-131">The format to be exported.</span></span> <span data-ttu-id="dbf41-132">Actuellement disponible : CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="dbf41-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="dbf41-133">Le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="dbf41-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="dbf41-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="dbf41-134">Examples</span></span>

- <span data-ttu-id="dbf41-135">Collecter tous les compteurs à un intervalle d’actualisation de 3 secondes et générer un CSV en tant que sortie :</span><span class="sxs-lookup"><span data-stu-id="dbf41-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="dbf41-136">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-136">dotnet-counters list</span></span>

<span data-ttu-id="dbf41-137">Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="dbf41-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dbf41-138">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dbf41-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="dbf41-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbf41-139">Example</span></span>

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
> <span data-ttu-id="dbf41-140">Les `Microsoft.AspNetCore.Hosting` compteurs s’affichent lorsque des processus identifiés prennent en charge ces compteurs, par exemple, quand une application ASP.net Core s’exécute sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="dbf41-140">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="dbf41-141">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="dbf41-141">dotnet-counters monitor</span></span>

<span data-ttu-id="dbf41-142">Affiche régulièrement les valeurs des compteurs sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="dbf41-142">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dbf41-143">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dbf41-143">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="dbf41-144">Options</span><span class="sxs-lookup"><span data-stu-id="dbf41-144">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="dbf41-145">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="dbf41-145">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="dbf41-146">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="dbf41-146">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="dbf41-147">Liste séparée par des espaces des compteurs.</span><span class="sxs-lookup"><span data-stu-id="dbf41-147">A space separated list of counters.</span></span> <span data-ttu-id="dbf41-148">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="dbf41-148">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="dbf41-149">Si le `provider_name` est utilisé sans qualification `counter_name` , tous les compteurs sont affichés.</span><span class="sxs-lookup"><span data-stu-id="dbf41-149">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="dbf41-150">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="dbf41-150">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="dbf41-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="dbf41-151">Examples</span></span>

- <span data-ttu-id="dbf41-152">Surveiller tous les compteurs à partir d' `System.Runtime` un intervalle d’actualisation de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="dbf41-152">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="dbf41-153">Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="dbf41-153">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="dbf41-154">Surveiller `EventCounter` les valeurs de définies par l’utilisateur `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="dbf41-154">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="dbf41-155">Pour plus d’informations, consultez [Didacticiel : mesurer les performances à l’aide de EventCounters dans .net Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="dbf41-155">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="dbf41-156">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="dbf41-156">dotnet-counters ps</span></span>

<span data-ttu-id="dbf41-157">Affiche la liste des processus dotnet qui peuvent être analysés.</span><span class="sxs-lookup"><span data-stu-id="dbf41-157">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dbf41-158">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dbf41-158">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="dbf41-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbf41-159">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
