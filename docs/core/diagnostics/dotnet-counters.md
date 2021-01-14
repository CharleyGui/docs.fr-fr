---
title: outil de diagnostic dotnet-Counters-.NET CLI
description: Découvrez comment installer et utiliser l’outil CLI dotnet-Counter pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.
ms.date: 11/17/2020
ms.openlocfilehash: 1842b1fb9cde0e0b7a570456766cbfdeb64c5896
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188580"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="9fcc7-103">Examiner les compteurs de performance (dotnet-Counters)</span><span class="sxs-lookup"><span data-stu-id="9fcc7-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="9fcc7-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9fcc7-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="9fcc7-105">Installer</span><span class="sxs-lookup"><span data-stu-id="9fcc7-105">Install</span></span>

<span data-ttu-id="9fcc7-106">Il existe deux façons de télécharger et d’installer `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="9fcc7-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="9fcc7-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="9fcc7-108">Pour installer la dernière version Release du `dotnet-counters` [package NuGet](https://www.nuget.org/packages/dotnet-counters), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="9fcc7-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="9fcc7-109">**Direct download:**</span></span>

  <span data-ttu-id="9fcc7-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="9fcc7-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="9fcc7-111">OS</span></span>  | <span data-ttu-id="9fcc7-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="9fcc7-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="9fcc7-113">Windows</span><span class="sxs-lookup"><span data-stu-id="9fcc7-113">Windows</span></span> | <span data-ttu-id="9fcc7-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="9fcc7-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="9fcc7-115">macOS</span><span class="sxs-lookup"><span data-stu-id="9fcc7-115">macOS</span></span>   | [<span data-ttu-id="9fcc7-116">x64</span><span class="sxs-lookup"><span data-stu-id="9fcc7-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="9fcc7-117">Linux</span><span class="sxs-lookup"><span data-stu-id="9fcc7-117">Linux</span></span>   | <span data-ttu-id="9fcc7-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="9fcc7-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="9fcc7-119">Pour utiliser `dotnet-counters` sur une application x86, vous avez besoin d’une version x86 correspondante de l’outil.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-119">To use `dotnet-counters` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9fcc7-120">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9fcc7-120">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9fcc7-121">Description</span><span class="sxs-lookup"><span data-stu-id="9fcc7-121">Description</span></span>

<span data-ttu-id="9fcc7-122">`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-122">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="9fcc7-123">Il peut observer les valeurs des compteurs de performance publiées via l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-123">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="9fcc7-124">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide `PerfView` de ou de `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-124">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="9fcc7-125">Options</span><span class="sxs-lookup"><span data-stu-id="9fcc7-125">Options</span></span>

- **`--version`**

  <span data-ttu-id="9fcc7-126">Affiche la version de l’utilitaire dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-126">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9fcc7-127">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-127">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="9fcc7-128">Commandes</span><span class="sxs-lookup"><span data-stu-id="9fcc7-128">Commands</span></span>

| <span data-ttu-id="9fcc7-129">Commande</span><span class="sxs-lookup"><span data-stu-id="9fcc7-129">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="9fcc7-130">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="9fcc7-130">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="9fcc7-131">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="9fcc7-131">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="9fcc7-132">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="9fcc7-132">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="9fcc7-133">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="9fcc7-133">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="9fcc7-134">dotnet-compteurs Collect</span><span class="sxs-lookup"><span data-stu-id="9fcc7-134">dotnet-counters collect</span></span>

<span data-ttu-id="9fcc7-135">Collectez périodiquement les valeurs de compteur sélectionnées et exportez-les dans un format de fichier spécifié pour le retraitement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-135">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9fcc7-136">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9fcc7-136">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="9fcc7-137">Options</span><span class="sxs-lookup"><span data-stu-id="9fcc7-137">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9fcc7-138">ID du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-138">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="9fcc7-139">Nom du processus à partir duquel collecter les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-139">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="9fcc7-140">Nom du port de diagnostic à créer.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-140">The name of the diagnostic port to create.</span></span> <span data-ttu-id="9fcc7-141">Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-141">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="9fcc7-142">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="9fcc7-142">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="9fcc7-143">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-143">A comma-separated list of counters.</span></span> <span data-ttu-id="9fcc7-144">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-144">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="9fcc7-145">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-145">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="9fcc7-146">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-146">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="9fcc7-147">Format à exporter.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-147">The format to be exported.</span></span> <span data-ttu-id="9fcc7-148">Actuellement disponible : CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-148">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="9fcc7-149">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-149">The name of the output file.</span></span>

- <span data-ttu-id="9fcc7-150">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="9fcc7-150">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="9fcc7-151">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-151">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="9fcc7-152">`dotnet-counters` lance un processus avec la commande fournie et collecte les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-152">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="9fcc7-153">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-153">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9fcc7-154">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-154">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="9fcc7-155">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-155">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9fcc7-156">Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-156">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="9fcc7-157">La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-157">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="9fcc7-158">Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-158">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="9fcc7-159">Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-159">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="9fcc7-160">Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-160">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="9fcc7-161">Sur Linux et macOS, cette commande attend l’application cible et `dotnet-counters` partager la même variable d' `TMPDIR` environnement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-161">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="9fcc7-162">Dans le cas contraire, la commande expire.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-162">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="9fcc7-163">Pour collecter des mesures à l’aide de `dotnet-counters` , il doit être exécuté en tant qu’utilisateur exécutant le processus cible ou en tant qu’utilisateur racine.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-163">To collect metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="9fcc7-164">Dans le cas contraire, l’outil ne parviendra pas à établir une connexion avec le processus cible.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-164">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

### <a name="examples"></a><span data-ttu-id="9fcc7-165">Exemples</span><span class="sxs-lookup"><span data-stu-id="9fcc7-165">Examples</span></span>

- <span data-ttu-id="9fcc7-166">Collecter tous les compteurs à un intervalle d’actualisation de 3 secondes et générer un CSV en tant que sortie :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-166">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="9fcc7-167">Démarrez `dotnet mvc.dll` en tant que processus enfant et commencez à collecter des compteurs Runtime et ASP.net Core des compteurs d’hébergement à partir du démarrage, puis enregistrez-le en tant que sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-167">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="9fcc7-168">liste dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="9fcc7-168">dotnet-counters list</span></span>

<span data-ttu-id="9fcc7-169">Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-169">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9fcc7-170">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9fcc7-170">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="9fcc7-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="9fcc7-171">Example</span></span>

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
> <span data-ttu-id="9fcc7-172">Les `Microsoft.AspNetCore.Hosting` compteurs s’affichent lorsque des processus identifiés prennent en charge ces compteurs, par exemple, quand une application ASP.net Core s’exécute sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-172">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="9fcc7-173">analyse dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="9fcc7-173">dotnet-counters monitor</span></span>

<span data-ttu-id="9fcc7-174">Affiche régulièrement les valeurs des compteurs sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-174">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9fcc7-175">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9fcc7-175">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="9fcc7-176">Options</span><span class="sxs-lookup"><span data-stu-id="9fcc7-176">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9fcc7-177">ID du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-177">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="9fcc7-178">Nom du processus à analyser.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-178">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="9fcc7-179">Nom du port de diagnostic à créer.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-179">The name of the diagnostic port to create.</span></span> <span data-ttu-id="9fcc7-180">Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-180">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="9fcc7-181">Nombre de secondes avant la mise à jour des compteurs affichés</span><span class="sxs-lookup"><span data-stu-id="9fcc7-181">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="9fcc7-182">Liste de compteurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-182">A comma-separated list of counters.</span></span> <span data-ttu-id="9fcc7-183">Les compteurs peuvent être spécifiés `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-183">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="9fcc7-184">Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-184">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="9fcc7-185">Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-185">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="9fcc7-186">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**</span><span class="sxs-lookup"><span data-stu-id="9fcc7-186">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="9fcc7-187">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-187">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="9fcc7-188">`dotnet-counters` lance un processus avec la commande fournie et surveille les métriques demandées.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-188">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="9fcc7-189">Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-189">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9fcc7-190">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-190">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="9fcc7-191">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-191">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9fcc7-192">Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-192">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="9fcc7-193">La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-193">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="9fcc7-194">Si le processus enfant se termine avant l’outil, l’outil s’arrête également.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-194">If the child process exits before the tool, the tool will exit as well.</span></span> <span data-ttu-id="9fcc7-195">Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-195">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="9fcc7-196">Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-196">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="9fcc7-197">Sur Linux et macOS, cette commande attend l’application cible et `dotnet-counters` partager la même variable d' `TMPDIR` environnement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-197">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span>

> [!NOTE]
> <span data-ttu-id="9fcc7-198">Pour surveiller les métriques à l’aide de `dotnet-counters` , il doit être exécuté en tant qu’utilisateur exécutant le processus cible ou en tant qu’utilisateur racine.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-198">To monitor metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span>

### <a name="examples"></a><span data-ttu-id="9fcc7-199">Exemples</span><span class="sxs-lookup"><span data-stu-id="9fcc7-199">Examples</span></span>

- <span data-ttu-id="9fcc7-200">Surveiller tous les compteurs à partir d' `System.Runtime` un intervalle d’actualisation de 3 secondes :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-200">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="9fcc7-201">Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-201">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="9fcc7-202">Surveiller `EventCounter` les valeurs de définies par l’utilisateur `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-202">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="9fcc7-203">Pour plus d’informations, consultez [Didacticiel : mesurer les performances à l’aide de EventCounters dans .net Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="9fcc7-203">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="9fcc7-204">Affichez tous les compteurs connus disponibles dans `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-204">View all well-known counters that are available in `dotnet-counters`:</span></span>

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- <span data-ttu-id="9fcc7-205">Affichez tous les compteurs connus disponibles dans `dotnet-counters` pour les applications .net 5 :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-205">View all well-known counters that are available in `dotnet-counters` for .NET 5 apps:</span></span>

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- <span data-ttu-id="9fcc7-206">Lancer `my-aspnet-server.exe` et surveiller le nombre d’assemblys chargés à partir de leur démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-206">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9fcc7-207">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-207">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="9fcc7-208">Lancer `my-aspnet-server.exe` avec `arg1` et `arg2` en tant qu’arguments de ligne de commande et surveiller sa plage de travail et sa taille de tas GC depuis son démarrage (.net 5,0 ou version ultérieure uniquement) :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-208">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9fcc7-209">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-209">This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="9fcc7-210">dotnet-Counters PS</span><span class="sxs-lookup"><span data-stu-id="9fcc7-210">dotnet-counters ps</span></span>

<span data-ttu-id="9fcc7-211">Affiche la liste des processus dotnet qui peuvent être analysés.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-211">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9fcc7-212">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9fcc7-212">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="9fcc7-213">Exemple</span><span class="sxs-lookup"><span data-stu-id="9fcc7-213">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="9fcc7-214">Utilisation du port de diagnostic</span><span class="sxs-lookup"><span data-stu-id="9fcc7-214">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9fcc7-215">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-215">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="9fcc7-216">Le port de diagnostic est une nouvelle fonctionnalité d’exécution qui a été ajoutée dans .NET 5, qui vous permet de démarrer l’analyse ou la collecte des compteurs à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-216">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="9fcc7-217">Pour ce faire à l’aide de `dotnet-counters` , vous pouvez utiliser `dotnet-counters <collect|monitor> -- <command>` comme décrit dans les exemples ci-dessus ou utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-217">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="9fcc7-218">L’utilisation `dotnet-counters <collect|monitor> -- <command>` de pour lancer l’application en tant que processus enfant est le moyen le plus simple de l’analyser rapidement à partir de son démarrage.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-218">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="9fcc7-219">Toutefois, lorsque vous souhaitez mieux contrôler la durée de vie de l’application surveillée (par exemple, surveiller l’application pendant les 10 premières minutes uniquement et continuer l’exécution) ou si vous devez interagir avec l’application à l’aide de l’interface CLI, l’utilisation `--diagnostic-port` de l’option vous permet de contrôler à la fois l’application cible en cours d’analyse et `dotnet-counters` .</span><span class="sxs-lookup"><span data-stu-id="9fcc7-219">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="9fcc7-220">La commande suivante permet aux compteurs dotnet de créer un socket de diagnostic nommé `myport.sock` et d’attendre une connexion.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-220">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="9fcc7-221">Sortie :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-221">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="9fcc7-222">Dans une console distincte, lancez l’application cible avec la variable d’environnement `DOTNET_DiagnosticPorts` définie sur la valeur dans la `dotnet-counters` sortie.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-222">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="9fcc7-223">Cela doit ensuite permettre `dotnet-counters` de démarrer la collecte des compteurs sur `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="9fcc7-223">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="9fcc7-224">Le lancement de votre application avec `dotnet run` peut être problématique, car l’interface CLI dotnet peut générer de nombreux processus enfants qui ne sont pas votre application et qui peuvent se connecter à `dotnet-counters` avant votre application, en laissant votre application interrompue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-224">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="9fcc7-225">Nous vous recommandons d’utiliser directement une version autonome de l’application ou `dotnet exec` d’utiliser pour lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="9fcc7-225">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
