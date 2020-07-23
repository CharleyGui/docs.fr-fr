---
title: Blocage du débogage-.NET Core
description: Un didacticiel qui vous guide tout au long du débogage d’un problème de verrouillage dans .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 247521176297254180d794d4d4fc850f30e343b0
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86926405"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="4b275-103">Déboguer un interblocage dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b275-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="4b275-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4b275-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="4b275-105">Dans ce didacticiel, vous allez apprendre à déboguer un scénario de blocage.</span><span class="sxs-lookup"><span data-stu-id="4b275-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="4b275-106">À l’aide de l’exemple fourni ASP.NET Core référentiel de code source de l' [application Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , vous pouvez provoquer un blocage intentionnellement.</span><span class="sxs-lookup"><span data-stu-id="4b275-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="4b275-107">Le point de terminaison subira un blocage et l’accumulation des threads.</span><span class="sxs-lookup"><span data-stu-id="4b275-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="4b275-108">Vous apprendrez comment vous pouvez utiliser différents outils pour analyser le problème, tels que les vidages de base, l’analyse de vidage noyau et le suivi de processus.</span><span class="sxs-lookup"><span data-stu-id="4b275-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="4b275-109">Ce didacticiel présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b275-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4b275-110">Examiner le blocage d’une application</span><span class="sxs-lookup"><span data-stu-id="4b275-110">Investigate an app hang</span></span>
> - <span data-ttu-id="4b275-111">Générer un fichier de vidage noyau</span><span class="sxs-lookup"><span data-stu-id="4b275-111">Generate a core dump file</span></span>
> - <span data-ttu-id="4b275-112">Analyser les threads de processus dans le fichier dump</span><span class="sxs-lookup"><span data-stu-id="4b275-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="4b275-113">Analyser les piles et les blocs de synchronisation</span><span class="sxs-lookup"><span data-stu-id="4b275-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="4b275-114">Diagnostiquer et résoudre un blocage</span><span class="sxs-lookup"><span data-stu-id="4b275-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b275-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4b275-115">Prerequisites</span></span>

<span data-ttu-id="4b275-116">Le didacticiel utilise :</span><span class="sxs-lookup"><span data-stu-id="4b275-116">The tutorial uses:</span></span>

- <span data-ttu-id="4b275-117">[.Net Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="4b275-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version</span></span>
- <span data-ttu-id="4b275-118">[Exemple de cible de débogage-application Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pour déclencher le scénario</span><span class="sxs-lookup"><span data-stu-id="4b275-118">[Sample debug target - web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="4b275-119">[dotnet-trace](dotnet-trace.md) pour répertorier les processus</span><span class="sxs-lookup"><span data-stu-id="4b275-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="4b275-120">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage</span><span class="sxs-lookup"><span data-stu-id="4b275-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="4b275-121">Génération de l’image mémoire principale</span><span class="sxs-lookup"><span data-stu-id="4b275-121">Core dump generation</span></span>

<span data-ttu-id="4b275-122">Pour examiner l’absence de réponse de l’application, un vidage de base ou une image mémoire vous permet d’inspecter l’état de ses threads et les éventuels verrous susceptibles de rencontrer des problèmes de contention.</span><span class="sxs-lookup"><span data-stu-id="4b275-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="4b275-123">Exécutez l’exemple d’application de [débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) à l’aide de la commande suivante à partir du répertoire racine de l’exemple :</span><span class="sxs-lookup"><span data-stu-id="4b275-123">Run the [sample debug](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="4b275-124">Pour Rechercher l’ID de processus, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4b275-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="4b275-125">Prenez note de l’ID de processus à partir de la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="4b275-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="4b275-126">Notre ID de processus était `4807` , mais la vôtre sera différente.</span><span class="sxs-lookup"><span data-stu-id="4b275-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="4b275-127">Accédez à l’URL suivante, qui est un point de terminaison d’API sur l’exemple de site :</span><span class="sxs-lookup"><span data-stu-id="4b275-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

[https://localhost:5001/api/diagscenario/deadlock](https://localhost:5001/api/diagscenario/deadlock)

<span data-ttu-id="4b275-128">La demande d’API au site se bloquera et ne répondra pas.</span><span class="sxs-lookup"><span data-stu-id="4b275-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="4b275-129">Laissez la demande s’exécuter pendant environ 10-15 secondes.</span><span class="sxs-lookup"><span data-stu-id="4b275-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="4b275-130">Créez ensuite le vidage de base à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4b275-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="4b275-131">Linux</span><span class="sxs-lookup"><span data-stu-id="4b275-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="4b275-132">Windows</span><span class="sxs-lookup"><span data-stu-id="4b275-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="4b275-133">Analyser le vidage principal</span><span class="sxs-lookup"><span data-stu-id="4b275-133">Analyze the core dump</span></span>

<span data-ttu-id="4b275-134">Pour démarrer l’analyse de vidage de base, ouvrez le vidage de base à l’aide de la `dotnet-dump analyze` commande suivante.</span><span class="sxs-lookup"><span data-stu-id="4b275-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="4b275-135">L’argument est le chemin d’accès au fichier de vidage principal qui a été collecté précédemment.</span><span class="sxs-lookup"><span data-stu-id="4b275-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="4b275-136">Étant donné que vous examinez un blocage potentiel, vous souhaitez avoir une idée globale de l’activité des threads dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4b275-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="4b275-137">Vous pouvez utiliser la `threads` commande comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="4b275-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="4b275-138">La sortie affiche tous les threads en cours d’exécution dans le processus avec leur ID de thread de débogueur et l’ID de thread de système d’exploitation associés.</span><span class="sxs-lookup"><span data-stu-id="4b275-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="4b275-139">En fonction de la sortie, il y a plus de 300 threads.</span><span class="sxs-lookup"><span data-stu-id="4b275-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="4b275-140">L’étape suivante consiste à obtenir une meilleure compréhension de ce que les threads exécute actuellement en obtenant la pile des appels de chaque thread.</span><span class="sxs-lookup"><span data-stu-id="4b275-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="4b275-141">La `clrstack` commande peut être utilisée pour générer piles.</span><span class="sxs-lookup"><span data-stu-id="4b275-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="4b275-142">Il peut générer une seule pile d’appels ou tous les piles.</span><span class="sxs-lookup"><span data-stu-id="4b275-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="4b275-143">Utilisez la commande suivante pour générer tous les piles pour tous les threads du processus :</span><span class="sxs-lookup"><span data-stu-id="4b275-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="4b275-144">Une partie représentative de la sortie ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="4b275-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="4b275-145">En observant le piles pour les plus de 300 threads, vous affichez un modèle où la majorité des threads partagent une pile d’appels commune :</span><span class="sxs-lookup"><span data-stu-id="4b275-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="4b275-146">La pile d’appels semble montrer que la demande est arrivée dans notre méthode de blocage qui, à son tour, effectue un appel à `Monitor.ReliableEnter` .</span><span class="sxs-lookup"><span data-stu-id="4b275-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="4b275-147">Cette méthode indique que les threads essaient d’entrer dans un verrou de moniteur.</span><span class="sxs-lookup"><span data-stu-id="4b275-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="4b275-148">Ils sont en attente de la disponibilité du verrou.</span><span class="sxs-lookup"><span data-stu-id="4b275-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="4b275-149">Il est probablement verrouillé par un thread différent.</span><span class="sxs-lookup"><span data-stu-id="4b275-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="4b275-150">L’étape suivante consiste à déterminer le thread qui détient réellement le verrou du moniteur.</span><span class="sxs-lookup"><span data-stu-id="4b275-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="4b275-151">Étant donné que les analyses stockent généralement les informations de verrouillage dans la table des blocs de synchronisation, nous pouvons utiliser la `syncblk` commande pour obtenir plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="4b275-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="4b275-152">Les deux colonnes intéressantes sont **MonitorHeld** et **propriétaire des informations sur les threads**.</span><span class="sxs-lookup"><span data-stu-id="4b275-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="4b275-153">La colonne **MonitorHeld** indique si un verrou de moniteur est acquis par un thread et le nombre de threads en attente.</span><span class="sxs-lookup"><span data-stu-id="4b275-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="4b275-154">La colonne **informations sur le thread propriétaire** montre le thread qui possède actuellement le verrou du moniteur.</span><span class="sxs-lookup"><span data-stu-id="4b275-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="4b275-155">Les informations de thread ont trois sous-colonnes différentes.</span><span class="sxs-lookup"><span data-stu-id="4b275-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="4b275-156">La deuxième sous-colonne affiche l’ID du thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4b275-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="4b275-157">À ce stade, nous savons que deux threads différents (0x5634 et 0x51d4) maintiennent un verrou de moniteur.</span><span class="sxs-lookup"><span data-stu-id="4b275-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="4b275-158">L’étape suivante consiste à jeter un coup d’œil sur ce que font ces threads.</span><span class="sxs-lookup"><span data-stu-id="4b275-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="4b275-159">Nous devons vérifier s’ils sont bloqués indéfiniment sur le verrou.</span><span class="sxs-lookup"><span data-stu-id="4b275-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="4b275-160">Utilisons les `setthread` `clrstack` commandes et pour basculer vers chacun des threads et afficher le piles.</span><span class="sxs-lookup"><span data-stu-id="4b275-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="4b275-161">Pour examiner le premier thread, exécutez la `setthread` commande et recherchez l’index du thread 0x5634 (notre index était 28).</span><span class="sxs-lookup"><span data-stu-id="4b275-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="4b275-162">La fonction de blocage attend d’acquérir un verrou, mais elle détient déjà le verrou.</span><span class="sxs-lookup"><span data-stu-id="4b275-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="4b275-163">Il s’agit d’un blocage en attente du verrou qu’il détient déjà.</span><span class="sxs-lookup"><span data-stu-id="4b275-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="4b275-164">Le deuxième thread est similaire.</span><span class="sxs-lookup"><span data-stu-id="4b275-164">The second thread is similar.</span></span> <span data-ttu-id="4b275-165">Elle tente également d’acquérir un verrou qu’elle possède déjà.</span><span class="sxs-lookup"><span data-stu-id="4b275-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="4b275-166">Les 300 threads plus restants qui sont en attente sont généralement en attente de l’un des verrous ayant provoqué le blocage.</span><span class="sxs-lookup"><span data-stu-id="4b275-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b275-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b275-167">See also</span></span>

- <span data-ttu-id="4b275-168">[dotnet-trace](dotnet-trace.md) pour répertorier les processus</span><span class="sxs-lookup"><span data-stu-id="4b275-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="4b275-169">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée</span><span class="sxs-lookup"><span data-stu-id="4b275-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="4b275-170">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage</span><span class="sxs-lookup"><span data-stu-id="4b275-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="4b275-171">dotnet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="4b275-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="4b275-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4b275-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b275-173">Les outils de diagnostic disponibles dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b275-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
