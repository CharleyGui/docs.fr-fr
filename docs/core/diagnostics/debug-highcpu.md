---
title: Utilisation élevée du processeur par le débogage-.NET Core
description: Un didacticiel qui vous guide tout au long du débogage de l’utilisation élevée de l’UC dans .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 91f31f77b54398d2f9816890338955bc9b0852e4
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437833"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="9bdf5-103">Déboguer une utilisation élevée du processeur dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="9bdf5-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="9bdf5-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9bdf5-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="9bdf5-105">Dans ce didacticiel, vous allez apprendre à déboguer un scénario d’utilisation excessive de l’UC.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="9bdf5-106">À l’aide de l’exemple fourni ASP.NET Core référentiel de code source de l' [application Web](/samples/dotnet/samples/diagnostic-scenarios) , vous pouvez provoquer un blocage intentionnellement.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="9bdf5-107">Le point de terminaison subira un blocage et l’accumulation des threads.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="9bdf5-108">Vous allez apprendre à utiliser différents outils pour diagnostiquer ce scénario avec plusieurs éléments clés de données de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="9bdf5-109">Ce didacticiel présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="9bdf5-110">Examiner l’utilisation élevée du processeur</span><span class="sxs-lookup"><span data-stu-id="9bdf5-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="9bdf5-111">Déterminer l’utilisation de l’UC avec [dotnet-Counters](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="9bdf5-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="9bdf5-112">Utiliser [dotnet-trace](dotnet-trace.md) pour la génération de trace</span><span class="sxs-lookup"><span data-stu-id="9bdf5-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="9bdf5-113">Performances des profils dans PerfView</span><span class="sxs-lookup"><span data-stu-id="9bdf5-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="9bdf5-114">Diagnostiquer et résoudre l’utilisation excessive du processeur</span><span class="sxs-lookup"><span data-stu-id="9bdf5-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9bdf5-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="9bdf5-115">Prerequisites</span></span>

<span data-ttu-id="9bdf5-116">Le didacticiel utilise :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-116">The tutorial uses:</span></span>

- <span data-ttu-id="9bdf5-117">[Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="9bdf5-118">[Exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios) pour déclencher le scénario.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-118">[Sample debug target](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="9bdf5-119">[dotnet-trace](dotnet-trace.md) pour répertorier les processus et générer un profil.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="9bdf5-120">[dotnet-compteurs](dotnet-counters.md) pour surveiller l’utilisation de l’UC.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="9bdf5-121">Compteurs UC</span><span class="sxs-lookup"><span data-stu-id="9bdf5-121">CPU counters</span></span>

<span data-ttu-id="9bdf5-122">Avant de tenter de collecter les données de diagnostic, vous devez observer une condition d’UC élevée.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="9bdf5-123">Exécutez l' [exemple d’application](/samples/dotnet/samples/diagnostic-scenarios) à l’aide de la commande suivante à partir du répertoire racine du projet.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-123">Run the [sample application](/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="9bdf5-124">Pour Rechercher l’ID de processus, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="9bdf5-125">Prenez note de l’ID de processus à partir de la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="9bdf5-126">Notre ID de processus était `22884` , mais la vôtre sera différente.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="9bdf5-127">Pour vérifier l’utilisation actuelle de l’UC, utilisez la commande [dotnet-Counters](dotnet-counters.md) Tool :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="9bdf5-128">Le `refresh-interval` est le nombre de secondes entre les valeurs de l’UC d’interrogation de compteur.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="9bdf5-129">La sortie doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="9bdf5-130">Avec l’application Web en cours d’exécution, immédiatement après le démarrage, l’UC n’est pas consommée et est signalée à `0%` .</span><span class="sxs-lookup"><span data-stu-id="9bdf5-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="9bdf5-131">Accédez à l' `api/diagscenario/highcpu` itinéraire avec `60000` comme paramètre d’itinéraire :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="9bdf5-132">À présent, réexécutez la commande [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="9bdf5-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="9bdf5-133">Pour surveiller uniquement le `cpu-usage` , spécifiez `System.Runtime[cpu-usage]` dans le cadre de la commande.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor --counters System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="9bdf5-134">Vous devez voir une augmentation de l’utilisation de l’UC comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="9bdf5-135">Pendant toute la durée de la demande, l’utilisation de l’UC passera à environ 25%.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="9bdf5-136">En fonction de l’ordinateur hôte, attendez-vous à varier l’utilisation du processeur.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="9bdf5-137">Pour visualiser une utilisation du processeur encore plus élevée, vous pouvez exercer ce point de terminaison dans plusieurs onglets de navigateur simultanément.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="9bdf5-138">À ce stade, vous pouvez indiquer en toute sécurité que l’UC s’exécute plus haut que prévu.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="9bdf5-139">Génération de trace</span><span class="sxs-lookup"><span data-stu-id="9bdf5-139">Trace generation</span></span>

<span data-ttu-id="9bdf5-140">Lors de l’analyse d’une requête lente, vous avez besoin d’un outil de diagnostic qui peut fournir des informations sur ce que fait le code.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="9bdf5-141">Le choix habituel est un profileur, et il existe différentes options de profileur à choisir.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="9bdf5-142">Linux</span><span class="sxs-lookup"><span data-stu-id="9bdf5-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="9bdf5-143">L' `perf` outil peut être utilisé pour générer des profils d’application .net core.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="9bdf5-144">Quittez l’instance précédente de l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios).</span><span class="sxs-lookup"><span data-stu-id="9bdf5-144">Exit the previous instance of the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="9bdf5-145">Définissez la `COMPlus_PerfMapEnabled` variable d’environnement pour que l’application .net Core crée un `map` fichier dans le `/tmp` répertoire.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="9bdf5-146">Ce `map` fichier est utilisé par `perf` pour mapper l’adresse de l’UC aux fonctions générées juste-à-temps par nom.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="9bdf5-147">Pour plus d’informations, consultez [écrire une carte de performances](../run-time-config/debugging-profiling.md#write-perf-map).</span><span class="sxs-lookup"><span data-stu-id="9bdf5-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="9bdf5-148">Exécutez l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios) dans la même session de terminal.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-148">Run the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="9bdf5-149">Renouvelez le point de terminaison de l’API UC élevée ( `https://localhost:5001/api/diagscenario/highcpu/60000` ).</span><span class="sxs-lookup"><span data-stu-id="9bdf5-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="9bdf5-150">Pendant qu’elle s’exécute dans la requête de 1 minute, exécutez la `perf` commande avec votre ID de processus :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="9bdf5-151">La `perf` commande démarre le processus de collecte des performances.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="9bdf5-152">Laissez-le s’exécuter pendant environ 20-30 secondes, puis appuyez sur <kbd>Ctrl + C</kbd> pour quitter le processus de collecte.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="9bdf5-153">Vous pouvez utiliser la même `perf` commande pour afficher la sortie de la trace.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="9bdf5-154">Vous pouvez également générer un _graphique à flamme_ à l’aide des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="9bdf5-155">Cette commande génère un `flamegraph.svg` que vous pouvez afficher dans le navigateur pour examiner le problème de performances :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="9bdf5-156">[![Image SVG du graphique à flamme](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9bdf5-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="9bdf5-157">Windows</span><span class="sxs-lookup"><span data-stu-id="9bdf5-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="9bdf5-158">Sur Windows, vous pouvez utiliser l’outil [dotnet-trace](dotnet-trace.md) en tant que profileur.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="9bdf5-159">À l’aide de l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios)précédent, réexécutez le point de terminaison d’UC élevé ( `https://localhost:5001/api/diagscenario/highcpu/60000` ).</span><span class="sxs-lookup"><span data-stu-id="9bdf5-159">Using the previous [sample debug target](/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="9bdf5-160">Pendant qu’elle s’exécute dans la requête de 1 minute, utilisez la `collect` commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="9bdf5-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="9bdf5-161">Laissez [dotnet-trace](dotnet-trace.md) s’exécuter pendant environ 20-30 secondes, puis appuyez sur <kbd>entrée</kbd> pour quitter la collection.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="9bdf5-162">Le résultat est un `nettrace` fichier situé dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="9bdf5-163">Les `nettrace` fichiers sont un excellent moyen d’utiliser les outils d’analyse existants sur Windows.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="9bdf5-164">Ouvrez `nettrace` avec [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="9bdf5-165">[![Image PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9bdf5-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="9bdf5-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bdf5-166">See also</span></span>

- <span data-ttu-id="9bdf5-167">[dotnet-trace](dotnet-trace.md) pour répertorier les processus</span><span class="sxs-lookup"><span data-stu-id="9bdf5-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="9bdf5-168">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée</span><span class="sxs-lookup"><span data-stu-id="9bdf5-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="9bdf5-169">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage</span><span class="sxs-lookup"><span data-stu-id="9bdf5-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="9bdf5-170">dotnet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="9bdf5-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="9bdf5-171">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9bdf5-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bdf5-172">Déboguer un interblocage dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="9bdf5-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
