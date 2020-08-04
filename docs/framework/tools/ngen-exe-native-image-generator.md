---
title: Ngen.exe (Native Image Generator)
description: Passez en revue Ngen.exe, le générateur d’images natives. Améliorez les performances des applications managées en créant des images natives et en les installant dans le cache d’images natives local.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: ae86aed773a9a13f102b1ad111cac5a3ee563508
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517267"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="d9307-104">Ngen.exe (Native Image Generator)</span><span class="sxs-lookup"><span data-stu-id="d9307-104">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="d9307-105">L'outil Native Image Generator Tool (Ngen.exe) est un outil qui améliore les performances des applications managées.</span><span class="sxs-lookup"><span data-stu-id="d9307-105">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="d9307-106">Ngen.exe crée des images natives, qui sont des fichiers contenant le code machine compilé spécifique au processeur, et les installe dans le cache des images natives sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d9307-106">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="d9307-107">Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.</span><span class="sxs-lookup"><span data-stu-id="d9307-107">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-108">Ngen.exe compile les images natives pour les assemblys qui ciblent le .NET Framework uniquement.</span><span class="sxs-lookup"><span data-stu-id="d9307-108">Ngen.exe compiles native images for assemblies that target the .NET Framework only.</span></span> <span data-ttu-id="d9307-109">Le générateur d’images natives équivalent pour .NET Core est [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).</span><span class="sxs-lookup"><span data-stu-id="d9307-109">The equivalent native image generator for .NET Core is [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).</span></span>

<span data-ttu-id="d9307-110">Modifications apportées à Ngen.exe dans .NET Framework 4 :</span><span class="sxs-lookup"><span data-stu-id="d9307-110">Changes to Ngen.exe in the .NET Framework 4:</span></span>

- <span data-ttu-id="d9307-111">Ngen.exe compile maintenant des assemblys avec une confiance totale et la stratégie de sécurité d'accès du code (CAS) n'est plus évaluée.</span><span class="sxs-lookup"><span data-stu-id="d9307-111">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="d9307-112">Les images natives générées avec Ngen.exe ne peuvent plus être chargées dans les applications qui s'exécutent avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="d9307-112">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="d9307-113">Modifications apportées à Ngen.exe dans le .NET Framework version 2.0 :</span><span class="sxs-lookup"><span data-stu-id="d9307-113">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="d9307-114">L'installation d'un assembly installe également ses dépendances, en simplifiant la syntaxe de Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-114">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="d9307-115">Les images natives peuvent maintenant être partagées entre les domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-115">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="d9307-116">Une nouvelle action, `update`, recrée des images qui ont été invalidées.</span><span class="sxs-lookup"><span data-stu-id="d9307-116">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="d9307-117">L'exécution des actions peuvent être différées par un service qui utilise la durée d'inactivité de l'ordinateur pour générer et installer des images.</span><span class="sxs-lookup"><span data-stu-id="d9307-117">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="d9307-118">Certaines causes d'invalidation d'images ont été éliminées.</span><span class="sxs-lookup"><span data-stu-id="d9307-118">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="d9307-119">Sur Windows 8, consultez [Tâche d’image native](#native-image-task).</span><span class="sxs-lookup"><span data-stu-id="d9307-119">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="d9307-120">Pour plus d’informations sur l’utilisation de Ngen.exe et du service d’images natives, consultez [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-120">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-121">Vous trouverez la syntaxe de Ngen.exe pour les versions 1.0 et 1.1 du .NET Framework dans [Syntaxe héritée du générateur d’images natives (Ngen.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d9307-121">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="d9307-122">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9307-122">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="d9307-123">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="d9307-123">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d9307-124">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d9307-124">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="d9307-125">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d9307-125">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="d9307-126">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9307-126">Syntax</span></span>

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="d9307-127">Actions</span><span class="sxs-lookup"><span data-stu-id="d9307-127">Actions</span></span>

<span data-ttu-id="d9307-128">Le tableau ci-après décrit la syntaxe de chaque `action`.</span><span class="sxs-lookup"><span data-stu-id="d9307-128">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="d9307-129">Pour obtenir une description de chaque partie d’une `action`, consultez les tableaux [Arguments](#ArgumentTable), [Niveaux de priorité](#PriorityTable), [Scénarios](#ScenarioTable) et [Config](#ConfigTable).</span><span class="sxs-lookup"><span data-stu-id="d9307-129">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="d9307-130">Le tableau [Options](#OptionTable) décrit les `options` et les commutateurs d'aide.</span><span class="sxs-lookup"><span data-stu-id="d9307-130">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="d9307-131">Action</span><span class="sxs-lookup"><span data-stu-id="d9307-131">Action</span></span>|<span data-ttu-id="d9307-132">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-132">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="d9307-133">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="d9307-133">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="d9307-134">Générer des images natives pour un assembly et ses dépendances et installer les images dans le cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-134">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="d9307-135">Si `/queue` est spécifié, l'action est mise en file d'attente pour le service d'images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-135">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="d9307-136">La priorité par défaut est 3.</span><span class="sxs-lookup"><span data-stu-id="d9307-136">The default priority is 3.</span></span> <span data-ttu-id="d9307-137">Consultez le tableau [Niveaux de priorité](#PriorityTable).</span><span class="sxs-lookup"><span data-stu-id="d9307-137">See the [Priority Levels](#PriorityTable) table.</span></span>|
|<span data-ttu-id="d9307-138">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="d9307-138">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="d9307-139">Supprimer les images natives d'un assembly et ses dépendances du cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-139">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="d9307-140">Pour désinstaller une seule image et ses dépendances, utilisez les mêmes arguments de ligne de commande que ceux utilisés pour installer l’image.</span><span class="sxs-lookup"><span data-stu-id="d9307-140">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="d9307-141">**Remarque :**  À partir du .NET Framework 4, l’action `uninstall` \* n’est plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="d9307-141">**Note:**  Starting with the .NET Framework 4, the action `uninstall` \* is no longer supported.</span></span>|
|<span data-ttu-id="d9307-142">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="d9307-142">`update` [`/queue`]</span></span>|<span data-ttu-id="d9307-143">Mettre à jour des images natives qui sont devenues non valides.</span><span class="sxs-lookup"><span data-stu-id="d9307-143">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="d9307-144">Si `/queue` est spécifié, les mises à jour sont mises en file d'attente pour le service d'images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-144">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="d9307-145">Les mises à jour sont toujours planifiées à la priorité 3, de sorte qu'elles s'exécutent lorsque l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-145">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|<span data-ttu-id="d9307-146">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="d9307-146">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="d9307-147">Afficher l'état des images natives pour un assembly et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="d9307-147">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="d9307-148">Si aucun argument n’est fourni, tout dans le cache des images natives est affiché.</span><span class="sxs-lookup"><span data-stu-id="d9307-148">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|<span data-ttu-id="d9307-149">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="d9307-149">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="d9307-150">-ou-</span><span class="sxs-lookup"><span data-stu-id="d9307-150">-or-</span></span><br /><br /> <span data-ttu-id="d9307-151">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="d9307-151">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="d9307-152">Exécuter les travaux de compilation en attente.</span><span class="sxs-lookup"><span data-stu-id="d9307-152">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="d9307-153">Si une priorité est spécifiée, les travaux de compilation présentant une priorité supérieure ou égale sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="d9307-153">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="d9307-154">Si aucune priorité n'est spécifiée, tous les travaux de compilation en attente sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="d9307-154">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|<span data-ttu-id="d9307-155">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="d9307-155">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="d9307-156">Suspendre le service d'images natives, reprendre le service suspendu ou interroger l'état du service.</span><span class="sxs-lookup"><span data-stu-id="d9307-156">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="d9307-157">Arguments</span><span class="sxs-lookup"><span data-stu-id="d9307-157">Arguments</span></span>

|<span data-ttu-id="d9307-158">Argument</span><span class="sxs-lookup"><span data-stu-id="d9307-158">Argument</span></span>|<span data-ttu-id="d9307-159">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-159">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="d9307-160">Nom complet de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-160">The full display name of the assembly.</span></span> <span data-ttu-id="d9307-161">Par exemple : `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="d9307-161">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="d9307-162">**Remarque :** Vous pouvez fournir un nom d'assembly partiel, comme `myAssembly`, pour les actions `display` et `uninstall`.</span><span class="sxs-lookup"><span data-stu-id="d9307-162">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="d9307-163">Un seul assembly peut être spécifié par la ligne de commande Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="d9307-164">Chemin d’accès explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-164">The explicit path of the assembly.</span></span> <span data-ttu-id="d9307-165">Vous pouvez spécifier un chemin d'accès complet ou relatif.</span><span class="sxs-lookup"><span data-stu-id="d9307-165">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="d9307-166">Si vous spécifiez un nom de fichier sans chemin d'accès, l'assembly doit se trouver dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9307-166">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="d9307-167">Un seul assembly peut être spécifié par la ligne de commande Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-167">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="d9307-168">Niveaux de priorité</span><span class="sxs-lookup"><span data-stu-id="d9307-168">Priority Levels</span></span>

|<span data-ttu-id="d9307-169">Priority</span><span class="sxs-lookup"><span data-stu-id="d9307-169">Priority</span></span>|<span data-ttu-id="d9307-170">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-170">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="d9307-171">Les images natives sont générées et installées immédiatement, sans attendre la durée d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="d9307-171">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="d9307-172">Les images natives sont générées et installées sans attendre la durée d'inactivité, mais après la fin de toutes les actions de priorité 1 (et de leurs dépendances).</span><span class="sxs-lookup"><span data-stu-id="d9307-172">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="d9307-173">Les images natives sont installées lorsque le service d'images natives détecte que l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-173">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="d9307-174">Consultez [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-174">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="d9307-175">Scénarios</span><span class="sxs-lookup"><span data-stu-id="d9307-175">Scenarios</span></span>

|<span data-ttu-id="d9307-176">Scénario</span><span class="sxs-lookup"><span data-stu-id="d9307-176">Scenario</span></span>|<span data-ttu-id="d9307-177">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-177">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="d9307-178">Générer des images natives qui peuvent être utilisées sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d9307-178">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="d9307-179">Générer des images natives qui peuvent être utilisées sous un profileur.</span><span class="sxs-lookup"><span data-stu-id="d9307-179">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="d9307-180">Générer le nombre minimal d'images natives requis par les options de scénario spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d9307-180">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="d9307-181">Config</span><span class="sxs-lookup"><span data-stu-id="d9307-181">Config</span></span>

|<span data-ttu-id="d9307-182">Configuration</span><span class="sxs-lookup"><span data-stu-id="d9307-182">Configuration</span></span>|<span data-ttu-id="d9307-183">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-183">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="d9307-184">`/ExeConfig:` `exePath`</span><span class="sxs-lookup"><span data-stu-id="d9307-184">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="d9307-185">Utiliser la configuration de l'assembly exécutable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d9307-185">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="d9307-186">Ngen.exe doit prendre les mêmes décisions que le chargeur lors de la liaison avec les dépendances.</span><span class="sxs-lookup"><span data-stu-id="d9307-186">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="d9307-187">Lorsqu'un composant partagé est chargé au moment de l'exécution, à l'aide de la méthode <xref:System.Reflection.Assembly.Load%2A>, le fichier de configuration de l'application détermine les dépendances qui sont chargées pour le composant partagé, par exemple, la version d'une dépendance qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="d9307-187">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="d9307-188">Le commutateur `/ExeConfig` donne à Ngen.exe des instructions sur les dépendances qui seraient chargées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d9307-188">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|<span data-ttu-id="d9307-189">`/AppBase:` `directoryPath`</span><span class="sxs-lookup"><span data-stu-id="d9307-189">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="d9307-190">Lors de la localisation des dépendances, utilisez le répertoire spécifié comme base de l'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-190">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="d9307-191">Options</span><span class="sxs-lookup"><span data-stu-id="d9307-191">Options</span></span>

|<span data-ttu-id="d9307-192">Option</span><span class="sxs-lookup"><span data-stu-id="d9307-192">Option</span></span>|<span data-ttu-id="d9307-193">Description</span><span class="sxs-lookup"><span data-stu-id="d9307-193">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="d9307-194">Supprimer l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d9307-194">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="d9307-195">Supprimer l'affichage des messages d'opération réussie.</span><span class="sxs-lookup"><span data-stu-id="d9307-195">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="d9307-196">Afficher des informations détaillées sur le débogage.</span><span class="sxs-lookup"><span data-stu-id="d9307-196">Display detailed information for debugging.</span></span> <span data-ttu-id="d9307-197">**Remarque :** En raison des limitations du système d'exploitation, cette option n'affiche pas autant d'informations supplémentaires sur Windows 98 et Windows Millennium.</span><span class="sxs-lookup"><span data-stu-id="d9307-197">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|
|<span data-ttu-id="d9307-198">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="d9307-198">`/help`, `/?`</span></span>|<span data-ttu-id="d9307-199">Afficher la syntaxe de commande et les options de la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="d9307-199">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9307-200">Remarques</span><span class="sxs-lookup"><span data-stu-id="d9307-200">Remarks</span></span>

<span data-ttu-id="d9307-201">Pour exécuter Ngen.exe, vous devez disposer de privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d9307-201">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="d9307-202">N'exécutez pas Ngen.exe sur les assemblys dont le niveau de confiance n'est pas suffisant.</span><span class="sxs-lookup"><span data-stu-id="d9307-202">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="d9307-203">À compter de .NET Framework 4, Ngen.exe compile des assemblys avec une confiance totale et la stratégie de sécurité d’accès du code (CAS) n’est plus évaluée.</span><span class="sxs-lookup"><span data-stu-id="d9307-203">Starting with the .NET Framework 4, Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="d9307-204">À compter de .NET Framework 4, les images natives générées avec Ngen.exe ne peuvent plus être chargées dans les applications qui s’exécutent avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="d9307-204">Starting with the .NET Framework 4, the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="d9307-205">À la place, le compilateur juste-à-temps (JIT) est appelé.</span><span class="sxs-lookup"><span data-stu-id="d9307-205">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="d9307-206">Ngen.exe génère des images natives pour l'assembly spécifié par l’argument `assemblyname` passé à l’action `install` et toutes ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="d9307-206">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="d9307-207">Les dépendances sont déterminées à partir de références du manifeste d'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-207">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="d9307-208">Le seul scénario dans lequel vous devez installer une dépendance séparément est lorsque l'application la charge à l'aide de la réflexion, en appelant la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> par exemple.</span><span class="sxs-lookup"><span data-stu-id="d9307-208">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9307-209">N'utilisez pas la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> avec les images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-209">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="d9307-210">Une image chargée avec cette méthode ne peut pas être utilisée par d'autres assemblys dans le contexte d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d9307-210">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="d9307-211">Ngen.exe conserve un décompte des dépendances.</span><span class="sxs-lookup"><span data-stu-id="d9307-211">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="d9307-212">Par exemple, supposons que `MyAssembly.exe` et `YourAssembly.exe` sont installés tous les deux dans le cache des images natives et qu'ils contiennent tous les deux des références à `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="d9307-212">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="d9307-213">Si `MyAssembly.exe` est désinstallé, `OurDependency.dll` n'est pas désinstallée.</span><span class="sxs-lookup"><span data-stu-id="d9307-213">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="d9307-214">Il est supprimé uniquement lorsque `YourAssembly.exe` est également désinstallé.</span><span class="sxs-lookup"><span data-stu-id="d9307-214">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="d9307-215">Si vous générez une image native pour un assembly dans le Global Assembly Cache, spécifiez son nom complet.</span><span class="sxs-lookup"><span data-stu-id="d9307-215">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="d9307-216">Consultez <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9307-216">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d9307-217">Les images natives que Ngen.exe génère peuvent être partagées entre des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-217">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="d9307-218">Cela signifie que vous ne pouvez pas utiliser Ngen.exe dans des scénarios d'application qui nécessitent que les assemblys soient partagés par des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-218">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="d9307-219">Pour spécifier la neutralité de domaine :</span><span class="sxs-lookup"><span data-stu-id="d9307-219">To specify domain neutrality:</span></span>

- <span data-ttu-id="d9307-220">Appliquez l'attribut <xref:System.LoaderOptimizationAttribute> à votre application.</span><span class="sxs-lookup"><span data-stu-id="d9307-220">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="d9307-221">Définissez la propriété <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> lorsque vous créez des informations de configuration pour un nouveau domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-221">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="d9307-222">Utilisez toujours un code indépendant du domaine lors du chargement du même assembly dans plusieurs domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-222">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="d9307-223">Si une image native est chargée dans un domaine d'application non partagé après avoir été chargée dans un domaine partagé, elle ne peut pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9307-223">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-224">Le code indépendant du domaine ne peut pas être déchargé et les performances peuvent être légèrement plus lentes, en particulier lors de l'accès aux membres statiques.</span><span class="sxs-lookup"><span data-stu-id="d9307-224">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="d9307-225">Dans cette section Notes :</span><span class="sxs-lookup"><span data-stu-id="d9307-225">In this Remarks section:</span></span>

- [<span data-ttu-id="d9307-226">Génération d’images dans différents scénarios</span><span class="sxs-lookup"><span data-stu-id="d9307-226">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="d9307-227">Détermination des cas d'utilisation des images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-227">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="d9307-228">Amélioration de l'utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d9307-228">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="d9307-229">Démarrage plus rapide de l’application</span><span class="sxs-lookup"><span data-stu-id="d9307-229">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="d9307-230">Récapitulatif des considérations relatives à l'utilisation</span><span class="sxs-lookup"><span data-stu-id="d9307-230">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="d9307-231">Importance des adresses de base d'assemblys</span><span class="sxs-lookup"><span data-stu-id="d9307-231">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="d9307-232">Liaison matérielle</span><span class="sxs-lookup"><span data-stu-id="d9307-232">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="d9307-233">Spécification d’une indication sur la liaison d’une dépendance</span><span class="sxs-lookup"><span data-stu-id="d9307-233">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="d9307-234">Spécification d’une indication sur la liaison par défaut d’un assembly</span><span class="sxs-lookup"><span data-stu-id="d9307-234">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="d9307-235">Traitement différé</span><span class="sxs-lookup"><span data-stu-id="d9307-235">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="d9307-236">Images natives et compilation JIT</span><span class="sxs-lookup"><span data-stu-id="d9307-236">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="d9307-237">Images non valides</span><span class="sxs-lookup"><span data-stu-id="d9307-237">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="d9307-238">Dépannage</span><span class="sxs-lookup"><span data-stu-id="d9307-238">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="d9307-239">Visionneuse du journal de liaison d’assembly</span><span class="sxs-lookup"><span data-stu-id="d9307-239">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="d9307-240">Assistant Débogage managé JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="d9307-240">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="d9307-241">Désactivation de la génération des images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-241">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="d9307-242">Génération d'images dans différents scénarios</span><span class="sxs-lookup"><span data-stu-id="d9307-242">Generating images for     different scenarios</span></span>

<span data-ttu-id="d9307-243">Une fois que vous avez généré une image native pour un assembly, le runtime essaie automatiquement de la localiser et de l'utiliser chaque fois qu'il exécute l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-243">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="d9307-244">Plusieurs images peuvent être générées, selon les scénarios d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="d9307-244">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="d9307-245">Par exemple, si vous exécutez un assembly dans un scénario de débogage ou de profilage, le runtime recherche une image native générée à l'aide des options `/Debug` ou `/Profile`.</span><span class="sxs-lookup"><span data-stu-id="d9307-245">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="d9307-246">S'il ne trouve pas d'image native correspondante, le runtime revient à la compilation JIT standard.</span><span class="sxs-lookup"><span data-stu-id="d9307-246">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="d9307-247">La seule façon de déboguer des images natives consiste à créer une image native avec l'option `/Debug`.</span><span class="sxs-lookup"><span data-stu-id="d9307-247">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="d9307-248">L'action `uninstall` reconnaît également les scénarios, vous pouvez ainsi désinstaller tous les scénarios ou uniquement les scénarios sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="d9307-248">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="d9307-249">Détermination des cas d'utilisation des images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-249">Determining when to Use native images</span></span>

<span data-ttu-id="d9307-250">Les images natives peuvent fournir des améliorations des performances dans deux domaines : l'amélioration de l'utilisation de la mémoire et la réduction du temps de démarrage.</span><span class="sxs-lookup"><span data-stu-id="d9307-250">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-251">Les performances des images natives dépendent de plusieurs facteurs qui rendent l'analyse difficile, tels que le code et les modèles d'accès aux données, le nombre d'appels effectués entre les limites de module et le nombre de dépendances déjà chargées par d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="d9307-251">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="d9307-252">La seule façon de déterminer si les images natives tirent parti de votre application consiste à effectuer des mesures de performances prudentes dans vos scénarios de déploiement clés.</span><span class="sxs-lookup"><span data-stu-id="d9307-252">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="d9307-253">Amélioration de l'utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d9307-253">Improved memory use</span></span>

<span data-ttu-id="d9307-254">Les images natives peuvent considérablement améliorer l'utilisation de la mémoire lorsque le code est partagé entre des processus.</span><span class="sxs-lookup"><span data-stu-id="d9307-254">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="d9307-255">Les images natives sont des fichiers PE Windows. Une seule copie d'un fichier .dll peut donc être partagée par plusieurs processus ; en revanche, le code natif produit par le compilateur JIT est stocké dans la mémoire privée et ne peut pas être partagé.</span><span class="sxs-lookup"><span data-stu-id="d9307-255">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="d9307-256">Les applications qui sont exécutées sous des services Terminal Server peuvent également bénéficier de pages de code partagées.</span><span class="sxs-lookup"><span data-stu-id="d9307-256">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="d9307-257">En outre, ne pas charger le compilateur JIT économise une quantité de mémoire fixe pour chaque instance d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-257">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="d9307-258">Démarrage d'applications plus rapide</span><span class="sxs-lookup"><span data-stu-id="d9307-258">Faster application startup</span></span>

<span data-ttu-id="d9307-259">La précompilation des assemblys avec Ngen.exe peut améliorer le temps de démarrage de certaines applications.</span><span class="sxs-lookup"><span data-stu-id="d9307-259">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="d9307-260">En général, des progrès peuvent être réalisés lorsque les applications partagent des assemblys de composants, car après le démarrage de la première application, les composants partagés sont déjà chargés pour les applications suivantes.</span><span class="sxs-lookup"><span data-stu-id="d9307-260">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="d9307-261">Le démarrage à froid, dans lequel tous les assemblys d'une application doivent être chargés à partir du disque dur, ne tire pas autant parti des images natives, car le temps d'accès au disque dur prédomine.</span><span class="sxs-lookup"><span data-stu-id="d9307-261">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="d9307-262">La liaison matérielle peut affecter le temps de démarrage, car toutes les images qui sont liées par une liaison matérielle à l'assembly d'application principale doivent être chargées en même temps.</span><span class="sxs-lookup"><span data-stu-id="d9307-262">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-263">Avant .NET Framework 3.5 Service Pack 1, vous devez mettre les composants partagés avec nom fort dans le Global Assembly Cache, étant donné que le chargeur exécute une validation supplémentaire sur les assemblys avec nom fort qui ne sont pas dans le Global Assembly Cache, en éliminant efficacement toute amélioration du temps de démarrage gagné à l'aide des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-263">Before the .NET Framework 3.5 Service Pack 1, you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="d9307-264">Les optimisations présentées dans .NET Framework 3.5 SP1 ont supprimé la validation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d9307-264">Optimizations that were introduced in the .NET Framework 3.5 SP1 removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="d9307-265">Récapitulatif des considérations relatives à l'utilisation</span><span class="sxs-lookup"><span data-stu-id="d9307-265">Summary of usage considerations</span></span>

<span data-ttu-id="d9307-266">Les considérations générales suivantes et celles sur l'application peuvent vous aider à décider si cela vaut la peine d'évaluer des images natives pour votre application :</span><span class="sxs-lookup"><span data-stu-id="d9307-266">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="d9307-267">Les images natives se chargent plus vite que MSIL, car elles ne nécessitent pas beaucoup d'activités de démarrage, comme la compilation JIT et la vérification de la sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="d9307-267">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="d9307-268">Les images natives requièrent un jeu de travail initial réduit, car elles n'ont pas besoin d'un compilateur JIT.</span><span class="sxs-lookup"><span data-stu-id="d9307-268">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="d9307-269">Les images natives activent le partage de code entre les processus.</span><span class="sxs-lookup"><span data-stu-id="d9307-269">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="d9307-270">Les images natives requièrent plus d'espace de disque dur que les assemblys MSIL et leur génération peut nécessiter beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="d9307-270">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="d9307-271">Les images natives doivent être gérées.</span><span class="sxs-lookup"><span data-stu-id="d9307-271">Native images must be maintained.</span></span>

  - <span data-ttu-id="d9307-272">Elles doivent être régénérées lorsque l'assembly d'origine ou l'une de ses dépendances est pris(e) en charge.</span><span class="sxs-lookup"><span data-stu-id="d9307-272">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="d9307-273">Un seul assembly peut avoir besoin de plusieurs images natives pour les utiliser dans différentes applications ou différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="d9307-273">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="d9307-274">Par exemple, les informations de configuration de deux applications peuvent donner lieu à des décisions différentes en matière de liaison pour le même assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="d9307-274">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="d9307-275">Les images natives doivent être générées par un administrateur, c'est-à-dire à partir d'un compte Windows du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="d9307-275">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="d9307-276">Outre ces considérations générales, la nature de votre application doit être prise en compte lorsque vous déterminez si les images natives peuvent fournir un gain de performances :</span><span class="sxs-lookup"><span data-stu-id="d9307-276">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="d9307-277">Si votre application s'exécute dans un environnement qui utilise beaucoup de composants partagés, les images natives permettent aux composants d'être partagés entre plusieurs processus.</span><span class="sxs-lookup"><span data-stu-id="d9307-277">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="d9307-278">Si votre application utilise plusieurs domaines d'application, les images natives permettent à des pages de codes d'être partagées entre des domaines.</span><span class="sxs-lookup"><span data-stu-id="d9307-278">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9307-279">Dans les versions 1.0 et 1.1 du .NET Framework, les images natives ne peuvent pas être partagées entre des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-279">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="d9307-280">Ce n'est pas le cas dans les versions 2.0 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d9307-280">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="d9307-281">Si votre application est exécutée sous Terminal Server, les images natives autorisent le partage des pages de code.</span><span class="sxs-lookup"><span data-stu-id="d9307-281">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="d9307-282">Les applications volumineuses tirent généralement parti de la compilation dans des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-282">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="d9307-283">Les petites applications n'en tirent généralement pas parti.</span><span class="sxs-lookup"><span data-stu-id="d9307-283">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="d9307-284">Pour les applications de longue durée, la compilation JIT à l'exécution est légèrement plus performante que les images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-284">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="d9307-285">(La liaison matérielle peut atténuer cette différence de performances dans une certaine mesure.)</span><span class="sxs-lookup"><span data-stu-id="d9307-285">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="d9307-286">Importance des adresses de base d'assemblys</span><span class="sxs-lookup"><span data-stu-id="d9307-286">Importance of assembly base addresses</span></span>

<span data-ttu-id="d9307-287">Étant donné que les images natives sont des fichiers PE Windows, elles sont soumises aux mêmes problèmes de redéfinition que les autres fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="d9307-287">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="d9307-288">Le coût du réadressage en termes de performances est encore plus marqué si la liaison matérielle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9307-288">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="d9307-289">Pour définir l'adresse de base d'une image native, utilisez l'option appropriée de votre compilateur pour définir l'adresse de base de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-289">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="d9307-290">Ngen.exe utilise cette adresse de base pour l'image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-290">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-291">Les images natives sont plus volumineuses que les assemblys managés à partir desquels elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="d9307-291">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="d9307-292">Les adresses de base doivent être calculées pour prendre en compte ces tailles plus grandes.</span><span class="sxs-lookup"><span data-stu-id="d9307-292">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="d9307-293">Vous pouvez utiliser un outil tel que dumpbin.exe pour visualiser l'adresse de base par défaut d'une image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-293">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="d9307-294">Liaison matérielle</span><span class="sxs-lookup"><span data-stu-id="d9307-294">Hard binding</span></span>

<span data-ttu-id="d9307-295">La liaison matérielle augmente le débit et réduit la taille du jeu de travail des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-295">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="d9307-296">L'inconvénient de la liaison matérielle réside dans le fait que toutes les images liées par une liaison matérielle à un assembly doivent être chargées lorsque l'assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="d9307-296">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="d9307-297">Cela peut augmenter considérablement le temps de démarrage d'une application volumineuse.</span><span class="sxs-lookup"><span data-stu-id="d9307-297">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="d9307-298">La liaison matérielle convient aux dépendances qui sont chargées dans tous les scénarios de votre application dont les performances sont critiques.</span><span class="sxs-lookup"><span data-stu-id="d9307-298">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="d9307-299">Comme dans tous les aspects de l'utilisation des images natives, les mesures de performances prudentes constituent le seul moyen de déterminer si la liaison matérielle améliore les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="d9307-299">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="d9307-300">Les attributs <xref:System.Runtime.CompilerServices.DependencyAttribute> et <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> vous permettent de fournir des indications sur la liaison matérielle à Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-300">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-301">Ces attributs sont des indications destinées à Ngen.exe et non des commandes.</span><span class="sxs-lookup"><span data-stu-id="d9307-301">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="d9307-302">Leur utilisation ne garantit pas de liaison matérielle.</span><span class="sxs-lookup"><span data-stu-id="d9307-302">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="d9307-303">La signification de ces attributs peut changer dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d9307-303">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="d9307-304">Spécification d’une indication sur la liaison d’une dépendance</span><span class="sxs-lookup"><span data-stu-id="d9307-304">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="d9307-305">Appliquez <xref:System.Runtime.CompilerServices.DependencyAttribute> à un assembly pour indiquer la probabilité de chargement d'une dépendance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d9307-305">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="d9307-306"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indique que la liaison matérielle est appropriée, <xref:System.Runtime.CompilerServices.LoadHint.Default> indique que la valeur par défaut de la dépendance doit être utilisée et <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indique que la liaison matérielle n'est pas appropriée.</span><span class="sxs-lookup"><span data-stu-id="d9307-306"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="d9307-307">Le code suivant affiche les attributs d'un assembly qui possède deux dépendances.</span><span class="sxs-lookup"><span data-stu-id="d9307-307">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="d9307-308">La première dépendance (Assembly1) est un candidat approprié pour la liaison matérielle et la deuxième (Assembly2) ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="d9307-308">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

<span data-ttu-id="d9307-309">Le nom de l'assembly n'inclut pas l'extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d9307-309">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="d9307-310">Les noms complets peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="d9307-310">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="d9307-311">Spécification d’une indication sur la liaison par défaut d’un assembly</span><span class="sxs-lookup"><span data-stu-id="d9307-311">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="d9307-312">Les indications sur la liaison par défaut sont nécessaires uniquement pour les assemblys qui seront utilisés immédiatement et fréquemment par toute application qui possède une dépendance sur eux.</span><span class="sxs-lookup"><span data-stu-id="d9307-312">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="d9307-313">Appliquez <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> avec <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> aux assemblys de ce type pour spécifier que la liaison matérielle doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9307-313">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-314">Il est inutile d'appliquer <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> aux assemblys .dll qui ne correspondent pas à cette catégorie, car l'application de l'attribut ayant une valeur autre que <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> a le même effet que de ne pas appliquer l'attribut du tout.</span><span class="sxs-lookup"><span data-stu-id="d9307-314">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="d9307-315">Microsoft utilise <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> pour spécifier que la liaison matérielle est la valeur par défaut d'un très petit nombre d'assemblys dans le .NET Framework, tel que mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="d9307-315">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="d9307-316">Traitement différé</span><span class="sxs-lookup"><span data-stu-id="d9307-316">Deferred processing</span></span>

<span data-ttu-id="d9307-317">La génération d'images natives d'une application très volumineuse peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="d9307-317">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="d9307-318">De même, les modifications apportées à un composant partagé ou aux paramètres de l'ordinateur peuvent nécessiter la mise à jour de nombreuses images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-318">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="d9307-319">Les actions `install` et `update` possèdent une option `/queue` qui met en file d'attente l'opération en vue d'une exécution différée par le service d'images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-319">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="d9307-320">En outre, Ngen.exe possède des actions `queue` et `executeQueuedItems` qui offrent un certain contrôle sur le service.</span><span class="sxs-lookup"><span data-stu-id="d9307-320">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="d9307-321">Pour plus d’informations, consultez [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-321">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="d9307-322">Images natives et compilation JIT</span><span class="sxs-lookup"><span data-stu-id="d9307-322">Native images and JIT compilation</span></span>

<span data-ttu-id="d9307-323">Si, dans un assembly, Ngen.exe rencontre des méthodes qu'il ne peut pas générer, il les exclut de l'image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-323">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="d9307-324">Lorsque le runtime exécute cet assembly, il revient à la compilation JIT des méthodes non incluses dans l'image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-324">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="d9307-325">En outre, les images natives ne sont pas utilisées si l'assembly a été mis à niveau ou si l'image a été invalidée pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="d9307-325">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="d9307-326">Images non valides</span><span class="sxs-lookup"><span data-stu-id="d9307-326">Invalid images</span></span>

<span data-ttu-id="d9307-327">Lorsque vous utilisez Ngen.exe pour créer une image native d'un assembly, le résultat dépend des options de ligne de commande spécifiées et de certains paramètres de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9307-327">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="d9307-328">Les paramètres suivants sont inclus :</span><span class="sxs-lookup"><span data-stu-id="d9307-328">These settings include the following:</span></span>

- <span data-ttu-id="d9307-329">Version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9307-329">The version of the .NET Framework.</span></span>

- <span data-ttu-id="d9307-330">Version du système d'exploitation, si vous passez de la famille Windows 9x à la famille Windows NT.</span><span class="sxs-lookup"><span data-stu-id="d9307-330">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

- <span data-ttu-id="d9307-331">Identité exacte de l'assembly (toute nouvelle compilation modifie l'identité).</span><span class="sxs-lookup"><span data-stu-id="d9307-331">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="d9307-332">Identité exacte de tous les assemblys auxquels l'assembly fait référence (toute nouvelle compilation modifie l'identité).</span><span class="sxs-lookup"><span data-stu-id="d9307-332">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="d9307-333">Facteurs de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d9307-333">Security factors.</span></span>

<span data-ttu-id="d9307-334">Ngen.exe enregistre ces informations lorsqu'il génère une image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-334">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="d9307-335">Lorsque vous exécutez un assembly, le runtime recherche l'image native générée à l'aide des options et des paramètres correspondant à l'environnement actif de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9307-335">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="d9307-336">Le runtime revient à la compilation JIT d'un assembly, s'il ne trouve pas d'image native correspondante.</span><span class="sxs-lookup"><span data-stu-id="d9307-336">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="d9307-337">Les modifications suivantes des paramètres et de l'environnement d'un ordinateur entraînent la perte de validité des images natives :</span><span class="sxs-lookup"><span data-stu-id="d9307-337">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="d9307-338">Version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9307-338">The version of the .NET Framework.</span></span>

     <span data-ttu-id="d9307-339">Si vous appliquez une mise à jour au .NET Framework, toutes les images natives que vous avez créées à l'aide de Ngen.exe deviennent non valides.</span><span class="sxs-lookup"><span data-stu-id="d9307-339">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="d9307-340">Pour cette raison, toutes les mises à jour du .NET Framework exécutent la commande `Ngen Update`, afin de s'assurer que toutes les images natives sont régénérées.</span><span class="sxs-lookup"><span data-stu-id="d9307-340">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="d9307-341">Le .NET Framework crée automatiquement de nouvelles images natives pour les bibliothèques .NET Framework qu'il installe.</span><span class="sxs-lookup"><span data-stu-id="d9307-341">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="d9307-342">Version du système d'exploitation, si vous passez de la famille Windows 9x à la famille Windows NT.</span><span class="sxs-lookup"><span data-stu-id="d9307-342">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

     <span data-ttu-id="d9307-343">Par exemple, si la version du système d’exploitation s’exécutant sur un ordinateur passe de Windows 98 à Windows XP, toutes les images natives stockées dans le cache des images natives ne sont plus valides.</span><span class="sxs-lookup"><span data-stu-id="d9307-343">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="d9307-344">Toutefois, si le système d’exploitation passe de Windows 2000 à Windows XP, les images restent valides.</span><span class="sxs-lookup"><span data-stu-id="d9307-344">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>

- <span data-ttu-id="d9307-345">Identité exacte de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-345">The exact identity of the assembly.</span></span>

     <span data-ttu-id="d9307-346">Si vous recompilez un assembly, l'image native correspondante de l'assembly devient non valide.</span><span class="sxs-lookup"><span data-stu-id="d9307-346">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="d9307-347">Identité exacte des assemblys auxquels l'assembly fait référence.</span><span class="sxs-lookup"><span data-stu-id="d9307-347">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="d9307-348">Si vous mettez à jour un assembly managé, toutes les images natives qui dépendent directement ou indirectement de cet assembly deviennent non valides et doivent être régénérées.</span><span class="sxs-lookup"><span data-stu-id="d9307-348">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="d9307-349">Cela inclut des références ordinaires et des dépendances liées par une liaison matérielle.</span><span class="sxs-lookup"><span data-stu-id="d9307-349">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="d9307-350">Chaque fois qu'une mise à jour de logiciel est appliquée, le programme d'installation doit exécuter une commande `Ngen Update` pour garantir que toutes les images natives dépendantes sont régénérées.</span><span class="sxs-lookup"><span data-stu-id="d9307-350">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="d9307-351">Facteurs de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d9307-351">Security factors.</span></span>

     <span data-ttu-id="d9307-352">Le changement de stratégie de sécurité d'un ordinateur pour restreindre les autorisations précédemment accordées à un assembly peut entraîner la perte de validité d'une image native précédemment compilée de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-352">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="d9307-353">Pour plus d'informations sur la façon dont le Common Language Runtime administre la sécurité d'accès du code et sur l'utilisation des autorisations, consultez [Sécurité d'accès du code](../misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="d9307-353">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="d9307-354">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="d9307-354">Troubleshooting</span></span>

<span data-ttu-id="d9307-355">Les rubriques de résolution de problèmes suivantes vous permettent d’identifier les images natives qui sont utilisées par votre application et celles qui ne le peuvent pas, de déterminer quand le compilateur JIT commence à compiler une méthode, et montrent comment désactiver la compilation d’images natives des méthodes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d9307-355">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="d9307-356">visionneuse du journal de liaison d’assembly</span><span class="sxs-lookup"><span data-stu-id="d9307-356">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="d9307-357">Pour confirmer que les images natives sont utilisées par votre application, vous pouvez utiliser [Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)](fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="d9307-357">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="d9307-358">Sélectionnez **Images natives** dans la zone **Catégories du journal** dans la fenêtre de la visionneuse du journal des liaisons.</span><span class="sxs-lookup"><span data-stu-id="d9307-358">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="d9307-359">Fuslogvw.exe fournit des informations sur la raison pour laquelle une image native a été rejetée.</span><span class="sxs-lookup"><span data-stu-id="d9307-359">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="d9307-360">Assistant Débogage managé JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="d9307-360">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="d9307-361">Vous pouvez utiliser l'Assistant Débogage managé (MDA) [JITCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) pour déterminer quand le compilateur JIT commence à compiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="d9307-361">You can use the [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="d9307-362">Désactivation de la génération des images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-362">Opting out of native image generation</span></span>

<span data-ttu-id="d9307-363">Dans certains cas, NGen.exe peut avoir des difficultés à générer une image native pour une méthode spécifique, ou vous pouvez préférer que la méthode soit compilée par JIT et non compilée dans une image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-363">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="d9307-364">Dans ce cas, vous pouvez utiliser l’attribut `System.Runtime.BypassNGenAttribute` pour éviter que NGen.exe génère une image native pour une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="d9307-364">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="d9307-365">L’attribut doit être appliqué individuellement à chaque méthode dont vous ne voulez pas inclure le code dans l’image native.</span><span class="sxs-lookup"><span data-stu-id="d9307-365">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="d9307-366">NGen.exe reconnaît l’attribut et ne génère pas de code dans l’image native pour la méthode correspondante.</span><span class="sxs-lookup"><span data-stu-id="d9307-366">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="d9307-367">Toutefois, notez que `BypassNGenAttribute` n’est pas défini comme un type dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9307-367">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="d9307-368">Pour pouvoir utiliser l’attribut dans votre code, vous devez d’abord le définir de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="d9307-368">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="d9307-369">Vous pouvez ensuite appliquer l’attribut selon la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9307-369">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="d9307-370">Dans l’exemple suivant, le générateur d’images natives reçoit l’instruction de ne pas générer d’image native pour la méthode `ExampleClass.ToJITCompile`.</span><span class="sxs-lookup"><span data-stu-id="d9307-370">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="d9307-371">Exemples</span><span class="sxs-lookup"><span data-stu-id="d9307-371">Examples</span></span>

<span data-ttu-id="d9307-372">La commande suivante génère une image native de `ClientApp.exe`, située dans le répertoire actif, puis installe l'image dans le cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-372">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="d9307-373">S'il existe un fichier de configuration de l'assembly, Ngen.exe l'utilise.</span><span class="sxs-lookup"><span data-stu-id="d9307-373">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="d9307-374">En outre, les images natives sont générées pour tous les fichiers .dll auxquels `ClientApp.exe` fait référence.</span><span class="sxs-lookup"><span data-stu-id="d9307-374">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```console
ngen install ClientApp.exe
```

<span data-ttu-id="d9307-375">Une image installée avec Ngen.exe est également appelée une racine.</span><span class="sxs-lookup"><span data-stu-id="d9307-375">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="d9307-376">Une racine peut être une application ou un composant partagé.</span><span class="sxs-lookup"><span data-stu-id="d9307-376">A root can be an application or a shared component.</span></span>

<span data-ttu-id="d9307-377">La commande suivante génère une image native de `MyAssembly.exe` en fonction du chemin d'accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="d9307-377">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```console
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="d9307-378">Lors de la localisation des assemblys et de leurs dépendances, Ngen.exe utilise la même logique de détection que celle utilisée par le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="d9307-378">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="d9307-379">Par défaut, le répertoire qui contient `ClientApp.exe` est utilisé comme répertoire de base de l'application et toute la recherche d'assemblys commence dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="d9307-379">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="d9307-380">Vous pouvez remplacer ce comportement en utilisant l'option `/AppBase`.</span><span class="sxs-lookup"><span data-stu-id="d9307-380">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-381">Il s'agit là d'un changement par rapport au comportement de Ngen.exe dans les versions 1.0 et 1.1 du .NET Framework, dans lesquelles la base de l'application est définie sur le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9307-381">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="d9307-382">Un assembly peut posséder une dépendance sans référence, par exemple, s'il charge un fichier .dll en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9307-382">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d9307-383">Vous pouvez créer une image native d'un fichier .dll de ce type en utilisant des informations de configuration de l'assembly d'application, avec l'option `/ExeConfig`.</span><span class="sxs-lookup"><span data-stu-id="d9307-383">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="d9307-384">La commande suivante génère une image native de `MyLib.dll,` à l'aide des informations de configuration de `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="d9307-384">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="d9307-385">Les assemblys installés grâce à cette méthode ne sont pas supprimés lorsque l'application est supprimée.</span><span class="sxs-lookup"><span data-stu-id="d9307-385">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="d9307-386">Pour désinstaller une dépendance, utilisez les mêmes options de ligne de commande que celles qui ont servi à l'installer.</span><span class="sxs-lookup"><span data-stu-id="d9307-386">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="d9307-387">La commande suivante désinstalle `MyLib.dll` de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="d9307-387">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="d9307-388">Pour créer une image native d'un assembly dans le Global Assembly Cache, utilisez le nom complet de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-388">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="d9307-389">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d9307-389">For example:</span></span>

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="d9307-390">NGen.exe génère un ensemble d'images séparé pour chaque scénario que vous installez.</span><span class="sxs-lookup"><span data-stu-id="d9307-390">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="d9307-391">Par exemple, les commandes suivantes installent un jeu complet d'images natives pour les opérations normales, un autre jeu complet pour le débogage et un troisième pour le profilage :</span><span class="sxs-lookup"><span data-stu-id="d9307-391">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="d9307-392">Affichage du cache des images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-392">Displaying the Native Image Cache</span></span>

<span data-ttu-id="d9307-393">Une fois les images natives installées dans le cache, elles peuvent être affichées à l'aide de Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-393">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="d9307-394">La commande suivante affiche toutes les images natives du cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-394">The following command displays all native images in the native image cache.</span></span>

```console
ngen display
```

<span data-ttu-id="d9307-395">L'action `display` répertorie d'abord tous les assemblys racine, puis toutes les images natives sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9307-395">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="d9307-396">Utilisez le nom simple d'un assembly pour afficher uniquement les informations de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="d9307-396">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="d9307-397">La commande suivante affiche toutes les images natives dans le cache des images natives qui correspondent au nom partiel `MyAssembly`, leurs dépendances et toutes les racines qui ont une dépendance sur `MyAssembly` :</span><span class="sxs-lookup"><span data-stu-id="d9307-397">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```console
ngen display MyAssembly
```

<span data-ttu-id="d9307-398">Connaître les racines qui dépendent d'un assembly de composant partagé est utile pour mesurer l'impact d'une action `update` après la mise à niveau du composant partagé.</span><span class="sxs-lookup"><span data-stu-id="d9307-398">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="d9307-399">Si vous spécifiez l’extension de fichier d’un assembly, vous devez spécifier le chemin d’accès ou exécuter Ngen.exe à partir du répertoire qui contient l’assembly :</span><span class="sxs-lookup"><span data-stu-id="d9307-399">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```console
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="d9307-400">La commande suivante affiche toutes les images natives du cache des images natives avec le nom `MyAssembly` et la version 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="d9307-400">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="d9307-401">Mise à jour d'images</span><span class="sxs-lookup"><span data-stu-id="d9307-401">Updating Images</span></span>

<span data-ttu-id="d9307-402">Les images sont généralement mises à jour après la mise à niveau d'un composant partagé.</span><span class="sxs-lookup"><span data-stu-id="d9307-402">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="d9307-403">Pour mettre à jour toutes les images natives qui ont été modifiées ou dont les dépendances ont été modifiées, utilisez l'action `update` sans arguments.</span><span class="sxs-lookup"><span data-stu-id="d9307-403">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```console
ngen update
```

<span data-ttu-id="d9307-404">La mise à jour de toutes les images peut prendre du temps.</span><span class="sxs-lookup"><span data-stu-id="d9307-404">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="d9307-405">Vous pouvez mettre en file d'attente les mises à jour pour une exécution par le service d'images natives en utilisant l'option `/queue`.</span><span class="sxs-lookup"><span data-stu-id="d9307-405">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="d9307-406">Pour plus d’informations sur l’option `/queue` et les priorités d’installation, consultez [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-406">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```console
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="d9307-407">Désinstallation d'images</span><span class="sxs-lookup"><span data-stu-id="d9307-407">Uninstalling Images</span></span>

<span data-ttu-id="d9307-408">Ngen.exe gère une liste de dépendances, de sorte que les composants partagés soient supprimés uniquement lorsque tous les assemblys qui dépendent d'eux ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="d9307-408">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="d9307-409">En outre, un composant partagé n'est pas supprimé s'il a été installé comme racine.</span><span class="sxs-lookup"><span data-stu-id="d9307-409">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="d9307-410">La commande suivante désinstalle tous les scénarios de `ClientApp.exe` racine :</span><span class="sxs-lookup"><span data-stu-id="d9307-410">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp
```

<span data-ttu-id="d9307-411">L'action `uninstall` peut être utilisée pour supprimer des scénarios spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d9307-411">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="d9307-412">La commande suivante désinstalle tous les scénarios de débogage de `ClientApp.exe` :</span><span class="sxs-lookup"><span data-stu-id="d9307-412">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="d9307-413">La désinstallation de scénarios `/debug` ne désinstalle pas un scénario qui inclut `/profile` et `/debug.`</span><span class="sxs-lookup"><span data-stu-id="d9307-413">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>

<span data-ttu-id="d9307-414">La commande suivante désinstalle tous les scénarios d'une version spécifique de `ClientApp.exe` :</span><span class="sxs-lookup"><span data-stu-id="d9307-414">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="d9307-415">Les commandes suivantes désinstallent tous les scénarios de `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` ou seulement le scénario de débogage de cet assembly :</span><span class="sxs-lookup"><span data-stu-id="d9307-415">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="d9307-416">Comme avec l'action `install`, le fait de fournir une extension requiert d'exécuter Ngen.exe à partir du répertoire contenant l'assembly ou de spécifier un chemin d'accès complet.</span><span class="sxs-lookup"><span data-stu-id="d9307-416">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="d9307-417">Pour obtenir des exemples liés au service d’images natives, consultez [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-417">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="d9307-418">Tâche d’image native</span><span class="sxs-lookup"><span data-stu-id="d9307-418">Native Image Task</span></span>

<span data-ttu-id="d9307-419">La tâche d'image native est une tâche Windows qui génère et conserve des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-419">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="d9307-420">La tâche d’image native génère et libère les images natives automatiquement pour les scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d9307-420">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="d9307-421">Elle permet aussi aux programmes d'installation d'utiliser [Ngen.exe (Générateur d'images natives)](ngen-exe-native-image-generator.md) pour créer et mettre à jour des images natives à un moment différé.</span><span class="sxs-lookup"><span data-stu-id="d9307-421">It also enables installers to use [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="d9307-422">La tâche d’image native est enregistrée une seule fois pour chaque architecture de processeur prise en charge sur un ordinateur, pour permettre la compilation des applications qui ciblent chaque architecture :</span><span class="sxs-lookup"><span data-stu-id="d9307-422">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="d9307-423">Nom de la tâche</span><span class="sxs-lookup"><span data-stu-id="d9307-423">Task name</span></span>|<span data-ttu-id="d9307-424">ordinateur 32 bits</span><span class="sxs-lookup"><span data-stu-id="d9307-424">32-bit computer</span></span>|<span data-ttu-id="d9307-425">Ordinateur 64 bits</span><span class="sxs-lookup"><span data-stu-id="d9307-425">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="d9307-426">.NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="d9307-426">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="d9307-427">Oui</span><span class="sxs-lookup"><span data-stu-id="d9307-427">Yes</span></span>|<span data-ttu-id="d9307-428">Yes</span><span class="sxs-lookup"><span data-stu-id="d9307-428">Yes</span></span>|
|<span data-ttu-id="d9307-429">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="d9307-429">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="d9307-430">Non</span><span class="sxs-lookup"><span data-stu-id="d9307-430">No</span></span>|<span data-ttu-id="d9307-431">Oui</span><span class="sxs-lookup"><span data-stu-id="d9307-431">Yes</span></span>|

<span data-ttu-id="d9307-432">La tâche d’image native est disponible dans le .NET Framework 4.5 et versions ultérieures, dans le cadre d’une exécution sur Windows 8 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d9307-432">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="d9307-433">Dans les versions antérieures de Windows, le .NET Framework utilise le [Service d’images natives](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="d9307-433">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="d9307-434">Durée de vie de la tâche</span><span class="sxs-lookup"><span data-stu-id="d9307-434">Task Lifetime</span></span>

<span data-ttu-id="d9307-435">En général, le Planificateur de tâches Windows démarre la tâche d'image native chaque nuit quand l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-435">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="d9307-436">La tâche recherche tout travail différé mis en attente par les programmes d'installation de l'application, toutes les demandes de mise à jour différée des images natives et toute création automatique d'images.</span><span class="sxs-lookup"><span data-stu-id="d9307-436">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="d9307-437">La tâche termine les éléments de travail en attente, puis s'arrête.</span><span class="sxs-lookup"><span data-stu-id="d9307-437">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="d9307-438">Si l'ordinateur cesse d'être inactif alors que la tâche s'exécute, celle-ci s'arrête.</span><span class="sxs-lookup"><span data-stu-id="d9307-438">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="d9307-439">Vous pouvez également démarrer la tâche d'image native manuellement à l'aide de l'interface utilisateur du Planificateur de tâches ou via des appels manuels à NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-439">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="d9307-440">Si la tâche est démarrée par le biais de ces méthodes, elle continue à s'exécuter quand l'ordinateur n'est plus inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-440">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="d9307-441">Les images créées manuellement à l'aide de NGen.exe sont hiérarchisées pour activer un comportement prévisible pour les programmes d'installation de l'application.</span><span class="sxs-lookup"><span data-stu-id="d9307-441">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="d9307-442">Service d'images natives</span><span class="sxs-lookup"><span data-stu-id="d9307-442">Native Image Service</span></span>

<span data-ttu-id="d9307-443">Le service d'images natives est un service Windows qui génère et conserve des images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-443">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="d9307-444">Le service d'images natives permet au développeur de différer l'installation et la mise à jour d'images natives jusqu'au moment où l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-444">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="d9307-445">Normalement, le service d'images natives est lancé par le programme d'installation d'une application ou mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d9307-445">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="d9307-446">Pour les actions de priorité 3, le service s'exécute pendant que l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-446">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="d9307-447">Le service enregistre son état et est capable de poursuivre après de multiples redémarrages si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d9307-447">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="d9307-448">Plusieurs compilations d'images peuvent être mises en attente.</span><span class="sxs-lookup"><span data-stu-id="d9307-448">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="d9307-449">Le service interagit également avec la commande Ngen.exe manuelle.</span><span class="sxs-lookup"><span data-stu-id="d9307-449">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="d9307-450">Les commandes manuelles sont prioritaires sur l'activité en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d9307-450">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="d9307-451">Sur Windows Vista, le nom affiché pour le service d'images natives est « Microsoft.NET Framework NGEN v2.0.50727_X86 » ou « Microsoft.NET Framework NGEN v2.0.50727_X64 ».</span><span class="sxs-lookup"><span data-stu-id="d9307-451">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="d9307-452">Sur toutes les versions antérieures de Microsoft Windows, le nom est « .NET Runtime Optimization Service v2.0.50727_X86 » ou « .NET Runtime Optimization Service v2.0.50727_X64 ».</span><span class="sxs-lookup"><span data-stu-id="d9307-452">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="d9307-453">Lancement d'opérations différées</span><span class="sxs-lookup"><span data-stu-id="d9307-453">Launching Deferred Operations</span></span>

<span data-ttu-id="d9307-454">Avant de commencer une installation ou une mise à niveau, il est recommandé d'interrompre le service.</span><span class="sxs-lookup"><span data-stu-id="d9307-454">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="d9307-455">Cette interruption garantit que le service ne s'exécute pas pendant que le programme d'installation copie des fichiers ou place des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="d9307-455">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="d9307-456">La ligne de commande Ngen.exe suivante interrompt le service :</span><span class="sxs-lookup"><span data-stu-id="d9307-456">The following Ngen.exe command line pauses the service:</span></span>

```console
ngen queue pause
```

<span data-ttu-id="d9307-457">Quand toutes les opérations différées ont été mises en attente, la commande suivante autorise le service à reprendre :</span><span class="sxs-lookup"><span data-stu-id="d9307-457">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```console
ngen queue continue
```

<span data-ttu-id="d9307-458">Pour différer la génération d'images natives lors de l'installation d'une nouvelle application ou lors de la mise à jour d'un composant partagé, utilisez l'option `/queue` avec les actions `install` ou `update`.</span><span class="sxs-lookup"><span data-stu-id="d9307-458">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="d9307-459">Les lignes de commande Ngen.exe suivantes installent une image native pour un composant partagé et effectuent une mise à jour de toutes les racines éventuellement affectées :</span><span class="sxs-lookup"><span data-stu-id="d9307-459">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```console
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="d9307-460">L'action `update` régénère toutes les images natives qui ont été invalidées, pas uniquement celles qui utilisent `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="d9307-460">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="d9307-461">Si votre application se compose de nombreuses racines, vous pouvez contrôler la priorité des actions différées.</span><span class="sxs-lookup"><span data-stu-id="d9307-461">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="d9307-462">Les commandes suivantes mettent en file d'attente l'installation de trois racines.</span><span class="sxs-lookup"><span data-stu-id="d9307-462">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="d9307-463">`Assembly1` est installé en premier, sans attendre l'inactivité.</span><span class="sxs-lookup"><span data-stu-id="d9307-463">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="d9307-464">`Assembly2` est également installé sans attendre l'inactivité, mais une fois que toutes les actions de priorité 1 sont terminées.</span><span class="sxs-lookup"><span data-stu-id="d9307-464">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="d9307-465">`Assembly3` est installé quand le service détecte que l'ordinateur est inactif.</span><span class="sxs-lookup"><span data-stu-id="d9307-465">`Assembly3` is installed when the service detects that the computer is idle.</span></span>

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="d9307-466">Vous pouvez forcer des actions mises en file d'attente à se produire de façon synchrone à l'aide de l'action `executeQueuedItems`.</span><span class="sxs-lookup"><span data-stu-id="d9307-466">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="d9307-467">Si vous fournissez la priorité facultative, cette action affecte uniquement les actions mises en file d'attente qui ont une priorité égale ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="d9307-467">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="d9307-468">La priorité par défaut est 3, donc la commande Ngen.exe suivante traite toutes les actions mises en file d'attente immédiatement et ne retourne pas de résultat tant qu'elles ne sont pas terminées :</span><span class="sxs-lookup"><span data-stu-id="d9307-468">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```console
ngen executeQueuedItems
```

<span data-ttu-id="d9307-469">Les commandes synchrones sont exécutées par Ngen.exe et n'utilisent pas le service d'images natives.</span><span class="sxs-lookup"><span data-stu-id="d9307-469">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="d9307-470">Vous pouvez exécuter des actions à l'aide de Ngen.exe pendant que le service d'images natives s'exécute.</span><span class="sxs-lookup"><span data-stu-id="d9307-470">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="d9307-471">Arrêt du service</span><span class="sxs-lookup"><span data-stu-id="d9307-471">Service Shutdown</span></span>

<span data-ttu-id="d9307-472">Après avoir été initialisé par l'exécution d'une commande Ngen.exe qui inclut l'option `/queue`, le service s'exécute en arrière-plan jusqu'à ce que toutes les actions aient été effectuées.</span><span class="sxs-lookup"><span data-stu-id="d9307-472">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="d9307-473">Le service enregistre son état pour pouvoir continuer via de multiples redémarrages si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d9307-473">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="d9307-474">Quand le service détecte qu'il n'y aucune action en attente, il réinitialise son état afin de ne pas redémarrer la prochaine fois que l'ordinateur est démarré, puis il s'arrête.</span><span class="sxs-lookup"><span data-stu-id="d9307-474">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="d9307-475">Interaction du service avec les clients</span><span class="sxs-lookup"><span data-stu-id="d9307-475">Service Interaction with Clients</span></span>

<span data-ttu-id="d9307-476">Dans le .NET Framework version 2.0, la seule interaction avec le service d'images natives s'effectue via l'outil en ligne de commande Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="d9307-476">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="d9307-477">Utilisez l'outil en ligne de commande dans les scripts d'installation pour mettre en file d'attente des actions pour le service d'images natives et interagir avec le service.</span><span class="sxs-lookup"><span data-stu-id="d9307-477">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9307-478">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9307-478">See also</span></span>

- [<span data-ttu-id="d9307-479">outils</span><span class="sxs-lookup"><span data-stu-id="d9307-479">Tools</span></span>](index.md)
- [<span data-ttu-id="d9307-480">Processus d’exécution managée</span><span class="sxs-lookup"><span data-stu-id="d9307-480">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="d9307-481">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="d9307-481">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d9307-482">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="d9307-482">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
