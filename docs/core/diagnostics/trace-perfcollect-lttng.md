---
title: Suivi des applications .NET avec PerfCollect.
description: Un didacticiel qui vous guide dans la collecte d’une trace avec perfcollect dans .NET.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 376c957833924a9991e574557671ea3c8503d7c2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507239"
---
# <a name="trace-net-applications-with-perfcollect"></a><span data-ttu-id="486dd-103">Suivre des applications .NET avec PerfCollect</span><span class="sxs-lookup"><span data-stu-id="486dd-103">Trace .NET applications with PerfCollect</span></span>

<span data-ttu-id="486dd-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="486dd-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="486dd-105">En cas de problèmes de performances sur Linux, la collecte d’une trace avec `perfcollect` peut être utilisée pour collecter des informations détaillées sur ce qui se passe sur l’ordinateur au moment du problème de performances.</span><span class="sxs-lookup"><span data-stu-id="486dd-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="486dd-106">`perfcollect` est un script bash qui tire parti de la [LTTng (tracing Tookit-Next Generation) de Linux](https://lttng.org) pour collecter des événements écrits à partir du runtime ou de n’importe quelle [EventSource](xref:System.Diagnostics.Tracing.EventListener), ainsi que des [performances](https://perf.wiki.kernel.org/) pour collecter des exemples d’UC du processus cible.</span><span class="sxs-lookup"><span data-stu-id="486dd-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="prepare-your-machine"></a><span data-ttu-id="486dd-107">Préparer votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="486dd-107">Prepare your machine</span></span>

<span data-ttu-id="486dd-108">Procédez comme suit pour préparer votre ordinateur à la collecte d’un suivi des performances avec `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="486dd-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="486dd-109">Si vous êtes dans un environnement de conteneur, votre conteneur doit avoir une `SYS_ADMIN` capacité.</span><span class="sxs-lookup"><span data-stu-id="486dd-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="486dd-110">Pour plus d’informations sur le suivi des applications dans des conteneurs à l’aide de PerfCollect, consultez [collecter des diagnostics dans des conteneurs](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="486dd-110">For more information on tracing applications inside containers using PerfCollect, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

1. <span data-ttu-id="486dd-111">Téléchargez `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="486dd-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="486dd-112">Rendez le script exécutable.</span><span class="sxs-lookup"><span data-stu-id="486dd-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="486dd-113">Installer la configuration requise pour le suivi : il s’agit des bibliothèques de suivi réelles.</span><span class="sxs-lookup"><span data-stu-id="486dd-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="486dd-114">Cette opération installe les composants requis suivants sur votre ordinateur :</span><span class="sxs-lookup"><span data-stu-id="486dd-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="486dd-115">`perf`: le sous-système d’événements de performances Linux et l’application de collecte/visionneuse en mode utilisateur associée.</span><span class="sxs-lookup"><span data-stu-id="486dd-115">`perf`: the Linux Performance Events subsystem and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="486dd-116">`perf` fait partie de la source du noyau Linux, mais n’est généralement pas installé par défaut.</span><span class="sxs-lookup"><span data-stu-id="486dd-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="486dd-117">`LTTng`: Utilisé pour capturer les données d’événement émises lors de l’exécution par CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="486dd-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="486dd-118">Ces données sont ensuite utilisées pour analyser le comportement de différents composants du runtime, tels que le catalogue global, le JIT et le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="486dd-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT, and thread pool.</span></span>

<span data-ttu-id="486dd-119">Les versions récentes de .NET Core et de l’outil de performances Linux prennent en charge la résolution automatique des noms de méthode pour le code du Framework.</span><span class="sxs-lookup"><span data-stu-id="486dd-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="486dd-120">Si vous utilisez la version 3,1 ou une version antérieure de .NET Core, une étape supplémentaire est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="486dd-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="486dd-121">Pour plus d’informations, consultez [résolution des symboles de Framework](#resolve-framework-symbols) .</span><span class="sxs-lookup"><span data-stu-id="486dd-121">See [Resolving Framework Symbols](#resolve-framework-symbols) for details.</span></span>

<span data-ttu-id="486dd-122">Pour résoudre les noms de méthode des dll du runtime natif (par exemple, libcoreclr.so), `perfcollect` résoudra les symboles pour eux lors de la conversion des données, mais uniquement si les symboles de ces fichiers binaires sont présents.</span><span class="sxs-lookup"><span data-stu-id="486dd-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="486dd-123">Pour plus d’informations, consultez [obtention de symboles pour la section du runtime natif](#get-symbols-for-the-native-runtime) .</span><span class="sxs-lookup"><span data-stu-id="486dd-123">See [Getting Symbols for the Native Runtime](#get-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collect-a-trace"></a><span data-ttu-id="486dd-124">Collecter une trace</span><span class="sxs-lookup"><span data-stu-id="486dd-124">Collect a trace</span></span>

1. <span data-ttu-id="486dd-125">Deux interpréteurs de commande disponibles : un pour contrôler le suivi, désigné sous le terme **[trace]** , et l’autre pour l’exécution de l’application, appelé **[App]**.</span><span class="sxs-lookup"><span data-stu-id="486dd-125">Have two shells available - one for controlling tracing, referred to as **[Trace]** , and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="486dd-126">**[Trace]** Démarrer la collecte.</span><span class="sxs-lookup"><span data-stu-id="486dd-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="486dd-127">Sortie attendue :</span><span class="sxs-lookup"><span data-stu-id="486dd-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="486dd-128">**[Application]** Configurez l’interpréteur de commandes de l’application avec les variables d’environnement suivantes : cela permet la configuration du suivi de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="486dd-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="486dd-129">**[Application]** Exécutez l’application : laissez-la s’exécuter aussi longtemps que nécessaire pour capturer le problème de performances.</span><span class="sxs-lookup"><span data-stu-id="486dd-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="486dd-130">La longueur exacte peut être aussi brève que nécessaire, à condition qu’elle capture suffisamment de temps pour que le problème de performances que vous souhaitez examiner se produise.</span><span class="sxs-lookup"><span data-stu-id="486dd-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="486dd-131">**[Trace]** Arrêter la collecte-Appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="486dd-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    <span data-ttu-id="486dd-132">Le fichier de trace compressé est maintenant stocké dans le répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="486dd-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="486dd-133">Afficher une trace</span><span class="sxs-lookup"><span data-stu-id="486dd-133">View a trace</span></span>

<span data-ttu-id="486dd-134">Il existe un certain nombre d’options pour l’affichage de la trace qui a été collectée.</span><span class="sxs-lookup"><span data-stu-id="486dd-134">There are a number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="486dd-135">Les traces sont mieux affichées à l’aide de [PerfView](https://aka.ms/perfview) sur Windows, mais elles peuvent être consultées directement sur Linux à l’aide de `PerfCollect` ou de `TraceCompass` .</span><span class="sxs-lookup"><span data-stu-id="486dd-135">Traces are best viewed using [PerfView](https://aka.ms/perfview) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="use-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="486dd-136">Utiliser PerfCollect pour afficher le fichier de trace</span><span class="sxs-lookup"><span data-stu-id="486dd-136">Use PerfCollect to view the trace file</span></span>

<span data-ttu-id="486dd-137">Vous pouvez utiliser perfcollect pour afficher le suivi que vous avez collecté.</span><span class="sxs-lookup"><span data-stu-id="486dd-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="486dd-138">Pour ce faire, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="486dd-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="486dd-139">Par défaut, cette option affiche le suivi de l’UC de l’application à l’aide de `perf` .</span><span class="sxs-lookup"><span data-stu-id="486dd-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="486dd-140">Pour examiner les événements collectés par le biais de `LTTng` , vous pouvez transmettre l’indicateur `-viewer lttng` pour voir les événements individuels :</span><span class="sxs-lookup"><span data-stu-id="486dd-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="486dd-141">Cette opération utilise `babeltrace` la visionneuse pour imprimer la charge utile des événements :</span><span class="sxs-lookup"><span data-stu-id="486dd-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a><span data-ttu-id="486dd-142">Utiliser PerfView pour ouvrir le fichier de trace</span><span class="sxs-lookup"><span data-stu-id="486dd-142">Use PerfView to open the trace file</span></span>

<span data-ttu-id="486dd-143">Pour afficher une vue agrégée de l’exemple de processeur et des événements, vous pouvez utiliser `PerfView` sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="486dd-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="486dd-144">Copiez le fichier trace.zip de Linux sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="486dd-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="486dd-145">Téléchargez PerfView à partir de <https://aka.ms/perfview> .</span><span class="sxs-lookup"><span data-stu-id="486dd-145">Download PerfView from <https://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="486dd-146">Exécuter PerfView.exe</span><span class="sxs-lookup"><span data-stu-id="486dd-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="486dd-147">PerfView affiche la liste des vues prises en charge en fonction des données contenues dans le fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="486dd-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="486dd-148">Pour les investigations du processeur, choisissez piles de l' **UC**.</span><span class="sxs-lookup"><span data-stu-id="486dd-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="486dd-149">Pour obtenir des informations détaillées sur le catalogue global, choisissez **GCStats**.</span><span class="sxs-lookup"><span data-stu-id="486dd-149">For detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="486dd-150">Pour les informations JIT par processus/module/méthode, choisissez **JITStats**.</span><span class="sxs-lookup"><span data-stu-id="486dd-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="486dd-151">S’il n’existe pas d’affichage pour les informations dont vous avez besoin, vous pouvez essayer de rechercher les événements dans la vue événements bruts.</span><span class="sxs-lookup"><span data-stu-id="486dd-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="486dd-152">Choisissez **événements**.</span><span class="sxs-lookup"><span data-stu-id="486dd-152">Choose **Events**.</span></span>

<span data-ttu-id="486dd-153">Pour plus d’informations sur la façon d’interpréter des affichages dans PerfView, consultez liens d’aide dans la vue elle-même, ou dans la fenêtre principale de PerfView, choisissez **aide->Guide des utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="486dd-153">For more information on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView, choose **Help->Users Guide**.</span></span>

### <a name="use-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="486dd-154">Utiliser TraceCompass pour ouvrir le fichier de trace</span><span class="sxs-lookup"><span data-stu-id="486dd-154">Use TraceCompass to open the trace file</span></span>

<span data-ttu-id="486dd-155">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) est une autre option que vous pouvez utiliser pour afficher les traces.</span><span class="sxs-lookup"><span data-stu-id="486dd-155">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you can use to view the traces.</span></span> <span data-ttu-id="486dd-156">`TraceCompass` fonctionne également sur les machines Linux. vous n’avez donc pas besoin de déplacer votre suivi vers un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="486dd-156">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="486dd-157">Pour utiliser `TraceCompass` pour ouvrir votre fichier de trace, vous devez décompresser le fichier.</span><span class="sxs-lookup"><span data-stu-id="486dd-157">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="486dd-158">`perfcollect` enregistre le suivi LTTng collecté dans un format de fichier CTF dans un sous-répertoire du `lttngTrace` .</span><span class="sxs-lookup"><span data-stu-id="486dd-158">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="486dd-159">Plus précisément, le fichier CTF se trouve dans un répertoire qui ressemble à `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` .</span><span class="sxs-lookup"><span data-stu-id="486dd-159">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="486dd-160">Vous pouvez ouvrir le fichier de trace CTF dans `TraceCompass` en sélectionnant et en sélectionnant `File -> Open Trace` le `metadata` fichier.</span><span class="sxs-lookup"><span data-stu-id="486dd-160">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="486dd-161">Pour plus d’informations, consultez [ `TraceCompass` la documentation](https://www.eclipse.org/tracecompass/).</span><span class="sxs-lookup"><span data-stu-id="486dd-161">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolve-framework-symbols"></a><span data-ttu-id="486dd-162">Résoudre les symboles Framework</span><span class="sxs-lookup"><span data-stu-id="486dd-162">Resolve framework symbols</span></span>

<span data-ttu-id="486dd-163">Les symboles de Framework doivent être générés manuellement au moment de la collecte de la trace.</span><span class="sxs-lookup"><span data-stu-id="486dd-163">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="486dd-164">Elles sont différentes des symboles au niveau de l’application, car l’infrastructure est précompilée, tandis que le code de l’application est compilé juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="486dd-164">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="486dd-165">Pour le code d’infrastructure qui a été précompilé en code natif, vous devez appeler `crossgen` qui sait comment générer le mappage du code natif au nom des méthodes.</span><span class="sxs-lookup"><span data-stu-id="486dd-165">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="486dd-166">`perfcollect` peut gérer la plupart des détails pour vous, mais il doit être `crossgen` disponible.</span><span class="sxs-lookup"><span data-stu-id="486dd-166">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="486dd-167">Par défaut, il n’est pas installé avec la distribution .NET.</span><span class="sxs-lookup"><span data-stu-id="486dd-167">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="486dd-168">Si `crossgen` n’y figure pas, `perfcollect` vous avertit et vous renvoie à ces instructions.</span><span class="sxs-lookup"><span data-stu-id="486dd-168">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="486dd-169">Pour résoudre les problèmes, vous devez récupérer exactement la version appropriée de CrossGen pour le runtime que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="486dd-169">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="486dd-170">Si vous placez l’outil CrossGen dans le même répertoire que les dll du Runtime .NET (par exemple, libcoreclr.so), `perfcollect` vous pouvez le trouver et ajouter les symboles d’infrastructure au fichier de trace pour vous.</span><span class="sxs-lookup"><span data-stu-id="486dd-170">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (for example, libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="486dd-171">Normalement, lorsque vous créez une application .NET, elle génère simplement la DLL du code que vous avez écrit, à l’aide d’une copie partagée du runtime pour le Rest.</span><span class="sxs-lookup"><span data-stu-id="486dd-171">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="486dd-172">Toutefois, vous pouvez également générer une version appelée « autonome » d’une application qui contient toutes les dll d’exécution.</span><span class="sxs-lookup"><span data-stu-id="486dd-172">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="486dd-173">`crossgen` fait partie du package NuGet utilisé pour créer des applications autonomes. par conséquent, pour obtenir la version appropriée de, vous pouvez `crossgen` créer un package autonome de votre application.</span><span class="sxs-lookup"><span data-stu-id="486dd-173">`crossgen` is part of the NuGet package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="486dd-174">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="486dd-174">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="486dd-175">Cela crée une application Hello World et la génère comme une application autonome.</span><span class="sxs-lookup"><span data-stu-id="486dd-175">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="486dd-176">En tant qu’effet secondaire de la création de l’application autonome, l’outil dotnet télécharge un package NuGet appelé Runtime. Linux-x64. Microsoft. Netcore. app et le place dans le répertoire ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, où VERSION correspond au numéro de version de votre Runtime .NET Core (par exemple, 2.1.0).</span><span class="sxs-lookup"><span data-stu-id="486dd-176">As a side effect of creating the self-contained application the dotnet tool will download a NuGet package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (for example, 2.1.0).</span></span> <span data-ttu-id="486dd-177">Sous, il s’agit d’un répertoire d’outils et l’outil CrossGen dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="486dd-177">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="486dd-178">À compter de .NET Core 3,0, l’emplacement du package est ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span><span class="sxs-lookup"><span data-stu-id="486dd-178">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="486dd-179">L' `crossgen` outil doit être placé en regard du runtime qui est réellement utilisé par votre application.</span><span class="sxs-lookup"><span data-stu-id="486dd-179">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="486dd-180">En général, votre application utilise la version partagée de .NET Core qui est installée sur/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION où VERSION est le numéro de version du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="486dd-180">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="486dd-181">Il s’agit d’un emplacement partagé. vous devez donc être super utilisateur pour le modifier.</span><span class="sxs-lookup"><span data-stu-id="486dd-181">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="486dd-182">Si la VERSION est 2.1.0, les commandes à mettre à jour `crossgen` sont :</span><span class="sxs-lookup"><span data-stu-id="486dd-182">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="486dd-183">Une fois que vous avez effectué cette opération, `perfcollect` utilise CrossGen pour inclure les symboles de Framework.</span><span class="sxs-lookup"><span data-stu-id="486dd-183">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="486dd-184">L’avertissement qui a été `perfcollect` utilisé pour émettre doit disparaître.</span><span class="sxs-lookup"><span data-stu-id="486dd-184">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="486dd-185">Il ne doit y avoir qu’une seule fois par ordinateur (jusqu’à ce que vous ayez mis à jour votre Runtime).</span><span class="sxs-lookup"><span data-stu-id="486dd-185">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="486dd-186">Alternative : désactiver l’utilisation du code précompilé</span><span class="sxs-lookup"><span data-stu-id="486dd-186">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="486dd-187">Si vous n’avez pas la possibilité de mettre à jour le Runtime .NET (à ajouter `crossgen` ), ou si la procédure ci-dessus ne fonctionnait pas pour une raison quelconque, il existe une autre approche pour obtenir les symboles de Framework.</span><span class="sxs-lookup"><span data-stu-id="486dd-187">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="486dd-188">Vous pouvez indiquer au runtime de ne pas utiliser simplement le code d’infrastructure précompilé.</span><span class="sxs-lookup"><span data-stu-id="486dd-188">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="486dd-189">Le code sera compilé juste-à-temps et `crossgen` n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="486dd-189">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="486dd-190">Le choix de cette approche peut augmenter le temps de démarrage de votre application.</span><span class="sxs-lookup"><span data-stu-id="486dd-190">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="486dd-191">Pour ce faire, vous pouvez ajouter la variable d’environnement suivante :</span><span class="sxs-lookup"><span data-stu-id="486dd-191">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="486dd-192">Avec cette modification, vous devez obtenir les symboles de tout le code .NET.</span><span class="sxs-lookup"><span data-stu-id="486dd-192">With this change, you should get the symbols for all .NET code.</span></span>

## <a name="get-symbols-for-the-native-runtime"></a><span data-ttu-id="486dd-193">Obtenir des symboles pour le runtime natif</span><span class="sxs-lookup"><span data-stu-id="486dd-193">Get symbols for the native runtime</span></span>

<span data-ttu-id="486dd-194">La plupart du temps, vous êtes intéressé par votre propre code, qui est `perfcollect` résolu par défaut.</span><span class="sxs-lookup"><span data-stu-id="486dd-194">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="486dd-195">Il est parfois utile de voir ce qui se passe à l’intérieur des dll .NET (ce que fait la dernière section), mais parfois ce qui se passe dans les dll du runtime natif (généralement libcoreclr.so), est intéressant.</span><span class="sxs-lookup"><span data-stu-id="486dd-195">Sometimes it is useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="486dd-196">`perfcollect` résoudra les symboles pour ceux-ci lorsqu’il convertit ses données, mais uniquement si les symboles de ces DLL natives sont présents (et sont en regard de la bibliothèque à laquelle ils sont destinés).</span><span class="sxs-lookup"><span data-stu-id="486dd-196">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="486dd-197">Il existe une commande globale appelée [dotnet-Symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) qui le fait.</span><span class="sxs-lookup"><span data-stu-id="486dd-197">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) that does this.</span></span> <span data-ttu-id="486dd-198">Pour utiliser dotnet-Symbol afin d’accéder aux symboles natifs du Runtime :</span><span class="sxs-lookup"><span data-stu-id="486dd-198">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="486dd-199">Installez `dotnet-symbol` :</span><span class="sxs-lookup"><span data-stu-id="486dd-199">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="486dd-200">Téléchargez les symboles.</span><span class="sxs-lookup"><span data-stu-id="486dd-200">Download the symbols.</span></span> <span data-ttu-id="486dd-201">Si votre version installée du Runtime .NET Core est 2.1.0, la commande permettant d’effectuer cette opération est la suivante :</span><span class="sxs-lookup"><span data-stu-id="486dd-201">If your installed version of the .NET Core runtime is 2.1.0, the command to do this is:</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="486dd-202">Copiez les symboles à l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="486dd-202">Copy the symbols to the correct place.</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="486dd-203">Si cela ne peut pas être fait parce que vous n’avez pas accès en écriture au répertoire approprié, vous pouvez utiliser `perf buildid-cache` pour ajouter les symboles.</span><span class="sxs-lookup"><span data-stu-id="486dd-203">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="486dd-204">Après cela, vous devez obtenir des noms symboliques pour les DLL natives lorsque vous exécutez `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="486dd-204">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collect-in-a-docker-container"></a><span data-ttu-id="486dd-205">Collecter dans un conteneur d’ancrage</span><span class="sxs-lookup"><span data-stu-id="486dd-205">Collect in a Docker container</span></span>

<span data-ttu-id="486dd-206">Pour plus d’informations sur l’utilisation `perfcollect` de dans les environnements de conteneur, consultez [collecter des diagnostics dans des conteneurs](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="486dd-206">For more information on how to use `perfcollect` in container environments, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>
