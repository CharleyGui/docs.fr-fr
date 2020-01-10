---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715578"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="c625c-103">Quels sont les outils de diagnostic disponibles dans .NET Core ?</span><span class="sxs-lookup"><span data-stu-id="c625c-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="c625c-104">Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.</span><span class="sxs-lookup"><span data-stu-id="c625c-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="c625c-105">Cet article vous aide à trouver les différents outils dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c625c-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="c625c-106">Débogueurs gérés</span><span class="sxs-lookup"><span data-stu-id="c625c-106">Managed debuggers</span></span>

<span data-ttu-id="c625c-107">Les [débogueurs managés](managed-debuggers.md) vous permettent d’interagir avec votre programme.</span><span class="sxs-lookup"><span data-stu-id="c625c-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="c625c-108">La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="c625c-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="c625c-109">Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.</span><span class="sxs-lookup"><span data-stu-id="c625c-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="c625c-110">Journalisation et suivi</span><span class="sxs-lookup"><span data-stu-id="c625c-110">Logging and tracing</span></span>

<span data-ttu-id="c625c-111">La [journalisation et le suivi](logging-tracing.md) sont des techniques associées.</span><span class="sxs-lookup"><span data-stu-id="c625c-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="c625c-112">Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="c625c-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="c625c-113">Les fichiers consignent le détail des tâches exécutées par un programme.</span><span class="sxs-lookup"><span data-stu-id="c625c-113">The files record the details of what a program does.</span></span> <span data-ttu-id="c625c-114">Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="c625c-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="c625c-115">Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.</span><span class="sxs-lookup"><span data-stu-id="c625c-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="c625c-116">Test unitaire</span><span class="sxs-lookup"><span data-stu-id="c625c-116">Unit testing</span></span>

<span data-ttu-id="c625c-117">Le [test unitaire](../testing/index.md) est un composant clé de l’intégration et du déploiement continus de logiciels de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="c625c-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="c625c-118">Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.</span><span class="sxs-lookup"><span data-stu-id="c625c-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="c625c-119">Outils globaux .NET Core dotnet diagnostic</span><span class="sxs-lookup"><span data-stu-id="c625c-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="c625c-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="c625c-120">dotnet-counters</span></span>

<span data-ttu-id="c625c-121">[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="c625c-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="c625c-122">Il observe les valeurs de compteur de performance publiées via l’API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="c625c-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="c625c-123">Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c625c-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="c625c-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="c625c-124">dotnet-dump</span></span>

<span data-ttu-id="c625c-125">L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.</span><span class="sxs-lookup"><span data-stu-id="c625c-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="c625c-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="c625c-126">dotnet-trace</span></span>

<span data-ttu-id="c625c-127">.NET Core comprend ce qui est appelé le `EventPipe` par le biais duquel les données de diagnostic sont exposées.</span><span class="sxs-lookup"><span data-stu-id="c625c-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="c625c-128">L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.</span><span class="sxs-lookup"><span data-stu-id="c625c-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="c625c-129">Tutoriels de diagnostics .NET Core</span><span class="sxs-lookup"><span data-stu-id="c625c-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="c625c-130">Déboguer une fuite de mémoire</span><span class="sxs-lookup"><span data-stu-id="c625c-130">Debug a memory leak</span></span>

<span data-ttu-id="c625c-131">[Didacticiel : déboguer une fuite de mémoire](debug-memory-leak.md) vous guide tout au long de la détection d’une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c625c-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="c625c-132">L’outil [dotnet-Counters](dotnet-counters.md) est utilisé pour confirmer la fuite et l’outil [dotnet-dump](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.</span><span class="sxs-lookup"><span data-stu-id="c625c-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
