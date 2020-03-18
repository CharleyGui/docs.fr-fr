---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399048"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="b0758-103">Quels sont les outils de diagnostic disponibles dans .NET Core ?</span><span class="sxs-lookup"><span data-stu-id="b0758-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="b0758-104">Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.</span><span class="sxs-lookup"><span data-stu-id="b0758-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="b0758-105">Cet article vous aide à trouver les différents outils dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b0758-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="b0758-106">Débogueurs gérés</span><span class="sxs-lookup"><span data-stu-id="b0758-106">Managed debuggers</span></span>

<span data-ttu-id="b0758-107">[Les débbuggeurs gérés](managed-debuggers.md) vous permettent d’interagir avec votre programme.</span><span class="sxs-lookup"><span data-stu-id="b0758-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="b0758-108">La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="b0758-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="b0758-109">Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.</span><span class="sxs-lookup"><span data-stu-id="b0758-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="b0758-110">Journalisation et suivi</span><span class="sxs-lookup"><span data-stu-id="b0758-110">Logging and tracing</span></span>

<span data-ttu-id="b0758-111">[L’exploitation forestière et le traçage](logging-tracing.md) sont des techniques connexes.</span><span class="sxs-lookup"><span data-stu-id="b0758-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="b0758-112">Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="b0758-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="b0758-113">Les fichiers consignent le détail des tâches exécutées par un programme.</span><span class="sxs-lookup"><span data-stu-id="b0758-113">The files record the details of what a program does.</span></span> <span data-ttu-id="b0758-114">Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="b0758-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="b0758-115">Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.</span><span class="sxs-lookup"><span data-stu-id="b0758-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="b0758-116">Test des unités</span><span class="sxs-lookup"><span data-stu-id="b0758-116">Unit testing</span></span>

<span data-ttu-id="b0758-117">[Le test unitaire](../testing/index.md) est un élément clé de l’intégration continue et du déploiement de logiciels de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="b0758-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="b0758-118">Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.</span><span class="sxs-lookup"><span data-stu-id="b0758-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="b0758-119">.NET Core dotnet diagnostic Global Tools</span><span class="sxs-lookup"><span data-stu-id="b0758-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="b0758-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b0758-120">dotnet-counters</span></span>

<span data-ttu-id="b0758-121">[dotnet-counters](dotnet-counters.md) est un outil de surveillance des performances pour la surveillance de la santé de premier niveau et l’enquête sur le rendement.</span><span class="sxs-lookup"><span data-stu-id="b0758-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="b0758-122">Il observe les valeurs de <xref:System.Diagnostics.Tracing.EventCounter> compteur de performance publiées via l’API.</span><span class="sxs-lookup"><span data-stu-id="b0758-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="b0758-123">Par exemple, vous pouvez surveiller rapidement des choses comme l’utilisation du processeur ou le taux d’exceptions jetés dans votre application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0758-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="b0758-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="b0758-124">dotnet-dump</span></span>

<span data-ttu-id="b0758-125">[L’outil dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les décharges de base de Windows et Linux sans un débbugger indigène.</span><span class="sxs-lookup"><span data-stu-id="b0758-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="b0758-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="b0758-126">dotnet-trace</span></span>

<span data-ttu-id="b0758-127">.NET Core comprend ce `EventPipe` qu’on appelle le moyen par lequel les données diagnostiques sont exposées.</span><span class="sxs-lookup"><span data-stu-id="b0758-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="b0758-128">[L’outil dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes de votre application qui peuvent vous aider dans les scénarios où vous devez provoquer des applications qui fonctionnent lentement.</span><span class="sxs-lookup"><span data-stu-id="b0758-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="b0758-129">Tutoriels de diagnostics .NET Core</span><span class="sxs-lookup"><span data-stu-id="b0758-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="b0758-130">Déboguer une fuite de mémoire</span><span class="sxs-lookup"><span data-stu-id="b0758-130">Debug a memory leak</span></span>

<span data-ttu-id="b0758-131">[Tutorial: Debug une fuite de mémoire](debug-memory-leak.md) marche à travers la recherche d’une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b0758-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="b0758-132">[L’outil dotnet-compteurs](dotnet-counters.md) est utilisé pour confirmer la fuite et [l’outil de décharge de dotnet](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.</span><span class="sxs-lookup"><span data-stu-id="b0758-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
