---
title: outil de diagnostic dotnet-Counters-.NET CLI
description: Découvrez comment installer et utiliser l’outil CLI dotnet-Counter pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.
ms.date: 11/17/2020
ms.openlocfilehash: 9787b4a78c5b49b839232c0bb5ffbd87d9f95556
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593433"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="394d9-103">Examiner les compteurs de performance (dotnet-Counters)</span><span class="sxs-lookup"><span data-stu-id="394d9-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="394d9-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="394d9-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="394d9-105">Installer</span><span class="sxs-lookup"><span data-stu-id="394d9-105">Install</span></span>

<span data-ttu-id="394d9-106">Il existe deux façons de télécharger et d’installer `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="394d9-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="394d9-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="394d9-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="394d9-108">Pour installer la dernière version Release du `dotnet-counters` [package NuGet](https://www.nuget.org/packages/dotnet-counters), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="394d9-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="394d9-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="394d9-109">**Direct download:**</span></span>

  <span data-ttu-id="394d9-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="394d9-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="394d9-111">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="394d9-111">OS</span></span>  | <span data-ttu-id="394d9-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="394d9-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="394d9-113">Windows</span><span class="sxs-lookup"><span data-stu-id="394d9-113">Windows</span></span> | <span data-ttu-id="394d9-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="394d9-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="394d9-115">macOS</span><span class="sxs-lookup"><span data-stu-id="394d9-115">macOS</span></span>   | [<span data-ttu-id="394d9-116">x64</span><span class="sxs-lookup"><span data-stu-id="394d9-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="394d9-117">Linux</span><span class="sxs-lookup"><span data-stu-id="394d9-117">Linux</span></span>   | <span data-ttu-id="394d9-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="394d9-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="394d9-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="394d9-119">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="394d9-120">Description</span><span class="sxs-lookup"><span data-stu-id="394d9-120">Description</span></span>

<span data-ttu-id="394d9-121">`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="394d9-121">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="394d9-122">Il peut observer les valeurs des compteurs de performance publiées via l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="394d9-122">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="394d9-123">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide `PerfView` de ou de `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="394d9-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="394d9-124">Options</span><span class="sxs-lookup"><span data-stu-id="394d9-124">Options</span></span>

- **`--version`**

  <span data-ttu-id="394d9-125">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="394d9-125">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="394d9-126">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="394d9-126">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="394d9-127">Commandes</span><span class="sxs-lookup"><span data-stu-id="394d9-127">Commands</span></span>

| <span data-ttu-id="394d9-128">Commande</span><span class="sxs-lookup"><span data-stu-id="394d9-128">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="394d9-129">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="394d9-129">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="394d9-130">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="394d9-130">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="394d9-131">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="394d9-131">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="394d9-132">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="394d9-132">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="394d9-133">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="394d9-133">dotnet-counters collect</span></span>

<span data-ttu-id="394d9-134">Collectez périodiquement les valeurs de compteur sélectionnées et exportez-les dans un format de fichier spécifié pour le retraitement.</span><span class="sxs-lookup"><span data-stu-id="394d9-134">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="394d9-135">Synopsis</span><span class="sxs-lookup"><span data-stu-id="394d9-135">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="394d9-136">Options</span><span class="sxs-lookup"><span data-stu-id="394d9-136">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="394d9-137">ID du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="394d9-137">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="394d9-138">Nom du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="394d9-138">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="394d9-139">Nom du port de diagnostic à créer.</span><span class="sxs-lookup"><span data-stu-id="394d9-139">The name of the diagnostic port to create.</span></span> <span data-ttu-id="394d9-140">Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="394d9-140">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="394d9-141">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="394d9-141">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="394d9-142">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="394d9-142">A comma-separated list of counters.</span></span> <span data-ttu-id="394d9-143">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="394d9-143">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="394d9-144">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="394d9-144">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="394d9-145">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="394d9-145">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="394d9-146">Format à exporter.</span><span class="sxs-lookup"><span data-stu-id="394d9-146">The format to be exported.</span></span> <span data-ttu-id="394d9-147">Actuellement disponible : CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="394d9-147">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="394d9-148">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="394d9-148">The name of the output file.</span></span>

- <span data-ttu-id="394d9-149">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="394d9-149">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="394d9-150">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="394d9-150">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="394d9-151">`dotnet-counters` lance un processus avec la commande fournie et collecte les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="394d9-151">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="394d9-152">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="394d9-152">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="394d9-153">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="394d9-153">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="394d9-154">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="394d9-154">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="394d9-155">Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="394d9-155">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="394d9-156">La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="394d9-156">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="394d9-157">Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="394d9-157">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="394d9-158">Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="394d9-158">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="394d9-159">Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="394d9-159">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="394d9-160">Exemples</span><span class="sxs-lookup"><span data-stu-id="394d9-160">Examples</span></span>

- <span data-ttu-id="394d9-161">Collecter tous les compteurs à un intervalle d’actualisation de 3 secondes et générer un CSV en tant que sortie :</span><span class="sxs-lookup"><span data-stu-id="394d9-161">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="394d9-162">Démarrez `dotnet mvc.dll` en tant que processus enfant et commencez à collecter des compteurs Runtime et ASP.net Core des compteurs d’hébergement à partir du démarrage, puis enregistrez-le en tant que sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="394d9-162">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="394d9-163">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="394d9-163">dotnet-counters list</span></span>

<span data-ttu-id="394d9-164">Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="394d9-164">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="394d9-165">Synopsis</span><span class="sxs-lookup"><span data-stu-id="394d9-165">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="394d9-166">Exemple</span><span class="sxs-lookup"><span data-stu-id="394d9-166">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
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
> <span data-ttu-id="394d9-167">Les `Microsoft.AspNetCore.Hosting` compteurs s’affichent lorsque des processus identifiés prennent en charge ces compteurs, par exemple, quand une application ASP.net Core s’exécute sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="394d9-167">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="394d9-168">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="394d9-168">dotnet-counters monitor</span></span>

<span data-ttu-id="394d9-169">Affiche régulièrement les valeurs des compteurs sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="394d9-169">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="394d9-170">Synopsis</span><span class="sxs-lookup"><span data-stu-id="394d9-170">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="394d9-171">Options</span><span class="sxs-lookup"><span data-stu-id="394d9-171">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="394d9-172">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="394d9-172">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="394d9-173">Nom du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="394d9-173">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="394d9-174">Nom du port de diagnostic à créer.</span><span class="sxs-lookup"><span data-stu-id="394d9-174">The name of the diagnostic port to create.</span></span> <span data-ttu-id="394d9-175">Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="394d9-175">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="394d9-176">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="394d9-176">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="394d9-177">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="394d9-177">A comma-separated list of counters.</span></span> <span data-ttu-id="394d9-178">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="394d9-178">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="394d9-179">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="394d9-179">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="394d9-180">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="394d9-180">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="394d9-181">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="394d9-181">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="394d9-182">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="394d9-182">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="394d9-183">`dotnet-counters` lance un processus avec la commande fournie et surveille les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="394d9-183">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="394d9-184">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="394d9-184">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="394d9-185">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="394d9-185">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="394d9-186">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="394d9-186">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="394d9-187">Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="394d9-187">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="394d9-188">La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="394d9-188">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="394d9-189">Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="394d9-189">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="394d9-190">Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="394d9-190">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="394d9-191">Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="394d9-191">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="394d9-192">Exemples</span><span class="sxs-lookup"><span data-stu-id="394d9-192">Examples</span></span>

- <span data-ttu-id="394d9-193">Surveiller tous les compteurs à partir d' `System.Runtime` un intervalle d’actualisation de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="394d9-193">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="394d9-194">Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="394d9-194">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="394d9-195">Surveiller `EventCounter` les valeurs de définies par l’utilisateur `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="394d9-195">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="394d9-196">Pour plus d’informations, consultez [Didacticiel : mesurer les performances à l’aide de EventCounters dans .net Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="394d9-196">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="394d9-197">Lancer `my-aspnet-server.exe` et surveiller le nombre d’assemblys chargés à partir de leur démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="394d9-197">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="394d9-198">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="394d9-198">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="394d9-199">Lancer `my-aspnet-server.exe` avec `arg1` et `arg2` en tant qu’arguments de ligne de commande et surveiller sa plage de travail et sa taille de tas GC depuis son démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="394d9-199">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="394d9-200">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="394d9-200">This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="394d9-201">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="394d9-201">dotnet-counters ps</span></span>

<span data-ttu-id="394d9-202">Affiche la liste des processus dotnet qui peuvent être analysés.</span><span class="sxs-lookup"><span data-stu-id="394d9-202">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="394d9-203">Synopsis</span><span class="sxs-lookup"><span data-stu-id="394d9-203">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="394d9-204">Exemple</span><span class="sxs-lookup"><span data-stu-id="394d9-204">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="394d9-205">Utilisation du port de diagnostic</span><span class="sxs-lookup"><span data-stu-id="394d9-205">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="394d9-206">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="394d9-206">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="394d9-207">Le port de diagnostic est une nouvelle fonctionnalité d’exécution qui a été ajoutée dans .NET 5, qui vous permet de démarrer l’analyse ou la collecte des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="394d9-207">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="394d9-208">Pour ce faire à l’aide de `dotnet-counters` , vous pouvez utiliser `dotnet-counters <collect|monitor> -- <command>` comme décrit dans les exemples ci-dessus ou utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="394d9-208">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="394d9-209">L’utilisation `dotnet-counters <collect|monitor> -- <command>` de pour lancer l’application en tant que processus enfant est le moyen le plus simple de l’analyser rapidement à partir de son démarrage.</span><span class="sxs-lookup"><span data-stu-id="394d9-209">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="394d9-210">Toutefois, lorsque vous souhaitez mieux contrôler la durée de vie de l’application surveillée (par exemple, surveiller l’application pendant les 10 premières minutes uniquement et continuer l’exécution) ou si vous devez interagir avec l’application à l’aide de l’interface CLI, l’utilisation `--diagnostic-port` de l’option vous permet de contrôler à la fois l’application cible en cours d’analyse et `dotnet-counters` .</span><span class="sxs-lookup"><span data-stu-id="394d9-210">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="394d9-211">La commande suivante permet aux compteurs dotnet de créer un socket de diagnostic nommé `myport.sock` et d’attendre une connexion.</span><span class="sxs-lookup"><span data-stu-id="394d9-211">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="394d9-212">Sortie :</span><span class="sxs-lookup"><span data-stu-id="394d9-212">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="394d9-213">Dans une console distincte, lancez l’application cible avec la variable d’environnement `DOTNET_DiagnosticPorts` définie sur la valeur dans la `dotnet-counters` sortie.</span><span class="sxs-lookup"><span data-stu-id="394d9-213">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="394d9-214">Cela doit ensuite permettre `dotnet-counters` de démarrer la collecte des compteurs sur `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="394d9-214">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="394d9-215">Le lancement de votre application avec `dotnet run` peut être problématique, car l’interface CLI dotnet peut générer de nombreux processus enfants qui ne sont pas votre application et qui peuvent se connecter à `dotnet-counters` avant votre application, en laissant votre application interrompue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="394d9-215">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="394d9-216">Nous vous recommandons d’utiliser directement une version autonome de l’application ou `dotnet exec` d’utiliser pour lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="394d9-216">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
