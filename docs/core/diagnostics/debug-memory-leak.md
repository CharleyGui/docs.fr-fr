---
title: Debug un tutoriel fuite de mémoire
description: Apprenez à déboiffer une fuite de mémoire dans .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737731"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="19443-103">Tutorial: Debug une fuite de mémoire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="19443-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="19443-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="19443-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="19443-105">Ce tutoriel démontre les outils pour analyser une fuite de mémoire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19443-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="19443-106">Ce tutoriel utilise une application d’échantillon, qui est conçu pour fuir intentionnellement la mémoire.</span><span class="sxs-lookup"><span data-stu-id="19443-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="19443-107">L’échantillon est fourni comme exercice.</span><span class="sxs-lookup"><span data-stu-id="19443-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="19443-108">Vous pouvez analyser une application qui fuit involontairement la mémoire aussi.</span><span class="sxs-lookup"><span data-stu-id="19443-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="19443-109">Ce didacticiel présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="19443-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="19443-110">Examinez l’utilisation gérée de la mémoire avec [des compteurs pointnet.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="19443-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="19443-111">Générer un fichier de décharge.</span><span class="sxs-lookup"><span data-stu-id="19443-111">Generate a dump file.</span></span>
> - <span data-ttu-id="19443-112">Analyser l’utilisation de la mémoire à l’aide du fichier de décharge.</span><span class="sxs-lookup"><span data-stu-id="19443-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19443-113">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="19443-113">Prerequisites</span></span>

<span data-ttu-id="19443-114">Le didacticiel utilise :</span><span class="sxs-lookup"><span data-stu-id="19443-114">The tutorial uses:</span></span>

- <span data-ttu-id="19443-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="19443-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="19443-116">[pointnet-trace](dotnet-trace.md) à la liste des processus.</span><span class="sxs-lookup"><span data-stu-id="19443-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="19443-117">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire gérée.</span><span class="sxs-lookup"><span data-stu-id="19443-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="19443-118">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de décharge.</span><span class="sxs-lookup"><span data-stu-id="19443-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="19443-119">Un [échantillon de débouger app cible](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="19443-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="19443-120">Le tutoriel suppose que l’échantillon et les outils sont installés et prêts à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="19443-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="19443-121">Examiner l’utilisation gérée de la mémoire</span><span class="sxs-lookup"><span data-stu-id="19443-121">Examine managed memory usage</span></span>

<span data-ttu-id="19443-122">Avant de commencer à collecter des données de diagnostic pour nous aider à provoquer ce scénario, vous devez vous assurer que vous voyez réellement une fuite de mémoire (croissance de la mémoire).</span><span class="sxs-lookup"><span data-stu-id="19443-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="19443-123">Vous pouvez utiliser l’outil [dotnet-counters](dotnet-counters.md) pour confirmer cela.</span><span class="sxs-lookup"><span data-stu-id="19443-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="19443-124">Ouvrez une fenêtre de console et naviguez vers l’annuaire où vous avez téléchargé et décompressé la [cible de débbug échantillon](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="19443-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="19443-125">Exécutez la cible :</span><span class="sxs-lookup"><span data-stu-id="19443-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="19443-126">À partir d’une console séparée, trouvez l’ID du processus à l’aide de l’outil [dotnet-trace](dotnet-trace.md) :</span><span class="sxs-lookup"><span data-stu-id="19443-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="19443-127">La sortie doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="19443-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="19443-128">Maintenant, vérifiez l’utilisation gérée de mémoire avec [l’outil dotnet-counters.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="19443-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="19443-129">Le `--refresh-interval` spécifie le nombre de secondes entre les rafraîchissements:</span><span class="sxs-lookup"><span data-stu-id="19443-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="19443-130">La production en direct devrait être similaire à :</span><span class="sxs-lookup"><span data-stu-id="19443-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="19443-131">En se concentrant sur cette ligne:</span><span class="sxs-lookup"><span data-stu-id="19443-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="19443-132">Vous pouvez voir que la mémoire de tas géré est de 4 Mo juste après le démarrage.</span><span class="sxs-lookup"><span data-stu-id="19443-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="19443-133">Maintenant, appuyez `http://localhost:5000/api/diagscenario/memleak/20000`sur l’URL .</span><span class="sxs-lookup"><span data-stu-id="19443-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="19443-134">Observez que l’utilisation de la mémoire est passée à 30 Mo.</span><span class="sxs-lookup"><span data-stu-id="19443-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="19443-135">En regardant l’utilisation de la mémoire, vous pouvez dire en toute sécurité que la mémoire est de plus en plus ou de fuite.</span><span class="sxs-lookup"><span data-stu-id="19443-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="19443-136">L’étape suivante consiste à recueillir les bonnes données pour l’analyse de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="19443-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="19443-137">Générer un dépotoir de mémoire</span><span class="sxs-lookup"><span data-stu-id="19443-137">Generate memory dump</span></span>

<span data-ttu-id="19443-138">Lors de l’analyse des fuites de mémoire possibles, vous devez accéder au tas de mémoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="19443-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="19443-139">Ensuite, vous pouvez analyser le contenu de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="19443-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="19443-140">En regardant les relations entre les objets, vous créez des théories sur les raisons pour lesquelles la mémoire n’est pas libérée.</span><span class="sxs-lookup"><span data-stu-id="19443-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="19443-141">Une source de données diagnostiques courante est un dépotoir de mémoire sur Windows ou le décharge de base équivalent sur Linux.</span><span class="sxs-lookup"><span data-stu-id="19443-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="19443-142">Pour générer un dépotoir d’une application .NET Core, vous pouvez utiliser l’outil [dotnet-dump).](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="19443-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="19443-143">À l’aide de la [cible de débaillement de l’échantillon](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) précédemment commencée, exécutez la commande suivante pour générer un décharge de base Linux :</span><span class="sxs-lookup"><span data-stu-id="19443-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="19443-144">Le résultat est un décharge de base situé dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="19443-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="19443-145">Redémarrer le processus défaillant</span><span class="sxs-lookup"><span data-stu-id="19443-145">Restart the failed process</span></span>

<span data-ttu-id="19443-146">Une fois que le dépotoir est recueilli, vous devriez avoir suffisamment d’informations pour diagnostiquer le processus défectueus.</span><span class="sxs-lookup"><span data-stu-id="19443-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="19443-147">Si le processus défaillant s’exécute sur un serveur de production, c’est maintenant le moment idéal pour l’assainissement à court terme en redémarrant le processus.</span><span class="sxs-lookup"><span data-stu-id="19443-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="19443-148">Dans ce tutoriel, vous avez maintenant terminé avec la [cible de débogé d’échantillons](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) et vous pouvez le fermer.</span><span class="sxs-lookup"><span data-stu-id="19443-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="19443-149">Naviguez vers le terminal qui `Control-C`a commencé le serveur et appuyez .</span><span class="sxs-lookup"><span data-stu-id="19443-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="19443-150">Analyser le dépotoir de base</span><span class="sxs-lookup"><span data-stu-id="19443-150">Analyze the core dump</span></span>

<span data-ttu-id="19443-151">Maintenant que vous avez un décharge de base généré, utilisez [l’outil dotnet-dump)](dotnet-dump.md) pour analyser le dépotoir :</span><span class="sxs-lookup"><span data-stu-id="19443-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="19443-152">Où `core_20190430_185145` est le nom de la décharge de base que vous voulez analyser.</span><span class="sxs-lookup"><span data-stu-id="19443-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="19443-153">Si vous voyez une erreur se plaindre que *libdl.so* ne peut pas être trouvé, vous devrez peut-être installer le paquet *libc6-dev.*</span><span class="sxs-lookup"><span data-stu-id="19443-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="19443-154">Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Linux](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="19443-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="19443-155">Vous serez présenté avec une invite où vous pouvez entrer les commandes SOS.</span><span class="sxs-lookup"><span data-stu-id="19443-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="19443-156">Généralement, la première chose que vous voulez regarder est l’état global du tas géré:</span><span class="sxs-lookup"><span data-stu-id="19443-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="19443-157">Ici, vous pouvez voir `String` que `Customer` la plupart des objets sont soit ou des objets.</span><span class="sxs-lookup"><span data-stu-id="19443-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="19443-158">Vous pouvez `dumpheap` utiliser la commande à nouveau avec la table `String` de méthode (MT) pour obtenir une liste de tous les cas:</span><span class="sxs-lookup"><span data-stu-id="19443-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="19443-159">Vous pouvez maintenant `gcroot` utiliser `System.String` la commande sur une instance pour voir comment et pourquoi l’objet est enraciné.</span><span class="sxs-lookup"><span data-stu-id="19443-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="19443-160">Soyez patient car cette commande prend plusieurs minutes avec un tas de 30 Mo :</span><span class="sxs-lookup"><span data-stu-id="19443-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="19443-161">Vous pouvez voir `String` que le `Customer` est directement détenu par `CustomerCache` l’objet et indirectement détenu par un objet.</span><span class="sxs-lookup"><span data-stu-id="19443-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="19443-162">Vous pouvez continuer à jeter `String` des objets pour voir que la plupart des objets suivent un modèle similaire.</span><span class="sxs-lookup"><span data-stu-id="19443-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="19443-163">À ce stade, l’enquête a fourni suffisamment d’informations pour identifier la cause profonde de votre code.</span><span class="sxs-lookup"><span data-stu-id="19443-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="19443-164">Cette procédure générale vous permet d’identifier la source des principales fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="19443-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="19443-165">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="19443-165">Clean up resources</span></span>

<span data-ttu-id="19443-166">Dans ce tutoriel, vous avez lancé un exemple de serveur web.</span><span class="sxs-lookup"><span data-stu-id="19443-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="19443-167">Ce serveur aurait dû être arrêté comme expliqué dans le redémarrage de la section [processus a échoué.](#restart-the-failed-process)</span><span class="sxs-lookup"><span data-stu-id="19443-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="19443-168">Vous pouvez également supprimer le fichier de décharge qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="19443-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19443-169">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="19443-169">Next steps</span></span>

<span data-ttu-id="19443-170">Félicitations pour avoir terminé ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="19443-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="19443-171">Nous publions encore plus de tutoriels diagnostiques.</span><span class="sxs-lookup"><span data-stu-id="19443-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="19443-172">Vous pouvez lire les versions provisoires sur le référentiel [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)</span><span class="sxs-lookup"><span data-stu-id="19443-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="19443-173">Ce tutoriel a couvert les bases des outils de diagnostic .NET clés.</span><span class="sxs-lookup"><span data-stu-id="19443-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="19443-174">Pour une utilisation avancée, consultez la documentation de référence suivante :</span><span class="sxs-lookup"><span data-stu-id="19443-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="19443-175">[pointnet-trace](dotnet-trace.md) à la liste des processus.</span><span class="sxs-lookup"><span data-stu-id="19443-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="19443-176">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire gérée.</span><span class="sxs-lookup"><span data-stu-id="19443-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="19443-177">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de décharge.</span><span class="sxs-lookup"><span data-stu-id="19443-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
