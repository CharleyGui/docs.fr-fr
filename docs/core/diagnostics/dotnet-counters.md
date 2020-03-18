---
title: dotnet-compteurs - .NET Core
description: Apprenez à installer et à utiliser l’outil de ligne de commande dotnet-counter.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147176"
---
# <a name="dotnet-counters"></a><span data-ttu-id="3c1bb-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="3c1bb-103">dotnet-counters</span></span>

<span data-ttu-id="3c1bb-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3c1bb-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="3c1bb-105">Installer des compteurs dotnet</span><span class="sxs-lookup"><span data-stu-id="3c1bb-105">Install dotnet-counters</span></span>

<span data-ttu-id="3c1bb-106">Pour installer la dernière `dotnet-counters` version du [paquet NuGet,](https://www.nuget.org/packages/dotnet-counters)utilisez la commande [d’installation d’outils dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="3c1bb-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="3c1bb-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3c1bb-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="3c1bb-108">Description</span><span class="sxs-lookup"><span data-stu-id="3c1bb-108">Description</span></span>

<span data-ttu-id="3c1bb-109">`dotnet-counters`est un outil de surveillance du rendement pour la surveillance de la santé ad hoc et l’enquête de premier niveau sur le rendement.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="3c1bb-110">Il peut observer les valeurs de <xref:System.Diagnostics.Tracing.EventCounter> compteur de performance qui sont publiées via l’API.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="3c1bb-111">Par exemple, vous pouvez surveiller rapidement des choses comme l’utilisation du processeur ou le taux d’exceptions jetées dans `PerfView` votre `dotnet-trace`application .NET Core pour voir s’il ya quelque chose de suspect avant de plonger dans une enquête de performance plus grave en utilisant ou .</span><span class="sxs-lookup"><span data-stu-id="3c1bb-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="3c1bb-112">Options</span><span class="sxs-lookup"><span data-stu-id="3c1bb-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="3c1bb-113">Affiche la version de l’utilitaire dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3c1bb-114">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="3c1bb-115">Commandes</span><span class="sxs-lookup"><span data-stu-id="3c1bb-115">Commands</span></span>

| <span data-ttu-id="3c1bb-116">Commande</span><span class="sxs-lookup"><span data-stu-id="3c1bb-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="3c1bb-117">dotnet-compteurs recueillir</span><span class="sxs-lookup"><span data-stu-id="3c1bb-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="3c1bb-118">liste de compteurs dotnet</span><span class="sxs-lookup"><span data-stu-id="3c1bb-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="3c1bb-119">moniteur dotnet-compteurs</span><span class="sxs-lookup"><span data-stu-id="3c1bb-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="3c1bb-120">dotnet-compteurs ps</span><span class="sxs-lookup"><span data-stu-id="3c1bb-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="3c1bb-121">dotnet-compteurs recueillir</span><span class="sxs-lookup"><span data-stu-id="3c1bb-121">dotnet-counters collect</span></span>

<span data-ttu-id="3c1bb-122">Recueillir périodiquement des valeurs de compteur sélectionnées et les exporter dans un format de fichier spécifié pour le post-traitement.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3c1bb-123">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3c1bb-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="3c1bb-124">Options</span><span class="sxs-lookup"><span data-stu-id="3c1bb-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="3c1bb-125">L’ID du processus à surveiller.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="3c1bb-126">Le nombre de secondes à retarder entre la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="3c1bb-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="3c1bb-127">Un espace séparé liste de compteurs.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-127">A space separated list of counters.</span></span> <span data-ttu-id="3c1bb-128">Les compteurs `provider_name[:counter_name]`peuvent être spécifiés .</span><span class="sxs-lookup"><span data-stu-id="3c1bb-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="3c1bb-129">Si `provider_name` le est utilisé `counter_name`sans qualification, alors tous les compteurs sont affichés.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="3c1bb-130">Pour découvrir les noms des fournisseurs et des comptoirs, utilisez la commande [de liste de compteurs pointnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="3c1bb-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="3c1bb-131">TLe format à exporter.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-131">TThe format to be exported.</span></span> <span data-ttu-id="3c1bb-132">Actuellement disponible: csv, json.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="3c1bb-133">Le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="3c1bb-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="3c1bb-134">Examples</span></span>

- <span data-ttu-id="3c1bb-135">Recueillir tous les compteurs à un intervalle de rafraîchissement de 3 secondes et de générer un csv comme sortie:</span><span class="sxs-lookup"><span data-stu-id="3c1bb-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="3c1bb-136">liste de compteurs dotnet</span><span class="sxs-lookup"><span data-stu-id="3c1bb-136">dotnet-counters list</span></span>

<span data-ttu-id="3c1bb-137">Affiche une liste de noms et de descriptions de compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3c1bb-138">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3c1bb-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="3c1bb-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3c1bb-139">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="3c1bb-140">moniteur dotnet-compteurs</span><span class="sxs-lookup"><span data-stu-id="3c1bb-140">dotnet-counters monitor</span></span>

<span data-ttu-id="3c1bb-141">Affiche des valeurs périodiquement rafraîchissantes de certains compteurs.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3c1bb-142">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3c1bb-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="3c1bb-143">Options</span><span class="sxs-lookup"><span data-stu-id="3c1bb-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="3c1bb-144">L’ID du processus à surveiller.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="3c1bb-145">Le nombre de secondes à retarder entre la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="3c1bb-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="3c1bb-146">Un espace séparé liste de compteurs.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-146">A space separated list of counters.</span></span> <span data-ttu-id="3c1bb-147">Les compteurs `provider_name[:counter_name]`peuvent être spécifiés .</span><span class="sxs-lookup"><span data-stu-id="3c1bb-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="3c1bb-148">Si `provider_name` le est utilisé `counter_name`sans qualification, alors tous les compteurs sont affichés.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="3c1bb-149">Pour découvrir les noms des fournisseurs et des comptoirs, utilisez la commande [de liste de compteurs pointnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="3c1bb-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="3c1bb-150">Exemples</span><span class="sxs-lookup"><span data-stu-id="3c1bb-150">Examples</span></span>

- <span data-ttu-id="3c1bb-151">Surveillez tous `System.Runtime` les compteurs à partir d’un intervalle de rafraîchissement de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="3c1bb-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="3c1bb-152">Surveiller juste l’utilisation de processeur `System.Runtime`et la taille de tas de GC de :</span><span class="sxs-lookup"><span data-stu-id="3c1bb-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="3c1bb-153">Surveiller `EventCounter` les valeurs `EventSource`de l’utilisateur défini .</span><span class="sxs-lookup"><span data-stu-id="3c1bb-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="3c1bb-154">Pour plus d’informations, voir [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="3c1bb-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="3c1bb-155">dotnet-compteurs ps</span><span class="sxs-lookup"><span data-stu-id="3c1bb-155">dotnet-counters ps</span></span>

<span data-ttu-id="3c1bb-156">Affichez une liste de processus dotnet qui peuvent être surveillés.</span><span class="sxs-lookup"><span data-stu-id="3c1bb-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3c1bb-157">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3c1bb-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="3c1bb-158"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3c1bb-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
