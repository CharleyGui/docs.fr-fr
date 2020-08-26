---
title: Programmation asynchrone
description: 'Découvrez comment F # fournit une prise en charge propre pour l’asynchronie basée sur un modèle de programmation au niveau du langage dérivé des concepts de programmation fonctionnelle de base.'
ms.date: 08/15/2020
ms.openlocfilehash: 2e5d4fb744b4443eb9caf90cc1bf01473b809127
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811767"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="86e2a-103">Programmation asynchrone en F\#</span><span class="sxs-lookup"><span data-stu-id="86e2a-103">Async programming in F\#</span></span>

<span data-ttu-id="86e2a-104">La programmation asynchrone est un mécanisme essentiel pour les applications modernes pour diverses raisons.</span><span class="sxs-lookup"><span data-stu-id="86e2a-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="86e2a-105">La plupart des développeurs rencontrent deux cas d’utilisation principaux :</span><span class="sxs-lookup"><span data-stu-id="86e2a-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="86e2a-106">Présentation d’un processus serveur qui peut traiter un nombre important de demandes entrantes simultanées, tout en minimisant les ressources système occupées pendant que le traitement des demandes attend les entrées des systèmes ou des services externes à ce processus</span><span class="sxs-lookup"><span data-stu-id="86e2a-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="86e2a-107">Maintien d’une interface utilisateur réactive ou d’un thread principal tout en progressant simultanément sur le travail en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="86e2a-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="86e2a-108">Bien que le travail en arrière-plan implique souvent l’utilisation de plusieurs threads, il est important de prendre en compte les concepts de l’asynchronie et du multithreading séparément.</span><span class="sxs-lookup"><span data-stu-id="86e2a-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="86e2a-109">En fait, il s’agit de problèmes distincts, et l’un n’implique pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="86e2a-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="86e2a-110">Cet article décrit plus en détail les concepts distincts.</span><span class="sxs-lookup"><span data-stu-id="86e2a-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="86e2a-111">Asynchronie défini</span><span class="sxs-lookup"><span data-stu-id="86e2a-111">Asynchrony defined</span></span>

<span data-ttu-id="86e2a-112">Le point précédent : l’asynchronie est indépendante de l’utilisation de plusieurs threads. il est donc judicieux d’expliquer un peu plus loin.</span><span class="sxs-lookup"><span data-stu-id="86e2a-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="86e2a-113">Trois concepts sont parfois liés, mais strictement indépendants les uns des autres :</span><span class="sxs-lookup"><span data-stu-id="86e2a-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="86e2a-114">D’accès concurrentiel Lorsque plusieurs calculs s’exécutent pendant le chevauchement de périodes.</span><span class="sxs-lookup"><span data-stu-id="86e2a-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="86e2a-115">Parallélisme Lorsque plusieurs calculs ou plusieurs parties d’un même calcul s’exécutent exactement à la même heure.</span><span class="sxs-lookup"><span data-stu-id="86e2a-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="86e2a-116">Asynchronie Lorsqu’un ou plusieurs calculs peuvent s’exécuter indépendamment du processus principal du programme.</span><span class="sxs-lookup"><span data-stu-id="86e2a-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="86e2a-117">Les trois sont des concepts orthogonaux, mais ils peuvent être facilement conplats, en particulier lorsqu’ils sont utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="86e2a-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="86e2a-118">Par exemple, vous devrez peut-être exécuter plusieurs calculs asynchrones en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="86e2a-119">Cette relation ne signifie pas que le parallélisme ou l’asynchronie impliquent l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="86e2a-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="86e2a-120">Si vous considérez le mot « Asynchronous » comme Etymology, deux éléments sont nécessaires :</span><span class="sxs-lookup"><span data-stu-id="86e2a-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="86e2a-121">« a », ce qui signifie « non ».</span><span class="sxs-lookup"><span data-stu-id="86e2a-121">"a", meaning "not".</span></span>
- <span data-ttu-id="86e2a-122">« synchrone », ce qui signifie « en même temps ».</span><span class="sxs-lookup"><span data-stu-id="86e2a-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="86e2a-123">Lorsque vous regroupez ces deux termes, vous verrez que « asynchrone » signifie « pas en même temps ».</span><span class="sxs-lookup"><span data-stu-id="86e2a-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="86e2a-124">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="86e2a-124">That's it!</span></span> <span data-ttu-id="86e2a-125">Il n’y a aucune implication de l’accès concurrentiel ou du parallélisme dans cette définition.</span><span class="sxs-lookup"><span data-stu-id="86e2a-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="86e2a-126">Cela est également vrai dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="86e2a-126">This is also true in practice.</span></span>

<span data-ttu-id="86e2a-127">En pratique, les calculs asynchrones en F # sont planifiés pour s’exécuter indépendamment du déroulement du programme principal.</span><span class="sxs-lookup"><span data-stu-id="86e2a-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="86e2a-128">Cette exécution indépendante n’implique pas la concurrence ou le parallélisme, et n’implique pas non plus qu’un calcul se produit toujours en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="86e2a-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="86e2a-129">En fait, les calculs asynchrones peuvent même s’exécuter de façon synchrone, en fonction de la nature du calcul et de l’environnement dans lequel le calcul s’exécute.</span><span class="sxs-lookup"><span data-stu-id="86e2a-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="86e2a-130">Le principal pas à pas est que les calculs asynchrones sont indépendants du processus principal du programme.</span><span class="sxs-lookup"><span data-stu-id="86e2a-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="86e2a-131">Bien qu’il existe peu de garanties quant au moment ou à l’exécution d’un calcul asynchrone, il existe des approches pour l’orchestration et la planification.</span><span class="sxs-lookup"><span data-stu-id="86e2a-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="86e2a-132">Le reste de cet article explore les concepts fondamentaux de l’asynchronie F # et explique comment utiliser les types, les fonctions et les expressions intégrés à F #.</span><span class="sxs-lookup"><span data-stu-id="86e2a-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="86e2a-133">Concepts principaux</span><span class="sxs-lookup"><span data-stu-id="86e2a-133">Core concepts</span></span>

<span data-ttu-id="86e2a-134">En F #, la programmation asynchrone est centrée autour de trois concepts fondamentaux :</span><span class="sxs-lookup"><span data-stu-id="86e2a-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="86e2a-135">`Async<'T>`Type, qui représente un calcul composable asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="86e2a-136">Les `Async` fonctions de module, qui vous permettent de planifier un travail asynchrone, de composer des calculs asynchrones et de transformer des résultats asynchrones.</span><span class="sxs-lookup"><span data-stu-id="86e2a-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="86e2a-137">L' `async { }` [expression de calcul](../../language-reference/computation-expressions.md), qui fournit une syntaxe pratique pour la génération et le contrôle des calculs asynchrones.</span><span class="sxs-lookup"><span data-stu-id="86e2a-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="86e2a-138">Vous pouvez voir ces trois concepts dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="86e2a-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="86e2a-139">Dans l’exemple, la `printTotalFileBytes` fonction est de type `string -> Async<unit>` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="86e2a-140">L’appel de la fonction n’exécute pas réellement le calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="86e2a-141">Au lieu de cela, elle retourne un `Async<unit>` qui agit comme une *spécification* du travail qui doit s’exécuter de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="86e2a-142">Il appelle `Async.AwaitTask` dans son corps, qui convertit le résultat de <xref:System.IO.File.ReadAllBytesAsync%2A> en un type approprié.</span><span class="sxs-lookup"><span data-stu-id="86e2a-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="86e2a-143">Une autre ligne importante est l’appel à `Async.RunSynchronously` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="86e2a-144">Il s’agit de l’une des fonctions de démarrage de module Async que vous devrez appeler si vous souhaitez réellement exécuter un calcul asynchrone F #.</span><span class="sxs-lookup"><span data-stu-id="86e2a-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="86e2a-145">Il s’agit d’une différence fondamentale avec le style de programmation C#/Visual Basic `async` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="86e2a-146">En F #, les calculs asynchrones peuvent être considérés comme des **tâches à froid**.</span><span class="sxs-lookup"><span data-stu-id="86e2a-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="86e2a-147">Ils doivent être démarrés explicitement pour s’exécuter réellement.</span><span class="sxs-lookup"><span data-stu-id="86e2a-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="86e2a-148">Cela présente des avantages, car elle vous permet de combiner et de séquencer un travail asynchrone bien plus facilement qu’en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86e2a-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="86e2a-149">Combiner des calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="86e2a-149">Combine asynchronous computations</span></span>

<span data-ttu-id="86e2a-150">Voici un exemple qui s’appuie sur le précédent en combinant des calculs :</span><span class="sxs-lookup"><span data-stu-id="86e2a-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="86e2a-151">Comme vous pouvez le voir, la `main` fonction a d’autres appels effectués.</span><span class="sxs-lookup"><span data-stu-id="86e2a-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="86e2a-152">D’un plan conceptuel, elle effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="86e2a-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="86e2a-153">Transformez les arguments de ligne de commande en `Async<unit>` calculs avec `Array.map` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="86e2a-154">Créez un `Async<'T[]>` qui planifie et exécute les `printTotalFileBytes` calculs en parallèle lorsqu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="86e2a-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="86e2a-155">Créez un `Async<unit>` qui exécutera le calcul parallèle et ignorez son résultat.</span><span class="sxs-lookup"><span data-stu-id="86e2a-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="86e2a-156">Exécute explicitement le dernier calcul avec `Async.RunSynchronously` et bloque jusqu’à ce qu’il se termine.</span><span class="sxs-lookup"><span data-stu-id="86e2a-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="86e2a-157">Lorsque ce programme s’exécute, `printTotalFileBytes` s’exécute en parallèle pour chaque argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="86e2a-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="86e2a-158">Étant donné que les calculs asynchrones s’exécutent indépendamment du déroulement du programme, il n’y a aucun ordre dans lequel ils impriment leurs informations et terminent leur exécution.</span><span class="sxs-lookup"><span data-stu-id="86e2a-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="86e2a-159">Les calculs sont planifiés en parallèle, mais leur ordre d’exécution n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="86e2a-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="86e2a-160">Séquencer des calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="86e2a-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="86e2a-161">Étant donné que `Async<'T>` est une spécification de travail plutôt qu’une tâche déjà en cours d’exécution, vous pouvez facilement effectuer des transformations plus complexes.</span><span class="sxs-lookup"><span data-stu-id="86e2a-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="86e2a-162">Voici un exemple qui séquence un ensemble de calculs asynchrones de sorte qu’ils s’exécutent l’un après l’autre.</span><span class="sxs-lookup"><span data-stu-id="86e2a-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="86e2a-163">Cela permet de planifier `printTotalFileBytes` l’exécution dans l’ordre des éléments de `argv` plutôt que de les planifier en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="86e2a-164">Étant donné que l’élément suivant n’est pas planifié tant que le dernier calcul n’a pas fini de s’exécuter, les calculs sont séquencés de telle sorte qu’il n’y a aucun chevauchement de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="86e2a-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="86e2a-165">Fonctions importantes du module Async</span><span class="sxs-lookup"><span data-stu-id="86e2a-165">Important Async module functions</span></span>

<span data-ttu-id="86e2a-166">Quand vous écrivez du code asynchrone en F #, vous interagissez généralement avec une infrastructure qui gère la planification des calculs pour vous.</span><span class="sxs-lookup"><span data-stu-id="86e2a-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="86e2a-167">Toutefois, ce n’est pas toujours le cas. il est donc judicieux d’apprendre les différentes fonctions de démarrage pour planifier un travail asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="86e2a-168">Étant donné que les calculs asynchrones F # sont une _spécification_ de travail plutôt qu’une représentation du travail qui est déjà en cours d’exécution, ils doivent être démarrés explicitement avec une fonction de démarrage.</span><span class="sxs-lookup"><span data-stu-id="86e2a-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="86e2a-169">De nombreuses [méthodes de démarrage asynchrones](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) sont utiles dans différents contextes.</span><span class="sxs-lookup"><span data-stu-id="86e2a-169">There are many [Async starting methods](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) that are helpful in different contexts.</span></span> <span data-ttu-id="86e2a-170">La section suivante décrit quelques-unes des fonctions de démarrage les plus courantes.</span><span class="sxs-lookup"><span data-stu-id="86e2a-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="86e2a-171">Async. StartChild</span><span class="sxs-lookup"><span data-stu-id="86e2a-171">Async.StartChild</span></span>

<span data-ttu-id="86e2a-172">Démarre un calcul enfant dans un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="86e2a-173">Cela permet l’exécution simultanée de plusieurs calculs asynchrones.</span><span class="sxs-lookup"><span data-stu-id="86e2a-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="86e2a-174">Le calcul enfant partage un jeton d’annulation avec le calcul parent.</span><span class="sxs-lookup"><span data-stu-id="86e2a-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="86e2a-175">Si le calcul parent est annulé, le calcul enfant est également annulé.</span><span class="sxs-lookup"><span data-stu-id="86e2a-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="86e2a-176">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="86e2a-177">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-177">When to use:</span></span>

- <span data-ttu-id="86e2a-178">Lorsque vous souhaitez exécuter plusieurs calculs asynchrones simultanément plutôt qu’un à la fois, mais que vous ne les avez pas planifiés en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="86e2a-179">Lorsque vous souhaitez lier la durée de vie d’un calcul enfant à celle d’un calcul parent.</span><span class="sxs-lookup"><span data-stu-id="86e2a-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="86e2a-180">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-180">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-181">Le démarrage de plusieurs calculs avec `Async.StartChild` n’est pas le même que pour les planifications en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="86e2a-182">Si vous souhaitez planifier des calculs en parallèle, utilisez `Async.Parallel` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="86e2a-183">L’annulation d’un calcul parent déclenchera l’annulation de tous les calculs enfants qu’il a démarrés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="86e2a-184">Async. StartImmediate</span><span class="sxs-lookup"><span data-stu-id="86e2a-184">Async.StartImmediate</span></span>

<span data-ttu-id="86e2a-185">Exécute un calcul asynchrone, en commençant immédiatement sur le thread de système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="86e2a-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="86e2a-186">Cela est utile si vous devez mettre à jour un événement sur le thread appelant pendant le calcul.</span><span class="sxs-lookup"><span data-stu-id="86e2a-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="86e2a-187">Par exemple, si un calcul asynchrone doit mettre à jour une interface utilisateur (telle que la mise à jour d’une barre de progression), `Async.StartImmediate` doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="86e2a-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="86e2a-188">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="86e2a-189">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-189">When to use:</span></span>

- <span data-ttu-id="86e2a-190">Lorsque vous devez mettre à jour un événement sur le thread appelant au milieu d’un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="86e2a-191">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-191">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-192">Le code dans le calcul asynchrone s’exécutera sur le thread sur lequel il se produit.</span><span class="sxs-lookup"><span data-stu-id="86e2a-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="86e2a-193">Cela peut être problématique si ce thread est sensible, par exemple un thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86e2a-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="86e2a-194">Dans ce cas, `Async.StartImmediate` il est probablement inapproprié d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="86e2a-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="86e2a-195">Async. StartAsTask</span><span class="sxs-lookup"><span data-stu-id="86e2a-195">Async.StartAsTask</span></span>

<span data-ttu-id="86e2a-196">Exécute un calcul dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="86e2a-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="86e2a-197">Retourne un <xref:System.Threading.Tasks.Task%601> qui sera terminé à l’état correspondant une fois le calcul terminé (produit le résultat, lève une exception ou est annulé).</span><span class="sxs-lookup"><span data-stu-id="86e2a-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="86e2a-198">Si aucun jeton d’annulation n’est fourni, le jeton d’annulation par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="86e2a-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="86e2a-199">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="86e2a-200">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-200">When to use:</span></span>

- <span data-ttu-id="86e2a-201">Lorsque vous devez appeler une API .NET qui s’attend à ce qu’un <xref:System.Threading.Tasks.Task%601> représente le résultat d’un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="86e2a-202">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-202">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-203">Cet appel va allouer un `Task` objet supplémentaire, ce qui peut augmenter la surcharge s’il est souvent utilisé.</span><span class="sxs-lookup"><span data-stu-id="86e2a-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="86e2a-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="86e2a-204">Async.Parallel</span></span>

<span data-ttu-id="86e2a-205">Planifie une séquence de calculs asynchrones à exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="86e2a-206">Le degré de parallélisme peut éventuellement être réglé/limité en spécifiant le `maxDegreesOfParallelism` paramètre.</span><span class="sxs-lookup"><span data-stu-id="86e2a-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="86e2a-207">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="86e2a-208">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-208">When to use it:</span></span>

- <span data-ttu-id="86e2a-209">Si vous devez exécuter un ensemble de calculs en même temps et que vous n’avez pas recours à leur ordre d’exécution.</span><span class="sxs-lookup"><span data-stu-id="86e2a-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="86e2a-210">Si vous n’avez pas besoin des résultats des calculs planifiés en parallèle jusqu’à ce qu’ils soient tous terminés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="86e2a-211">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-211">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-212">Vous ne pouvez accéder au tableau de valeurs résultant qu’une fois que tous les calculs sont terminés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="86e2a-213">Les calculs sont exécutés à chaque fois qu’ils finissent par être planifiés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="86e2a-214">Ce comportement signifie que vous ne pouvez pas compter sur leur ordre d’exécution.</span><span class="sxs-lookup"><span data-stu-id="86e2a-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="86e2a-215">Async. sequential</span><span class="sxs-lookup"><span data-stu-id="86e2a-215">Async.Sequential</span></span>

<span data-ttu-id="86e2a-216">Planifie l’exécution d’une séquence de calculs asynchrones dans l’ordre dans lequel ils sont passés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="86e2a-217">Le premier calcul sera exécuté, puis le suivant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="86e2a-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="86e2a-218">Aucun calcul n’est exécuté en parallèle.</span><span class="sxs-lookup"><span data-stu-id="86e2a-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="86e2a-219">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="86e2a-220">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-220">When to use it:</span></span>

- <span data-ttu-id="86e2a-221">Si vous devez exécuter plusieurs calculs dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="86e2a-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="86e2a-222">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-222">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-223">Vous ne pouvez accéder au tableau de valeurs résultant qu’une fois que tous les calculs sont terminés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="86e2a-224">Les calculs sont exécutés dans l’ordre dans lequel ils sont passés à cette fonction, ce qui peut signifier que plus de temps s’écoulera avant que les résultats ne soient retournés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="86e2a-225">Async. AwaitTask</span><span class="sxs-lookup"><span data-stu-id="86e2a-225">Async.AwaitTask</span></span>

<span data-ttu-id="86e2a-226">Retourne un calcul asynchrone qui attend que le donné <xref:System.Threading.Tasks.Task%601> se termine et retourne son résultat sous la forme d’un `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="86e2a-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="86e2a-227">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="86e2a-228">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-228">When to use:</span></span>

- <span data-ttu-id="86e2a-229">Lorsque vous consommez une API .NET qui retourne un <xref:System.Threading.Tasks.Task%601> dans un calcul asynchrone F #.</span><span class="sxs-lookup"><span data-stu-id="86e2a-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="86e2a-230">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-230">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-231">Les exceptions sont encapsulées en <xref:System.AggregateException> suivant la Convention de la bibliothèque parallèle de tâches, et ce comportement est différent de la façon dont F # Async recouvre généralement les exceptions.</span><span class="sxs-lookup"><span data-stu-id="86e2a-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="86e2a-232">Async. catch</span><span class="sxs-lookup"><span data-stu-id="86e2a-232">Async.Catch</span></span>

<span data-ttu-id="86e2a-233">Crée un calcul asynchrone qui exécute un donné `Async<'T>` , en retournant un `Async<Choice<'T, exn>>` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="86e2a-234">Si le donné `Async<'T>` se termine correctement, un `Choice1Of2` est retourné avec la valeur résultante.</span><span class="sxs-lookup"><span data-stu-id="86e2a-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="86e2a-235">Si une exception est levée avant qu’elle ne se termine, une `Choice2of2` est retournée avec l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="86e2a-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="86e2a-236">S’il est utilisé sur un calcul asynchrone qui est lui-même composé de plusieurs calculs, et que l’un de ces calculs lève une exception, le calcul englobant est arrêté entièrement.</span><span class="sxs-lookup"><span data-stu-id="86e2a-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="86e2a-237">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="86e2a-238">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-238">When to use:</span></span>

- <span data-ttu-id="86e2a-239">Lorsque vous effectuez un travail asynchrone qui peut échouer avec une exception et que vous souhaitez gérer cette exception dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="86e2a-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="86e2a-240">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-240">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-241">Lors de l’utilisation de calculs asynchrones combinés ou séquencés, le calcul englobant s’arrête entièrement si l’un de ses calculs « internes » lève une exception.</span><span class="sxs-lookup"><span data-stu-id="86e2a-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="86e2a-242">Async. ignore</span><span class="sxs-lookup"><span data-stu-id="86e2a-242">Async.Ignore</span></span>

<span data-ttu-id="86e2a-243">Crée un calcul asynchrone qui exécute le calcul donné et ignore son résultat.</span><span class="sxs-lookup"><span data-stu-id="86e2a-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="86e2a-244">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="86e2a-245">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-245">When to use:</span></span>

- <span data-ttu-id="86e2a-246">Quand vous avez un calcul asynchrone dont le résultat n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="86e2a-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="86e2a-247">Cela est analogue au `ignore` code pour le code non asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="86e2a-248">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-248">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-249">Si vous devez utiliser `Async.Ignore` parce que vous souhaitez utiliser `Async.Start` ou une autre fonction qui requiert `Async<unit>` , prenez en compte la possibilité d’ignorer le résultat.</span><span class="sxs-lookup"><span data-stu-id="86e2a-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="86e2a-250">Évitez d’ignorer les résultats pour qu’ils correspondent à une signature de type.</span><span class="sxs-lookup"><span data-stu-id="86e2a-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="86e2a-251">Async. RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="86e2a-251">Async.RunSynchronously</span></span>

<span data-ttu-id="86e2a-252">Exécute un calcul asynchrone et attend son résultat sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="86e2a-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="86e2a-253">Cet appel est bloquant.</span><span class="sxs-lookup"><span data-stu-id="86e2a-253">This call is blocking.</span></span>

<span data-ttu-id="86e2a-254">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="86e2a-255">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="86e2a-255">When to use it:</span></span>

- <span data-ttu-id="86e2a-256">Si vous en avez besoin, utilisez-le une seule fois dans une application, au point d’entrée d’un exécutable.</span><span class="sxs-lookup"><span data-stu-id="86e2a-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="86e2a-257">Lorsque vous ne vous souciez pas des performances et que vous souhaitez exécuter un ensemble d’autres opérations asynchrones à la fois.</span><span class="sxs-lookup"><span data-stu-id="86e2a-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="86e2a-258">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-258">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-259">L’appel `Async.RunSynchronously` de bloque le thread appelant jusqu’à ce que l’exécution se termine.</span><span class="sxs-lookup"><span data-stu-id="86e2a-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="86e2a-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="86e2a-260">Async.Start</span></span>

<span data-ttu-id="86e2a-261">Démarre un calcul asynchrone dans le pool de threads qui retourne `unit` .</span><span class="sxs-lookup"><span data-stu-id="86e2a-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="86e2a-262">N’attend pas son résultat.</span><span class="sxs-lookup"><span data-stu-id="86e2a-262">Doesn't wait for its result.</span></span> <span data-ttu-id="86e2a-263">Les calculs imbriqués démarrés avec `Async.Start` sont démarrés indépendamment du calcul parent qui les a appelés.</span><span class="sxs-lookup"><span data-stu-id="86e2a-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="86e2a-264">Leur durée de vie n’est pas liée à un calcul parent.</span><span class="sxs-lookup"><span data-stu-id="86e2a-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="86e2a-265">Si le calcul parent est annulé, aucun calcul enfant n’est annulé.</span><span class="sxs-lookup"><span data-stu-id="86e2a-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="86e2a-266">Signature :</span><span class="sxs-lookup"><span data-stu-id="86e2a-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="86e2a-267">À utiliser uniquement dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="86e2a-267">Use only when:</span></span>

- <span data-ttu-id="86e2a-268">Vous avez un calcul asynchrone qui ne génère pas de résultat et/ou nécessite le traitement d’un.</span><span class="sxs-lookup"><span data-stu-id="86e2a-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="86e2a-269">Vous n’avez pas besoin de savoir quand un calcul asynchrone se termine.</span><span class="sxs-lookup"><span data-stu-id="86e2a-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="86e2a-270">Vous ne vous souciez pas du thread sur lequel s’exécute un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86e2a-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="86e2a-271">Vous n’avez pas besoin de connaître ou de signaler les exceptions résultant de la tâche.</span><span class="sxs-lookup"><span data-stu-id="86e2a-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="86e2a-272">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="86e2a-272">What to watch out for:</span></span>

- <span data-ttu-id="86e2a-273">Les exceptions déclenchées par les calculs démarrés avec `Async.Start` ne sont pas propagées à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="86e2a-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="86e2a-274">La pile des appels sera complètement déroulée.</span><span class="sxs-lookup"><span data-stu-id="86e2a-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="86e2a-275">Tout travail (tel que `printfn` l’appel) démarré avec `Async.Start` n’entraînera pas l’effet sur le thread principal de l’exécution d’un programme.</span><span class="sxs-lookup"><span data-stu-id="86e2a-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="86e2a-276">Interagir avec .NET</span><span class="sxs-lookup"><span data-stu-id="86e2a-276">Interoperate with .NET</span></span>

<span data-ttu-id="86e2a-277">Vous travaillez peut-être avec une bibliothèque .NET ou un code base C# qui utilise la programmation asynchrone asynchrone [/await](../../../standard/async.md).</span><span class="sxs-lookup"><span data-stu-id="86e2a-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="86e2a-278">Étant donné que C# et la majorité des bibliothèques .NET utilisent les <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> types et comme leurs abstractions de base plutôt que `Async<'T>` , vous devez franchir une limite entre ces deux approches pour l’asynchronie.</span><span class="sxs-lookup"><span data-stu-id="86e2a-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="86e2a-279">Comment utiliser .NET Async et `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="86e2a-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="86e2a-280">L’utilisation des bibliothèques et des codes base .NET Async qui utilisent <xref:System.Threading.Tasks.Task%601> (autrement dit, des calculs asynchrones ayant des valeurs de retour) est simple et offre une prise en charge intégrée de F #.</span><span class="sxs-lookup"><span data-stu-id="86e2a-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="86e2a-281">Vous pouvez utiliser la `Async.AwaitTask` fonction pour attendre un calcul asynchrone .net :</span><span class="sxs-lookup"><span data-stu-id="86e2a-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="86e2a-282">Vous pouvez utiliser la `Async.StartAsTask` fonction pour passer un calcul asynchrone à un appelant .net :</span><span class="sxs-lookup"><span data-stu-id="86e2a-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="86e2a-283">Comment utiliser .NET Async et `Task`</span><span class="sxs-lookup"><span data-stu-id="86e2a-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="86e2a-284">Pour utiliser des API qui utilisent <xref:System.Threading.Tasks.Task> (autrement dit, les calculs asynchrones .net qui ne retournent pas de valeur), vous devrez peut-être ajouter une fonction supplémentaire qui convertit un `Async<'T>` en <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="86e2a-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="86e2a-285">Il existe déjà un `Async.AwaitTask` qui accepte un <xref:System.Threading.Tasks.Task> comme entrée.</span><span class="sxs-lookup"><span data-stu-id="86e2a-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="86e2a-286">Avec cette fonction et la fonction définie précédemment `startTaskFromAsyncUnit` , vous pouvez démarrer et attendre <xref:System.Threading.Tasks.Task> des types à partir d’un calcul F # Async.</span><span class="sxs-lookup"><span data-stu-id="86e2a-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="86e2a-287">Relation avec le Multi-Threading</span><span class="sxs-lookup"><span data-stu-id="86e2a-287">Relationship to multi-threading</span></span>

<span data-ttu-id="86e2a-288">Bien que le Threading soit mentionné tout au long de cet article, il y a deux points importants à retenir :</span><span class="sxs-lookup"><span data-stu-id="86e2a-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="86e2a-289">Il n’y a pas d’affinité entre un calcul asynchrone et un thread, à moins qu’il ne soit explicitement démarré sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="86e2a-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="86e2a-290">La programmation asynchrone en F # n’est pas une abstraction pour le Multi-Threading.</span><span class="sxs-lookup"><span data-stu-id="86e2a-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="86e2a-291">Par exemple, un calcul peut s’exécuter sur le thread de son appelant, en fonction de la nature du travail.</span><span class="sxs-lookup"><span data-stu-id="86e2a-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="86e2a-292">Un calcul peut également « sauter » entre les threads, ce qui les emprunte pendant une courte période pour effectuer un travail utile entre les périodes d’attente (par exemple, lorsqu’un appel réseau est en transit).</span><span class="sxs-lookup"><span data-stu-id="86e2a-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="86e2a-293">Bien que F # offre des capacités pour démarrer un calcul asynchrone sur le thread actuel (ou pas explicitement sur le thread actuel), l’asynchronie n’est généralement pas associé à une stratégie de thread particulière.</span><span class="sxs-lookup"><span data-stu-id="86e2a-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="86e2a-294">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86e2a-294">See also</span></span>

- [<span data-ttu-id="86e2a-295">Modèle de programmation asynchrone F #</span><span class="sxs-lookup"><span data-stu-id="86e2a-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="86e2a-296">Guide F # Async de jet. com</span><span class="sxs-lookup"><span data-stu-id="86e2a-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="86e2a-297">F # pour le Guide de programmation asynchrone du divertissement et des bénéfices</span><span class="sxs-lookup"><span data-stu-id="86e2a-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="86e2a-298">Async en C# et F # : pièges asynchrones en C #</span><span class="sxs-lookup"><span data-stu-id="86e2a-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
