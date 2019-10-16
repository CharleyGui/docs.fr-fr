---
title: dotnet-Counters-.NET Core
description: Découvrez comment installer et utiliser l’outil en ligne de commande dotnet-Counter.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321588"
---
# <a name="dotnet-counters"></a><span data-ttu-id="07bd7-103">dotnet-compteurs</span><span class="sxs-lookup"><span data-stu-id="07bd7-103">dotnet-counters</span></span>

<span data-ttu-id="07bd7-104">**Cet article s’applique à : ✓** .net Core 3,0 SDK et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="07bd7-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="07bd7-105">Installer dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="07bd7-105">Install dotnet-counters</span></span>

<span data-ttu-id="07bd7-106">Pour installer la dernière version Release du [package NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="07bd7-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="07bd7-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="07bd7-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="07bd7-108">Description</span><span class="sxs-lookup"><span data-stu-id="07bd7-108">Description</span></span>

<span data-ttu-id="07bd7-109">`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="07bd7-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="07bd7-110">Il peut observer les valeurs des compteurs de performance publiées via l’API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="07bd7-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="07bd7-111">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide de `PerfView` ou `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="07bd7-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="07bd7-112">Options</span><span class="sxs-lookup"><span data-stu-id="07bd7-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="07bd7-113">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="07bd7-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="07bd7-114">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="07bd7-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="07bd7-115">Commandes</span><span class="sxs-lookup"><span data-stu-id="07bd7-115">Commands</span></span>

| <span data-ttu-id="07bd7-116">Commande</span><span class="sxs-lookup"><span data-stu-id="07bd7-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="07bd7-117">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="07bd7-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="07bd7-118">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="07bd7-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="07bd7-119">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="07bd7-119">dotnet-counters list</span></span>

<span data-ttu-id="07bd7-120">Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="07bd7-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="07bd7-121">Résumé</span><span class="sxs-lookup"><span data-stu-id="07bd7-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="07bd7-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="07bd7-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="07bd7-123">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="07bd7-123">dotnet-counters monitor</span></span>

<span data-ttu-id="07bd7-124">Affiche régulièrement les valeurs des compteurs sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="07bd7-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="07bd7-125">Résumé</span><span class="sxs-lookup"><span data-stu-id="07bd7-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="07bd7-126">Options</span><span class="sxs-lookup"><span data-stu-id="07bd7-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="07bd7-127">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="07bd7-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="07bd7-128">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="07bd7-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="07bd7-129">Liste séparée par des espaces des compteurs.</span><span class="sxs-lookup"><span data-stu-id="07bd7-129">A space separated list of counters.</span></span> <span data-ttu-id="07bd7-130">Les compteurs peuvent être spécifiés `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="07bd7-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="07bd7-131">Si le `provider_name` est utilisé sans `counter_name` éligible, tous les compteurs sont affichés.</span><span class="sxs-lookup"><span data-stu-id="07bd7-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="07bd7-132">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="07bd7-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="07bd7-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="07bd7-133">Examples</span></span>

- <span data-ttu-id="07bd7-134">Surveillez tous les compteurs de `System.Runtime` à un intervalle d’actualisation de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="07bd7-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="07bd7-135">Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="07bd7-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="07bd7-136">Analyser les valeurs `EventCounter` à partir des `EventSource` définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07bd7-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="07bd7-137">Pour plus d’informations, consultez [Didacticiel : Comment mesurer les performances pour les événements très fréquents à l’aide de EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="07bd7-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
