---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 0aa404497cb7d6a488fb51e1df8f7f45d4f213fd
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678097"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="c6f14-103">Quels sont les outils de diagnostic disponibles dans .NET Core ?</span><span class="sxs-lookup"><span data-stu-id="c6f14-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="c6f14-104">Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.</span><span class="sxs-lookup"><span data-stu-id="c6f14-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="c6f14-105">Cet article vous aide à trouver les différents outils dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c6f14-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="c6f14-106">Débogueurs gérés</span><span class="sxs-lookup"><span data-stu-id="c6f14-106">Managed debuggers</span></span>

<span data-ttu-id="c6f14-107">Les [débogueurs managés](managed-debuggers.md) vous permettent d’interagir avec votre programme.</span><span class="sxs-lookup"><span data-stu-id="c6f14-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="c6f14-108">La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="c6f14-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="c6f14-109">Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.</span><span class="sxs-lookup"><span data-stu-id="c6f14-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="c6f14-110">Journalisation et suivi</span><span class="sxs-lookup"><span data-stu-id="c6f14-110">Logging and tracing</span></span>

<span data-ttu-id="c6f14-111">La [journalisation et le suivi](logging-tracing.md) sont des techniques associées.</span><span class="sxs-lookup"><span data-stu-id="c6f14-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="c6f14-112">Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="c6f14-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="c6f14-113">Les fichiers consignent le détail des tâches exécutées par un programme.</span><span class="sxs-lookup"><span data-stu-id="c6f14-113">The files record the details of what a program does.</span></span> <span data-ttu-id="c6f14-114">Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="c6f14-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="c6f14-115">Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.</span><span class="sxs-lookup"><span data-stu-id="c6f14-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="c6f14-116">Mesures</span><span class="sxs-lookup"><span data-stu-id="c6f14-116">Metrics</span></span>

<span data-ttu-id="c6f14-117">[EventCounters](event-counters.md) vous permet d’écrire des mesures pour identifier et surveiller les problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="c6f14-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="c6f14-118">Les métriques entraînent une baisse des performances par rapport au suivi, ce qui le rend plus adapté à une analyse des performances Always on.</span><span class="sxs-lookup"><span data-stu-id="c6f14-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="c6f14-119">Le Runtime .NET et les bibliothèques publient plusieurs [EventCounters bien connus](available-counters.md) que vous pouvez également surveiller.</span><span class="sxs-lookup"><span data-stu-id="c6f14-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="c6f14-120">Test unitaire</span><span class="sxs-lookup"><span data-stu-id="c6f14-120">Unit testing</span></span>

<span data-ttu-id="c6f14-121">Le [test unitaire](../testing/index.md) est un composant clé de l’intégration et du déploiement continus de logiciels de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="c6f14-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="c6f14-122">Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.</span><span class="sxs-lookup"><span data-stu-id="c6f14-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="c6f14-123">Vidages</span><span class="sxs-lookup"><span data-stu-id="c6f14-123">Dumps</span></span>

<span data-ttu-id="c6f14-124">Un [dump](./dumps.md) est un fichier qui contient un instantané du processus au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="c6f14-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="c6f14-125">Elles peuvent être utiles pour examiner l’état de votre application à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="c6f14-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="c6f14-126">Collecter les diagnostics dans les conteneurs</span><span class="sxs-lookup"><span data-stu-id="c6f14-126">Collect diagnostics in containers</span></span>

<span data-ttu-id="c6f14-127">Les outils de diagnostic utilisés dans les environnements Linux non conteneurs peuvent également être utilisés pour [collecter les diagnostics dans des conteneurs](diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="c6f14-127">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="c6f14-128">Il n’y a que quelques modifications d’utilisation nécessaires pour s’assurer que les outils fonctionnent dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="c6f14-128">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="c6f14-129">Outils globaux de diagnostic .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6f14-129">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="c6f14-130">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="c6f14-130">dotnet-counters</span></span>

<span data-ttu-id="c6f14-131">[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="c6f14-131">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="c6f14-132">Il observe les valeurs de compteur de performance publiées par le biais de l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="c6f14-132">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="c6f14-133">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6f14-133">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="c6f14-134">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="c6f14-134">dotnet-dump</span></span>

<span data-ttu-id="c6f14-135">L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.</span><span class="sxs-lookup"><span data-stu-id="c6f14-135">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="c6f14-136">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="c6f14-136">dotnet-gcdump</span></span>

<span data-ttu-id="c6f14-137">L’outil [dotnet-gcdump](dotnet-gcdump.md) est un moyen de collecter des vidages de mémoire GC (garbage collector) des processus .net en direct.</span><span class="sxs-lookup"><span data-stu-id="c6f14-137">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="c6f14-138">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="c6f14-138">dotnet-trace</span></span>

<span data-ttu-id="c6f14-139">.NET Core comprend ce qui est appelé `EventPipe` par le biais duquel les données de diagnostic sont exposées.</span><span class="sxs-lookup"><span data-stu-id="c6f14-139">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="c6f14-140">L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.</span><span class="sxs-lookup"><span data-stu-id="c6f14-140">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="c6f14-141">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="c6f14-141">dotnet-symbol</span></span>

<span data-ttu-id="c6f14-142">[dotnet-Symbol télécharge des](dotnet-symbol.md) fichiers (symboles, DAC/DBI, fichiers hôtes, etc.) nécessaires à l’ouverture d’un vidage principal ou d’un minidump.</span><span class="sxs-lookup"><span data-stu-id="c6f14-142">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="c6f14-143">Utilisez cet outil si vous avez besoin de symboles et de modules pour déboguer un fichier de vidage capturé sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c6f14-143">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="c6f14-144">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="c6f14-144">dotnet-sos</span></span>

<span data-ttu-id="c6f14-145">[dotnet-SOS](dotnet-sos.md) est utilisé pour installer l' [extension de débogage SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) sur Linux ou MacOS (ou sur Windows si vous utilisez des outils de débogage plus anciens).</span><span class="sxs-lookup"><span data-stu-id="c6f14-145">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="c6f14-146">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="c6f14-146">PerfCollect</span></span>

<span data-ttu-id="c6f14-147">[PerfCollect](trace-perfcollect-lttng.md) est un script bash que vous pouvez utiliser pour collecter des traces avec `perf` et `LTTng` pour une analyse des performances plus approfondie des applications .net s’exécutant sur des distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="c6f14-147">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="c6f14-148">Tutoriels de diagnostics .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6f14-148">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="c6f14-149">Déboguer une fuite de mémoire</span><span class="sxs-lookup"><span data-stu-id="c6f14-149">Debug a memory leak</span></span>

<span data-ttu-id="c6f14-150">[Didacticiel : déboguer une fuite de mémoire](debug-memory-leak.md) vous guide tout au long de la détection d’une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c6f14-150">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="c6f14-151">L’outil [dotnet-Counters](dotnet-counters.md) est utilisé pour confirmer la fuite et l’outil [dotnet-dump](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.</span><span class="sxs-lookup"><span data-stu-id="c6f14-151">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="c6f14-152">Déboguer une utilisation élevée du processeur</span><span class="sxs-lookup"><span data-stu-id="c6f14-152">Debug high CPU usage</span></span>

<span data-ttu-id="c6f14-153">[Didacticiel : déboguer l’utilisation intensive du processeur](debug-highcpu.md) vous guide tout au long de l’examen de l’utilisation intensive du processeur.</span><span class="sxs-lookup"><span data-stu-id="c6f14-153">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="c6f14-154">Elle utilise l’outil [dotnet-Counters](dotnet-counters.md) pour vérifier l’utilisation intensive du processeur.</span><span class="sxs-lookup"><span data-stu-id="c6f14-154">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="c6f14-155">Il vous guide ensuite dans l’utilisation [de trace for Performance Analysis Utility ( `dotnet-trace` )](dotnet-trace.md) ou Linux `perf` pour collecter et afficher le profil d’utilisation de l’UC.</span><span class="sxs-lookup"><span data-stu-id="c6f14-155">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="c6f14-156">Déboguer un interblocage</span><span class="sxs-lookup"><span data-stu-id="c6f14-156">Debug deadlock</span></span>

<span data-ttu-id="c6f14-157">[Didacticiel : déboguer le blocage](debug-deadlock.md) vous montre comment utiliser l’outil [dotnet-dump](dotnet-dump.md) pour examiner les threads et les verrous.</span><span class="sxs-lookup"><span data-stu-id="c6f14-157">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="c6f14-158">Déboguer des vidages Linux</span><span class="sxs-lookup"><span data-stu-id="c6f14-158">Debug Linux dumps</span></span>

<span data-ttu-id="c6f14-159">[Déboguer les vidages Linux](debug-linux-dumps.md) explique comment collecter et analyser les vidages sur Linux.</span><span class="sxs-lookup"><span data-stu-id="c6f14-159">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="c6f14-160">Mesurer les performances à l’aide de EventCounters</span><span class="sxs-lookup"><span data-stu-id="c6f14-160">Measure performance using EventCounters</span></span>

<span data-ttu-id="c6f14-161">[Didacticiel : mesurer les performances à l’aide de EventCounters dans .net](event-counter-perf.md) montre comment utiliser l' <xref:System.Diagnostics.Tracing.EventCounter> API pour mesurer les performances dans votre application .net.</span><span class="sxs-lookup"><span data-stu-id="c6f14-161">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
