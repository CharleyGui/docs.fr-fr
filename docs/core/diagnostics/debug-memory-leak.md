---
title: Didacticiel de débogage d’une fuite de mémoire
description: Découvrez comment déboguer une fuite de mémoire dans .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 7fa87a411606e81ffe91348c3cbce5f258a6e4e2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538590"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="f4d86-103">Déboguer une fuite de mémoire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4d86-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="f4d86-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f4d86-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="f4d86-105">Ce didacticiel présente les outils permettant d’analyser une fuite de mémoire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4d86-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="f4d86-106">Ce didacticiel utilise un exemple d’application, conçu pour une fuite de mémoire intentionnelle.</span><span class="sxs-lookup"><span data-stu-id="f4d86-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="f4d86-107">L’exemple est fourni en tant qu’exercice.</span><span class="sxs-lookup"><span data-stu-id="f4d86-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="f4d86-108">Vous pouvez analyser une application qui présente involontairement une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f4d86-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="f4d86-109">Ce didacticiel présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="f4d86-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f4d86-110">Examinez l’utilisation de la mémoire managée avec [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="f4d86-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="f4d86-111">Générez un fichier dump.</span><span class="sxs-lookup"><span data-stu-id="f4d86-111">Generate a dump file.</span></span>
> - <span data-ttu-id="f4d86-112">Analyser l’utilisation de la mémoire à l’aide du fichier dump.</span><span class="sxs-lookup"><span data-stu-id="f4d86-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4d86-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f4d86-113">Prerequisites</span></span>

<span data-ttu-id="f4d86-114">Le didacticiel utilise :</span><span class="sxs-lookup"><span data-stu-id="f4d86-114">The tutorial uses:</span></span>

- <span data-ttu-id="f4d86-115">[Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f4d86-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="f4d86-116">[dotnet-trace](dotnet-trace.md) pour répertorier les processus.</span><span class="sxs-lookup"><span data-stu-id="f4d86-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="f4d86-117">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="f4d86-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="f4d86-118">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage.</span><span class="sxs-lookup"><span data-stu-id="f4d86-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="f4d86-119">Exemple d’application [cible de débogage](/samples/dotnet/samples/diagnostic-scenarios/) à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="f4d86-119">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="f4d86-120">Ce didacticiel part du principe que l’exemple et les outils sont installés et prêts à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="f4d86-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="f4d86-121">Examiner l’utilisation de la mémoire managée</span><span class="sxs-lookup"><span data-stu-id="f4d86-121">Examine managed memory usage</span></span>

<span data-ttu-id="f4d86-122">Avant de commencer à collecter les données de diagnostics pour nous aider dans ce scénario, vous devez vous assurer que vous voyez une fuite de mémoire (croissance de la mémoire).</span><span class="sxs-lookup"><span data-stu-id="f4d86-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="f4d86-123">Vous pouvez utiliser l’outil [dotnet-Counters pour le](dotnet-counters.md) confirmer.</span><span class="sxs-lookup"><span data-stu-id="f4d86-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="f4d86-124">Ouvrez une fenêtre de console et accédez au répertoire où vous avez téléchargé et décompressé l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="f4d86-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="f4d86-125">Exécutez la cible :</span><span class="sxs-lookup"><span data-stu-id="f4d86-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="f4d86-126">À partir d’une console distincte, recherchez l’ID de processus à l’aide de l’outil [dotnet-trace](dotnet-trace.md) :</span><span class="sxs-lookup"><span data-stu-id="f4d86-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="f4d86-127">La sortie doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f4d86-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="f4d86-128">À présent, vérifiez l’utilisation de la mémoire managée avec l’outil [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="f4d86-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="f4d86-129">`--refresh-interval`Spécifie le nombre de secondes entre les actualisations :</span><span class="sxs-lookup"><span data-stu-id="f4d86-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="f4d86-130">La sortie dynamique doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f4d86-130">The live output should be similar to:</span></span>

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

<span data-ttu-id="f4d86-131">Se focaliser sur cette ligne :</span><span class="sxs-lookup"><span data-stu-id="f4d86-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="f4d86-132">Vous pouvez voir que la mémoire du tas managé est de 4 Mo juste après le démarrage.</span><span class="sxs-lookup"><span data-stu-id="f4d86-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="f4d86-133">À présent, cliquez sur l’URL `https://localhost:5001/api/diagscenario/memleak/20000` .</span><span class="sxs-lookup"><span data-stu-id="f4d86-133">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="f4d86-134">Notez que l’utilisation de la mémoire a augmenté jusqu’à 30 Mo.</span><span class="sxs-lookup"><span data-stu-id="f4d86-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="f4d86-135">En observant l’utilisation de la mémoire, vous pouvez en toute sécurité indiquer que la mémoire augmente ou subit une fuite.</span><span class="sxs-lookup"><span data-stu-id="f4d86-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="f4d86-136">L’étape suivante consiste à collecter les données appropriées pour l’analyse de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="f4d86-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="f4d86-137">Générer un vidage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="f4d86-137">Generate memory dump</span></span>

<span data-ttu-id="f4d86-138">Lors de l’analyse de fuites de mémoire possibles, vous devez accéder au segment de mémoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="f4d86-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="f4d86-139">Vous pouvez ensuite analyser le contenu de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="f4d86-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="f4d86-140">En examinant les relations entre les objets, vous créez des théories sur la raison pour laquelle la mémoire n’est pas libérée.</span><span class="sxs-lookup"><span data-stu-id="f4d86-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="f4d86-141">Une source de données de diagnostics courante est un vidage de la mémoire sur Windows ou le vidage de base équivalent sur Linux.</span><span class="sxs-lookup"><span data-stu-id="f4d86-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="f4d86-142">Pour générer un dump d’une application .NET Core, vous pouvez utiliser l’outil [dotnet-dump)](dotnet-dump.md) .</span><span class="sxs-lookup"><span data-stu-id="f4d86-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="f4d86-143">À l’aide de l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios/) précédemment démarré, exécutez la commande suivante pour générer un vidage Linux Core :</span><span class="sxs-lookup"><span data-stu-id="f4d86-143">Using the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="f4d86-144">Le résultat est un vidage central situé dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="f4d86-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="f4d86-145">Redémarrer le processus en échec</span><span class="sxs-lookup"><span data-stu-id="f4d86-145">Restart the failed process</span></span>

<span data-ttu-id="f4d86-146">Une fois le vidage collecté, vous devez disposer d’informations suffisantes pour diagnostiquer le processus en échec.</span><span class="sxs-lookup"><span data-stu-id="f4d86-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="f4d86-147">Si le processus en échec est en cours d’exécution sur un serveur de production, il s’agit de l’heure idéale pour la correction à terme, en redémarrant le processus.</span><span class="sxs-lookup"><span data-stu-id="f4d86-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="f4d86-148">Dans ce didacticiel, vous avez maintenant terminé l' [exemple de cible de débogage](/samples/dotnet/samples/diagnostic-scenarios/) et vous pouvez le fermer.</span><span class="sxs-lookup"><span data-stu-id="f4d86-148">In this tutorial, you're now done with the [Sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="f4d86-149">Accédez au terminal qui a démarré le serveur, puis appuyez sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f4d86-149">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="f4d86-150">Analyser le vidage principal</span><span class="sxs-lookup"><span data-stu-id="f4d86-150">Analyze the core dump</span></span>

<span data-ttu-id="f4d86-151">Maintenant que vous avez généré un vidage de base, utilisez l’outil [dotnet-dump](dotnet-dump.md) pour analyser le vidage :</span><span class="sxs-lookup"><span data-stu-id="f4d86-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="f4d86-152">Où `core_20190430_185145` est le nom de l’image de base que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="f4d86-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="f4d86-153">Si vous voyez une erreur indiquant que *libdl.so* est introuvable, vous devrez peut-être installer le package *libc6-dev* .</span><span class="sxs-lookup"><span data-stu-id="f4d86-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="f4d86-154">Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Linux](../install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="f4d86-154">For more information, see [Prerequisites for .NET Core on Linux](../install/linux.md).</span></span>

<span data-ttu-id="f4d86-155">Une invite s’affiche, dans laquelle vous pouvez entrer des commandes SOS.</span><span class="sxs-lookup"><span data-stu-id="f4d86-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="f4d86-156">En règle générale, la première chose que vous souhaitez examiner est l’état global du tas géré :</span><span class="sxs-lookup"><span data-stu-id="f4d86-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="f4d86-157">Ici, vous pouvez voir que la plupart des objets sont des `String` `Customer` objets ou.</span><span class="sxs-lookup"><span data-stu-id="f4d86-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="f4d86-158">Vous pouvez réutiliser la `dumpheap` commande à l’aide de la table de méthodes (MT) pour obtenir la liste de toutes les `String` instances :</span><span class="sxs-lookup"><span data-stu-id="f4d86-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="f4d86-159">Vous pouvez maintenant utiliser la `gcroot` commande sur une `System.String` instance pour voir comment et pourquoi l’objet est associé à une racine.</span><span class="sxs-lookup"><span data-stu-id="f4d86-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="f4d86-160">Soyez patient, car cette commande prend plusieurs minutes avec un segment de mémoire de 30 Mo :</span><span class="sxs-lookup"><span data-stu-id="f4d86-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="f4d86-161">Vous pouvez voir que `String` est directement détenu par l' `Customer` objet et détenu indirectement par un `CustomerCache` objet.</span><span class="sxs-lookup"><span data-stu-id="f4d86-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="f4d86-162">Vous pouvez continuer à vider les objets pour voir que la plupart des `String` objets suivent un modèle similaire.</span><span class="sxs-lookup"><span data-stu-id="f4d86-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="f4d86-163">À ce stade, l’investigation a fourni suffisamment d’informations pour identifier la cause racine de votre code.</span><span class="sxs-lookup"><span data-stu-id="f4d86-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="f4d86-164">Cette procédure générale vous permet d’identifier la source de fuites de mémoire majeures.</span><span class="sxs-lookup"><span data-stu-id="f4d86-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="f4d86-165">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="f4d86-165">Clean up resources</span></span>

<span data-ttu-id="f4d86-166">Dans ce didacticiel, vous avez démarré un exemple de serveur Web.</span><span class="sxs-lookup"><span data-stu-id="f4d86-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="f4d86-167">Ce serveur doit avoir été arrêté, comme expliqué dans la section [redémarrage de l’échec du processus](#restart-the-failed-process) .</span><span class="sxs-lookup"><span data-stu-id="f4d86-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="f4d86-168">Vous pouvez également supprimer le fichier dump qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="f4d86-168">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4d86-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4d86-169">See also</span></span>

- <span data-ttu-id="f4d86-170">[dotnet-trace](dotnet-trace.md) pour répertorier les processus</span><span class="sxs-lookup"><span data-stu-id="f4d86-170">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="f4d86-171">[dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée</span><span class="sxs-lookup"><span data-stu-id="f4d86-171">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="f4d86-172">[dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage</span><span class="sxs-lookup"><span data-stu-id="f4d86-172">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="f4d86-173">dotnet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="f4d86-173">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="f4d86-174">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f4d86-174">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4d86-175">Déboguer le processeur élevé dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4d86-175">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
