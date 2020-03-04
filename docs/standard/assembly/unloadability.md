---
title: Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core
description: Découvrez comment utiliser un AssemblyLoadContext pouvant être collecté pour charger et décharger des assemblys managés, et comment résoudre les problèmes de déchargement.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159739"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="b7390-103">Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7390-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="b7390-104">À compter de .NET Core 3.0, il est possible de charger un ensemble d’assemblys et de le décharger plus tard.</span><span class="sxs-lookup"><span data-stu-id="b7390-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="b7390-105">Dans le .NET Framework, les domaines d’application personnalisés étaient utilisés à cet effet, mais .NET Core ne prend en charge qu’un seul domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="b7390-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="b7390-106">.NET Core 3.0 et versions ultérieures utilisent <xref:System.Runtime.Loader.AssemblyLoadContext> pour prendre en charge le déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="b7390-107">Vous pouvez charger un ensemble d’assemblys dans un `AssemblyLoadContext` pouvant être collecté, exécuter des méthodes dans ceux-ci ou simplement les inspecter par réflexion, puis finalement décharger `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="b7390-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="b7390-108">Cela décharge les assemblys chargés dans le `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="b7390-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="b7390-109">Il existe une différence notable entre le déchargement qui utilise `AssemblyLoadContext` et celui qui utilise des domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="b7390-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="b7390-110">Avec les domaines d’application, le déchargement est forcé.</span><span class="sxs-lookup"><span data-stu-id="b7390-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="b7390-111">Au moment du déchargement, tous les threads qui s’exécutent dans l’AppDomain cible sont abandonnés, les objets COM managés créés dans l’AppDomain cible sont détruits, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b7390-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="b7390-112">Avec `AssemblyLoadContext`, le déchargement est « coopératif ».</span><span class="sxs-lookup"><span data-stu-id="b7390-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="b7390-113">L’appel de la méthode <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> lance simplement le déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="b7390-114">Le déchargement se termine quand :</span><span class="sxs-lookup"><span data-stu-id="b7390-114">The unloading finishes after:</span></span>

- <span data-ttu-id="b7390-115">Aucun thread n’a de méthodes provenant des assemblys chargés dans `AssemblyLoadContext` sur leurs piles d’appels.</span><span class="sxs-lookup"><span data-stu-id="b7390-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="b7390-116">Aucun des types des assemblys chargés dans le `AssemblyLoadContext`, les instances de ces types et les assemblys eux-mêmes sont référencés par :</span><span class="sxs-lookup"><span data-stu-id="b7390-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="b7390-117">Des références en dehors d’`AssemblyLoadContext`, à l’exception de références faibles (<xref:System.WeakReference> ou <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="b7390-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="b7390-118">Handles de garbage collector (GC) forts ([GCHandleType. normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) ou [GCHandleType. épinglé](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) à partir de l’intérieur et de l’extérieur de la `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="b7390-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="b7390-119">Utiliser l’AssemblyLoadContext pouvant être collecté</span><span class="sxs-lookup"><span data-stu-id="b7390-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="b7390-120">Cette section contient un tutoriel pas à pas qui présente un moyen simple de charger une application .NET Core dans un `AssemblyLoadContext` pouvant être collecté, d’exécuter son point d’entrée, puis de procéder au déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="b7390-121">Vous trouverez un exemple complet dans [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span><span class="sxs-lookup"><span data-stu-id="b7390-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="b7390-122">Créer un AssemblyLoadContext pouvant être collecté</span><span class="sxs-lookup"><span data-stu-id="b7390-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="b7390-123">Vous devez dériver votre classe d’<xref:System.Runtime.Loader.AssemblyLoadContext> et surcharger sa méthode <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7390-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7390-124">Cette méthode résout les références à tous les assemblys qui sont des dépendances d’assemblys chargés dans cet `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="b7390-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="b7390-125">Le code suivant est un exemple d’un `AssemblyLoadContext` de base personnalisé :</span><span class="sxs-lookup"><span data-stu-id="b7390-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="b7390-126">Comme vous pouvez le voir, la méthode `Load` retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="b7390-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="b7390-127">Cela signifie que tous les assemblys de dépendances sont chargés dans le contexte par défaut, et que le nouveau contexte contient uniquement les assemblys explicitement chargés dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b7390-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="b7390-128">Si vous souhaitez également charger une partie ou la totalité des dépendances dans `AssemblyLoadContext`, vous pouvez utiliser `AssemblyDependencyResolver` dans la méthode `Load`.</span><span class="sxs-lookup"><span data-stu-id="b7390-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="b7390-129">Le `AssemblyDependencyResolver` résout les noms d’assembly en chemins d’accès absolus au fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b7390-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="b7390-130">Le programme de résolution utilise le fichier *. DEPS. JSON* et les fichiers d’assembly dans le répertoire de l’assembly principal chargé dans le contexte.</span><span class="sxs-lookup"><span data-stu-id="b7390-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="b7390-131">Utiliser un AssemblyLoadContext personnalisé pouvant être collecté</span><span class="sxs-lookup"><span data-stu-id="b7390-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="b7390-132">Cette section part du principe que vous utilisez la version de base de `TestAssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="b7390-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="b7390-133">Pour créer une instance d’un `AssemblyLoadContext` personnalisé et y charger un assembly, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7390-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="b7390-134">Pour chacun des assemblys référencés par l’assembly chargé, la méthode `TestAssemblyLoadContext.Load` est appelée afin que `TestAssemblyLoadContext` puisse déterminer où obtenir l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b7390-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="b7390-135">Dans notre cas, elle retourne `null` pour indiquer qu’il doit être chargé dans le contexte par défaut à partir d’emplacements que le runtime utilise pour charger les assemblys par défaut.</span><span class="sxs-lookup"><span data-stu-id="b7390-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="b7390-136">Maintenant qu’un assembly a été chargé, vous pouvez exécuter une méthode à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b7390-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="b7390-137">Exécutez la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="b7390-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="b7390-138">Quand la méthode `Main` retourne une valeur, vous pouvez lancer le déchargement en appelant la méthode `Unload` sur l’`AssemblyLoadContext` personnalisé ou en éliminant la référence à `AssemblyLoadContext` :</span><span class="sxs-lookup"><span data-stu-id="b7390-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="b7390-139">Cela suffit pour décharger l’assembly de test.</span><span class="sxs-lookup"><span data-stu-id="b7390-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="b7390-140">Nous allons à présent placer tout cela dans une méthode distincte non inlineable de telle sorte que `TestAssemblyLoadContext`, `Assembly` et `MethodInfo` (`Assembly.EntryPoint`) ne puissent pas être maintenus actifs par des références d’emplacement de pile (variables locales en temps réel ou juste-à-temps).</span><span class="sxs-lookup"><span data-stu-id="b7390-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="b7390-141">En effet, le déchargement n’a pas lieu si `TestAssemblyLoadContext` reste actif.</span><span class="sxs-lookup"><span data-stu-id="b7390-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="b7390-142">Retournez également une référence faible à `AssemblyLoadContext` afin que vous puissiez l’utiliser par la suite pour détecter la fin du déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="b7390-143">Vous pouvez maintenant exécuter cette fonction pour charger, exécuter et décharger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b7390-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="b7390-144">Toutefois, le déchargement ne se termine pas immédiatement.</span><span class="sxs-lookup"><span data-stu-id="b7390-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="b7390-145">Comme mentionné précédemment, il s’appuie sur le garbage collector pour collecter tous les objets de l’assembly de test.</span><span class="sxs-lookup"><span data-stu-id="b7390-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="b7390-146">Dans de nombreux cas, il n’est pas nécessaire d’attendre la fin du déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="b7390-147">Toutefois, dans certains cas, il est utile de savoir que le déchargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="b7390-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="b7390-148">Par exemple, vous souhaitez peut-être supprimer le fichier d’assembly qui a été chargé dans l’`AssemblyLoadContext` personnalisé du disque.</span><span class="sxs-lookup"><span data-stu-id="b7390-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="b7390-149">Dans ce cas, vous pouvez utiliser l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b7390-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="b7390-150">Il déclenche garbage collection et attend les finaliseurs en attente dans une boucle jusqu’à ce que la référence faible à la `AssemblyLoadContext` personnalisée soit définie sur `null`, ce qui indique que l’objet cible a été collecté.</span><span class="sxs-lookup"><span data-stu-id="b7390-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="b7390-151">Dans la plupart des cas, un seul passage à la boucle est requis.</span><span class="sxs-lookup"><span data-stu-id="b7390-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="b7390-152">Toutefois, dans les cas plus complexes où les objets créés par le code qui s’exécute dans `AssemblyLoadContext` ont des finaliseurs, des passages supplémentaires peuvent être nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b7390-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="b7390-153">Événement de déchargement</span><span class="sxs-lookup"><span data-stu-id="b7390-153">The Unloading event</span></span>

<span data-ttu-id="b7390-154">Dans certains cas, le code chargé dans un `AssemblyLoadContext` personnalisé doit effectuer des tâches de nettoyage au moment du lancement du déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="b7390-155">Par exemple, il peut être nécessaire d’arrêter des threads ou de nettoyer des handles de GC forts.</span><span class="sxs-lookup"><span data-stu-id="b7390-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="b7390-156">L’événement `Unloading` peut être utilisé dans de tels cas.</span><span class="sxs-lookup"><span data-stu-id="b7390-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="b7390-157">Un gestionnaire qui effectue le nettoyage nécessaire peut être raccroché à cet événement.</span><span class="sxs-lookup"><span data-stu-id="b7390-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="b7390-158">Résoudre les problèmes de déchargement</span><span class="sxs-lookup"><span data-stu-id="b7390-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="b7390-159">En raison de la nature coopérative du déchargement, il est facile d’oublier les références qui peuvent conserver le contenu dans un `AssemblyLoadContext` de l’objets de suivi actif et empêcher le déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="b7390-160">Voici un résumé des entités (certaines d’entre elles non évidentes) qui peuvent contenir les références :</span><span class="sxs-lookup"><span data-stu-id="b7390-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="b7390-161">Les références régulières détenues de l’extérieur de l' `AssemblyLoadContext` pouvant être collectées et stockées dans un emplacement de pile ou un registre de processeur (variables locales, créées explicitement par le code utilisateur ou implicitement par le compilateur juste-à-temps (JIT)), une variable statique ou un handle de GC fort (épinglage) et pointant vers :</span><span class="sxs-lookup"><span data-stu-id="b7390-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="b7390-162">Un assembly chargé dans l’`AssemblyLoadContext` pouvant être collecté.</span><span class="sxs-lookup"><span data-stu-id="b7390-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="b7390-163">Un type d’un tel assembly.</span><span class="sxs-lookup"><span data-stu-id="b7390-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="b7390-164">Une instance d’un type à partir d’un tel assembly.</span><span class="sxs-lookup"><span data-stu-id="b7390-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="b7390-165">Threads exécutant du code à partir d’un assembly chargé dans l’`AssemblyLoadContext` pouvant être collecté.</span><span class="sxs-lookup"><span data-stu-id="b7390-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="b7390-166">Instances de types de `AssemblyLoadContext` personnalisés et non collectés créés à l’intérieur du `AssemblyLoadContext`pouvant être collecté.</span><span class="sxs-lookup"><span data-stu-id="b7390-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="b7390-167">Instances de <xref:System.Threading.RegisteredWaitHandle> en attente avec des rappels définis sur les méthodes dans le `AssemblyLoadContext`personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b7390-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="b7390-168">Les références d’objet qui sont stockées dans des emplacements de pile ou des registres de processeur et qui peuvent empêcher le déchargement d’un `AssemblyLoadContext` peuvent se produire dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7390-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="b7390-169">Lorsque les résultats de l’appel de fonction sont passés directement à une autre fonction, même s’il n’y a aucune variable locale créée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7390-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="b7390-170">Quand le compilateur JIT conserve une référence à un objet qui était disponible à un moment donné dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="b7390-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="b7390-171">Déboguer les problèmes de déchargement</span><span class="sxs-lookup"><span data-stu-id="b7390-171">Debug unloading issues</span></span>

<span data-ttu-id="b7390-172">Le débogage des problèmes de déchargement peut être fastidieux.</span><span class="sxs-lookup"><span data-stu-id="b7390-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="b7390-173">Vous pouvez vous retrouver dans des situations où le déchargement échoue sans que vous sachiez ce qui maintient un `AssemblyLoadContext` actif.</span><span class="sxs-lookup"><span data-stu-id="b7390-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="b7390-174">Le meilleur moyen de résoudre ce genre de problème est d’utiliser WinDbg (LLDB sur UNIX) avec le plug-in SOS.</span><span class="sxs-lookup"><span data-stu-id="b7390-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="b7390-175">Vous devez déterminer ce qui fait qu’un `LoaderAllocator` appartenant à l’`AssemblyLoadContext` donné reste actif.</span><span class="sxs-lookup"><span data-stu-id="b7390-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="b7390-176">Le plug-in SOS vous permet d’examiner les objets du tas GC, leurs hiérarchies et leurs racines.</span><span class="sxs-lookup"><span data-stu-id="b7390-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="b7390-177">Pour charger le plug-in dans le débogueur, entrez la commande suivante dans la ligne de commande du débogueur :</span><span class="sxs-lookup"><span data-stu-id="b7390-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="b7390-178">Dans WinDbg (apparemment, WinDbg le fait automatiquement quand il s’arrête dans une application .NET Core) :</span><span class="sxs-lookup"><span data-stu-id="b7390-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="b7390-179">Dans LLDB :</span><span class="sxs-lookup"><span data-stu-id="b7390-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="b7390-180">Déboguez un exemple de programme qui rencontre des problèmes de déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="b7390-181">Le code source est inclus ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b7390-181">Source code is included below.</span></span> <span data-ttu-id="b7390-182">Quand vous l’exécutez sous WinDbg, le programme s’arrête dans le débogueur juste après la tentative de vérification de la réussite du déchargement.</span><span class="sxs-lookup"><span data-stu-id="b7390-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="b7390-183">Vous pouvez ensuite commencer à rechercher les coupables.</span><span class="sxs-lookup"><span data-stu-id="b7390-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="b7390-184">Si vous déboguez à l’aide de LLDB sur UNIX, les commandes SOS dans les exemples suivants n’ont pas les `!` devant elles.</span><span class="sxs-lookup"><span data-stu-id="b7390-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="b7390-185">Cette commande vide tous les objets dont le nom de type contient `LoaderAllocator` et qui se trouvent dans le tas GC.</span><span class="sxs-lookup"><span data-stu-id="b7390-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="b7390-186">Voici un exemple : </span><span class="sxs-lookup"><span data-stu-id="b7390-186">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="b7390-187">Dans la partie « Statistics: » ci-dessous, examinez l’élément `MT` (`MethodTable`) appartenant à `System.Reflection.LoaderAllocator`, qui est l’objet qui nous intéresse.</span><span class="sxs-lookup"><span data-stu-id="b7390-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="b7390-188">Ensuite, dans la liste au début, recherchez l’entrée avec `MT` correspondant à celle-ci et obtenez l’adresse de l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="b7390-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="b7390-189">Dans notre cas, il s’agit de « 000002b78000ce40 ».</span><span class="sxs-lookup"><span data-stu-id="b7390-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="b7390-190">Maintenant que nous savons l’adresse de l’objet `LoaderAllocator`, nous pouvons utiliser une autre commande pour rechercher ses racines GC :</span><span class="sxs-lookup"><span data-stu-id="b7390-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="b7390-191">Cette commande vide la chaîne des références d’objet qui mènent à l’instance `LoaderAllocator`.</span><span class="sxs-lookup"><span data-stu-id="b7390-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="b7390-192">La liste commence par la racine, qui est l’entité qui garde notre `LoaderAllocator` actif et constitue donc le cœur du problème.</span><span class="sxs-lookup"><span data-stu-id="b7390-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="b7390-193">La racine peut être un emplacement de pile, un registre de processeur, un handle de GC ou une variable statique.</span><span class="sxs-lookup"><span data-stu-id="b7390-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="b7390-194">Voici un exemple de sortie de la commande `gcroot` :</span><span class="sxs-lookup"><span data-stu-id="b7390-194">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="b7390-195">L’étape suivante consiste à déterminer où se trouve la racine afin de pouvoir la corriger.</span><span class="sxs-lookup"><span data-stu-id="b7390-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="b7390-196">Dans le cas le plus simple, la racine est un emplacement de pile ou un registre de processeur.</span><span class="sxs-lookup"><span data-stu-id="b7390-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="b7390-197">Dans ce cas, le `gcroot` affiche le nom de la fonction dont le frame contient la racine et le thread qui exécute cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b7390-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="b7390-198">La situation est plus complexe quand la racine est une variable statique ou un handle de GC.</span><span class="sxs-lookup"><span data-stu-id="b7390-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="b7390-199">Dans l’exemple précédent, la première racine est un local de type `System.Reflection.RuntimeMethodInfo` stocké dans le frame de la fonction `example.Program.Main(System.String[])` à l’adresse `rbp-20` (`rbp` est le registre de processeur `rbp` et -20 est un décalage hexadécimal de ce registre).</span><span class="sxs-lookup"><span data-stu-id="b7390-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="b7390-200">La deuxième racine est un `GCHandle` normal (fort) qui contient une référence à une instance de la classe `test.Test`.</span><span class="sxs-lookup"><span data-stu-id="b7390-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="b7390-201">La troisième racine est un `GCHandle` épinglé.</span><span class="sxs-lookup"><span data-stu-id="b7390-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="b7390-202">Il s’agit en fait d’une variable statique, mais malheureusement, il n’existe aucun moyen de le savoir.</span><span class="sxs-lookup"><span data-stu-id="b7390-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="b7390-203">Les variables statiques pour les types références sont stockées dans un tableau d’objets managés dans des structures de runtime internes.</span><span class="sxs-lookup"><span data-stu-id="b7390-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="b7390-204">Le déchargement d’un `AssemblyLoadContext` peut aussi ne pas aboutir quand un thread a le frame d’une méthode d’un assembly chargé dans l’`AssemblyLoadContext` sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="b7390-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="b7390-205">Pour vérifier cela, videz les piles d’appels managées de tous les threads :</span><span class="sxs-lookup"><span data-stu-id="b7390-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="b7390-206">La commande signifie « appliquer à tous les threads la commande `!clrstack` ».</span><span class="sxs-lookup"><span data-stu-id="b7390-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="b7390-207">Voici la sortie de cette commande pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b7390-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="b7390-208">Malheureusement, LLDB sur UNIX n’a aucun moyen d’appliquer une commande à tous les threads. vous devez donc basculer manuellement les threads et répéter la commande `clrstack`.</span><span class="sxs-lookup"><span data-stu-id="b7390-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="b7390-209">Ignore tous les threads où le débogueur indique « Impossible de parcourir la pile managée ».</span><span class="sxs-lookup"><span data-stu-id="b7390-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

<span data-ttu-id="b7390-210">Comme vous pouvez le voir, le dernier thread a `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="b7390-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="b7390-211">Il s’agit d’une fonction de l’assembly chargé dans `AssemblyLoadContext` qui maintient `AssemblyLoadContext` actif.</span><span class="sxs-lookup"><span data-stu-id="b7390-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="b7390-212">Exemple de source avec des problèmes de déchargement</span><span class="sxs-lookup"><span data-stu-id="b7390-212">Example source with unloadability issues</span></span>

<span data-ttu-id="b7390-213">Le code suivant est utilisé dans l’exemple de débogage précédent.</span><span class="sxs-lookup"><span data-stu-id="b7390-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="b7390-214">Programme de test principal</span><span class="sxs-lookup"><span data-stu-id="b7390-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="b7390-215">Programme chargé dans TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="b7390-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="b7390-216">Le code suivant représente le *fichier test. dll* transmis à la méthode `ExecuteAndUnload` dans le programme de test principal.</span><span class="sxs-lookup"><span data-stu-id="b7390-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
