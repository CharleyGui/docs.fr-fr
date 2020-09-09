---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 568f237e131cde18dad7c87ddff2fdd3d4bc5b8b
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89597984"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="38392-103">Quels sont les outils de diagnostic disponibles dans .NET Core ?</span><span class="sxs-lookup"><span data-stu-id="38392-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="38392-104">Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.</span><span class="sxs-lookup"><span data-stu-id="38392-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="38392-105">Cet article vous aide à trouver les différents outils dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="38392-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="38392-106">Débogueurs gérés</span><span class="sxs-lookup"><span data-stu-id="38392-106">Managed debuggers</span></span>

<span data-ttu-id="38392-107">Les [débogueurs managés](managed-debuggers.md) vous permettent d’interagir avec votre programme.</span><span class="sxs-lookup"><span data-stu-id="38392-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="38392-108">La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="38392-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="38392-109">Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.</span><span class="sxs-lookup"><span data-stu-id="38392-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="38392-110">Journalisation et suivi</span><span class="sxs-lookup"><span data-stu-id="38392-110">Logging and tracing</span></span>

<span data-ttu-id="38392-111">La [journalisation et le suivi](logging-tracing.md) sont des techniques associées.</span><span class="sxs-lookup"><span data-stu-id="38392-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="38392-112">Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="38392-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="38392-113">Les fichiers consignent le détail des tâches exécutées par un programme.</span><span class="sxs-lookup"><span data-stu-id="38392-113">The files record the details of what a program does.</span></span> <span data-ttu-id="38392-114">Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="38392-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="38392-115">Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.</span><span class="sxs-lookup"><span data-stu-id="38392-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="38392-116">Test unitaire</span><span class="sxs-lookup"><span data-stu-id="38392-116">Unit testing</span></span>

<span data-ttu-id="38392-117">Le [test unitaire](../testing/index.md) est un composant clé de l’intégration et du déploiement continus de logiciels de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="38392-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="38392-118">Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.</span><span class="sxs-lookup"><span data-stu-id="38392-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="38392-119">Déboguer des vidages Linux</span><span class="sxs-lookup"><span data-stu-id="38392-119">Debug Linux dumps</span></span>

<span data-ttu-id="38392-120">[Déboguer les vidages Linux](debug-linux-dumps.md) explique comment collecter et analyser les vidages sur Linux.</span><span class="sxs-lookup"><span data-stu-id="38392-120">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="38392-121">Outils globaux de diagnostic .NET Core</span><span class="sxs-lookup"><span data-stu-id="38392-121">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="38392-122">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="38392-122">dotnet-counters</span></span>

<span data-ttu-id="38392-123">[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="38392-123">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="38392-124">Il observe les valeurs de compteur de performance publiées par le biais de l' <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="38392-124">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="38392-125">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38392-125">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="38392-126">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="38392-126">dotnet-dump</span></span>

<span data-ttu-id="38392-127">L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.</span><span class="sxs-lookup"><span data-stu-id="38392-127">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="38392-128">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="38392-128">dotnet-gcdump</span></span>

<span data-ttu-id="38392-129">L’outil [dotnet-gcdump](dotnet-gcdump.md) est un moyen de collecter des vidages de mémoire GC (garbage collector) des processus .net en direct.</span><span class="sxs-lookup"><span data-stu-id="38392-129">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="38392-130">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="38392-130">dotnet-trace</span></span>

<span data-ttu-id="38392-131">.NET Core comprend ce qui est appelé `EventPipe` par le biais duquel les données de diagnostic sont exposées.</span><span class="sxs-lookup"><span data-stu-id="38392-131">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="38392-132">L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.</span><span class="sxs-lookup"><span data-stu-id="38392-132">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="38392-133">dotnet-Symbol</span><span class="sxs-lookup"><span data-stu-id="38392-133">dotnet-symbol</span></span>

<span data-ttu-id="38392-134">[dotnet-Symbol télécharge des](dotnet-symbol.md) fichiers (symboles, DAC/DBI, fichiers hôtes, etc.) nécessaires à l’ouverture d’un vidage principal ou d’un minidump.</span><span class="sxs-lookup"><span data-stu-id="38392-134">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="38392-135">Utilisez cet outil si vous avez besoin de symboles et de modules pour déboguer un fichier de vidage capturé sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38392-135">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="38392-136">dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="38392-136">dotnet-sos</span></span>

<span data-ttu-id="38392-137">[dotnet-SOS](dotnet-sos.md) est utilisé pour installer l' [extension de débogage SOS](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) sur Linux ou MacOS (ou sur Windows si vous utilisez des outils de débogage plus anciens).</span><span class="sxs-lookup"><span data-stu-id="38392-137">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="38392-138">Tutoriels de diagnostics .NET Core</span><span class="sxs-lookup"><span data-stu-id="38392-138">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="38392-139">Déboguer une fuite de mémoire</span><span class="sxs-lookup"><span data-stu-id="38392-139">Debug a memory leak</span></span>

<span data-ttu-id="38392-140">[Didacticiel : déboguer une fuite de mémoire](debug-memory-leak.md) vous guide tout au long de la détection d’une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="38392-140">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="38392-141">L’outil [dotnet-Counters](dotnet-counters.md) est utilisé pour confirmer la fuite et l’outil [dotnet-dump](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.</span><span class="sxs-lookup"><span data-stu-id="38392-141">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="38392-142">Déboguer une utilisation élevée du processeur</span><span class="sxs-lookup"><span data-stu-id="38392-142">Debug high CPU usage</span></span>

<span data-ttu-id="38392-143">[Didacticiel : déboguer l’utilisation intensive du processeur](debug-highcpu.md) vous guide tout au long de l’examen de l’utilisation intensive du processeur.</span><span class="sxs-lookup"><span data-stu-id="38392-143">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="38392-144">Elle utilise l’outil [dotnet-Counters](dotnet-counters.md) pour vérifier l’utilisation intensive du processeur.</span><span class="sxs-lookup"><span data-stu-id="38392-144">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="38392-145">Il vous guide ensuite dans l’utilisation [de trace for Performance Analysis Utility ( `dotnet-trace` )](dotnet-trace.md) ou Linux `perf` pour collecter et afficher le profil d’utilisation de l’UC.</span><span class="sxs-lookup"><span data-stu-id="38392-145">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="38392-146">Déboguer un interblocage</span><span class="sxs-lookup"><span data-stu-id="38392-146">Debug deadlock</span></span>

<span data-ttu-id="38392-147">[Didacticiel : déboguer le blocage](debug-deadlock.md) vous montre comment utiliser l’outil [dotnet-dump](dotnet-dump.md) pour examiner les threads et les verrous.</span><span class="sxs-lookup"><span data-stu-id="38392-147">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
