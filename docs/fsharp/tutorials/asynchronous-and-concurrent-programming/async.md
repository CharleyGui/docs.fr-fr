---
title: Programmation Async
description: Découvrez comment FMD fournit un soutien propre à l’asynchronie basé sur un modèle de programmation au niveau de la langue dérivé des concepts de programmation fonctionnelle de base.
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021521"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="32703-103">Programmation Async en F\#</span><span class="sxs-lookup"><span data-stu-id="32703-103">Async programming in F\#</span></span>

<span data-ttu-id="32703-104">La programmation asynchrone est un mécanisme qui est essentiel aux applications modernes pour diverses raisons.</span><span class="sxs-lookup"><span data-stu-id="32703-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="32703-105">Il y a deux cas d’utilisation primaire que la plupart des développeurs rencontreront :</span><span class="sxs-lookup"><span data-stu-id="32703-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="32703-106">Présentation d’un processus serveur qui peut traiter un nombre important de demandes entrantes simultanées, tout en minimisant les ressources système occupées pendant le traitement des demandes, vous attendez des entrées de systèmes ou de services externes à ce processus.</span><span class="sxs-lookup"><span data-stu-id="32703-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="32703-107">Maintenir une interface utilisateur ou un thread principal réactif tout en progressant simultanément dans les travaux d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="32703-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="32703-108">Bien que le travail de fond implique souvent l’utilisation de plusieurs threads, il est important de considérer les concepts d’asynchrone et multi-threading séparément.</span><span class="sxs-lookup"><span data-stu-id="32703-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="32703-109">En fait, il s’agit de préoccupations distinctes, et l’une n’implique pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="32703-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="32703-110">Cet article décrit plus en détail les concepts distincts.</span><span class="sxs-lookup"><span data-stu-id="32703-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="32703-111">Asynchrony défini</span><span class="sxs-lookup"><span data-stu-id="32703-111">Asynchrony defined</span></span>

<span data-ttu-id="32703-112">Le point précédent - que l’asynchronie est indépendante de l’utilisation de plusieurs threads - vaut la peine d’expliquer un peu plus loin.</span><span class="sxs-lookup"><span data-stu-id="32703-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="32703-113">Il y a trois concepts qui sont parfois liés, mais strictement indépendants les uns des autres :</span><span class="sxs-lookup"><span data-stu-id="32703-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="32703-114">La concurrence; lorsque plusieurs calculs s’exécutent dans des périodes de temps qui se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="32703-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="32703-115">Le parallélisme; lorsque plusieurs calculs ou plusieurs parties d’un calcul unique s’exécutent exactement en même temps.</span><span class="sxs-lookup"><span data-stu-id="32703-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="32703-116">Asynchrony; lorsqu’un ou plusieurs calculs peuvent s’exécuter séparément du flux principal du programme.</span><span class="sxs-lookup"><span data-stu-id="32703-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="32703-117">Tous les trois sont des concepts orthogonaux, mais peuvent être facilement confondus, surtout quand ils sont utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="32703-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="32703-118">Par exemple, vous devrez peut-être exécuter plusieurs calculs asynchrones en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="32703-119">Cette relation ne signifie pas que le parallélisme ou l’asynchrone s’impliquent les uns les autres.</span><span class="sxs-lookup"><span data-stu-id="32703-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="32703-120">Si vous considérez l’étymologie du mot «asynchrone», il ya deux pièces impliquées:</span><span class="sxs-lookup"><span data-stu-id="32703-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="32703-121">"a", c’est-à-dire "non".</span><span class="sxs-lookup"><span data-stu-id="32703-121">"a", meaning "not".</span></span>
- <span data-ttu-id="32703-122">"synchrone", c’est-à-dire "en même temps".</span><span class="sxs-lookup"><span data-stu-id="32703-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="32703-123">Lorsque vous mettez ces deux termes ensemble, vous verrez que "asynchrone" signifie "pas en même temps".</span><span class="sxs-lookup"><span data-stu-id="32703-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="32703-124">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="32703-124">That's it!</span></span> <span data-ttu-id="32703-125">Il n’y a aucune implication de concordance ou de parallélisme dans cette définition.</span><span class="sxs-lookup"><span data-stu-id="32703-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="32703-126">Cela est également vrai dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="32703-126">This is also true in practice.</span></span>

<span data-ttu-id="32703-127">Concrètement, les calculs asynchrones dans le F sont programmés pour exécuter indépendamment du flux principal du programme.</span><span class="sxs-lookup"><span data-stu-id="32703-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="32703-128">Cette exécution indépendante n’implique pas la concurrence ou le parallélisme, et cela n’implique pas non plus qu’un calcul se produise toujours en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="32703-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="32703-129">En fait, les calculs asynchrones peuvent même exécuter de façon synchrone, selon la nature du calcul et de l’environnement dans lequel le calcul est exécuté.</span><span class="sxs-lookup"><span data-stu-id="32703-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="32703-130">Le principal plat à emporter que vous devriez avoir est que les calculs asynchrones sont indépendants du flux principal du programme.</span><span class="sxs-lookup"><span data-stu-id="32703-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="32703-131">Bien qu’il y ait peu de garanties quant au moment ou à la façon dont un calcul asynchrone s’exécute, il existe quelques approches pour les orchestrer et les planifier.</span><span class="sxs-lookup"><span data-stu-id="32703-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="32703-132">Le reste de cet article explore les concepts de base pour l’asynchrone de F et comment utiliser les types, les fonctions et les expressions intégrées dans le F.</span><span class="sxs-lookup"><span data-stu-id="32703-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="32703-133">Principaux concepts</span><span class="sxs-lookup"><span data-stu-id="32703-133">Core concepts</span></span>

<span data-ttu-id="32703-134">Dans la programmation asynchrone, la programmation asynchrone est centrée autour de trois concepts fondamentaux :</span><span class="sxs-lookup"><span data-stu-id="32703-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="32703-135">Le `Async<'T>` type, qui représente un calcul asynchrone composable.</span><span class="sxs-lookup"><span data-stu-id="32703-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="32703-136">Les `Async` fonctions du module, qui vous permettent de planifier des travaux asynchrones, de composer des calculs asynchrones, et de transformer des résultats asynchrones.</span><span class="sxs-lookup"><span data-stu-id="32703-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="32703-137">`async { }` [L’expression de calcul](../../language-reference/computation-expressions.md), qui fournit une syntaxe pratique pour la construction et le contrôle des calculs asynchrones.</span><span class="sxs-lookup"><span data-stu-id="32703-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="32703-138">Vous pouvez voir ces trois concepts dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="32703-138">You can see these three concepts in the following example:</span></span>

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

<span data-ttu-id="32703-139">Dans l’exemple, la `printTotalFileBytes` `string -> Async<unit>`fonction est de type .</span><span class="sxs-lookup"><span data-stu-id="32703-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="32703-140">Appeler la fonction n’exécute pas réellement le calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="32703-141">Au lieu de `Async<unit>` cela, il renvoie un qui agit comme une *spécification* de l’œuvre qui est d’exécuter asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="32703-142">Il `Async.AwaitTask` appelle dans son corps, qui <xref:System.IO.File.ReadAllBytesAsync%2A> convertit le résultat d’un type approprié.</span><span class="sxs-lookup"><span data-stu-id="32703-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="32703-143">Une autre ligne importante `Async.RunSynchronously`est l’appel à .</span><span class="sxs-lookup"><span data-stu-id="32703-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="32703-144">Il s’agit de l’une des fonctions de démarrage du module Async que vous aurez besoin d’appeler si vous voulez réellement exécuter un calcul asynchrone F.</span><span class="sxs-lookup"><span data-stu-id="32703-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="32703-145">Il s’agit d’une différence fondamentale `async` avec le style de programmation de base visuelle et C.</span><span class="sxs-lookup"><span data-stu-id="32703-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="32703-146">Dans les calculs asynchrones, on peut penser que les tâches froides sont considérées comme **des tâches froides.**</span><span class="sxs-lookup"><span data-stu-id="32703-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="32703-147">Ils doivent être explicitement commencés à exécuter réellement.</span><span class="sxs-lookup"><span data-stu-id="32703-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="32703-148">Cela a quelques avantages, car il vous permet de combiner et séquencer un travail asynchrone beaucoup plus facilement que dans C ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32703-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="32703-149">Combinez des calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="32703-149">Combine asynchronous computations</span></span>

<span data-ttu-id="32703-150">Voici un exemple qui s’appuie sur le précédent en combinant les calculs :</span><span class="sxs-lookup"><span data-stu-id="32703-150">Here is an example that builds upon the previous one by combining computations:</span></span>

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

<span data-ttu-id="32703-151">Comme vous pouvez `main` le voir, la fonction a un peu plus d’appels effectués.</span><span class="sxs-lookup"><span data-stu-id="32703-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="32703-152">Conceptuellement, il fait ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="32703-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="32703-153">Transformez les arguments `Async<unit>` de la ligne `Array.map`de commande en calculs avec .</span><span class="sxs-lookup"><span data-stu-id="32703-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="32703-154">Créez `Async<'T[]>` un qui planifie `printTotalFileBytes` et exécute les calculs en parallèle quand il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="32703-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="32703-155">Créez `Async<unit>` un calcul parallèle qui exécutera le calcul parallèle et ignorera son résultat.</span><span class="sxs-lookup"><span data-stu-id="32703-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="32703-156">Exécutez explicitement le dernier `Async.RunSynchronously` calcul avec et bloquez jusqu’à ce qu’il se termine.</span><span class="sxs-lookup"><span data-stu-id="32703-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="32703-157">Lorsque ce programme `printTotalFileBytes` s’exécute, fonctionne en parallèle pour chaque argument de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="32703-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="32703-158">Parce que les calculs asynchrones exécutent indépendamment du flux de programme, il n’y a aucun ordre dans lequel ils impriment leurs informations et finissent d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="32703-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="32703-159">Les calculs seront programmés en parallèle, mais leur ordre d’exécution n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="32703-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="32703-160">Séquences de calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="32703-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="32703-161">Parce `Async<'T>` que c’est une spécification du travail plutôt qu’une tâche déjà en cours d’exécution, vous pouvez effectuer des transformations plus complexes facilement.</span><span class="sxs-lookup"><span data-stu-id="32703-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="32703-162">Voici un exemple qui séquence un ensemble de calculs Async afin qu’ils s’exécutent l’un après l’autre.</span><span class="sxs-lookup"><span data-stu-id="32703-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

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

<span data-ttu-id="32703-163">Cela permettra `printTotalFileBytes` d’exécuter dans l’ordre des éléments de plutôt que de `argv` les planifier en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="32703-164">Étant donné que le prochain élément ne sera programmé qu’après la fin de l’exécution du dernier calcul, les calculs sont séquencés de telle sorte qu’il n’y ait pas de chevauchement dans leur exécution.</span><span class="sxs-lookup"><span data-stu-id="32703-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="32703-165">Fonctions importantes du module Async</span><span class="sxs-lookup"><span data-stu-id="32703-165">Important Async module functions</span></span>

<span data-ttu-id="32703-166">Lorsque vous écrivez du code async en F, vous interagissez généralement avec un cadre qui gère la planification des calculs pour vous.</span><span class="sxs-lookup"><span data-stu-id="32703-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="32703-167">Cependant, ce n’est pas toujours le cas, il est donc bon d’apprendre les différentes fonctions de départ pour planifier un travail asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="32703-168">Étant donné que les calculs asynchrones de F sont une _spécification_ du travail plutôt qu’une représentation du travail qui est déjà en cours d’exécution, elles doivent être explicitement commencées par une fonction de départ.</span><span class="sxs-lookup"><span data-stu-id="32703-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="32703-169">Il existe de nombreuses [fonctions de départ Async](https://msdn.microsoft.com/library/ee370232.aspx) qui sont utiles dans différents contextes.</span><span class="sxs-lookup"><span data-stu-id="32703-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="32703-170">La section suivante décrit certaines des fonctions de départ les plus courantes.</span><span class="sxs-lookup"><span data-stu-id="32703-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="32703-171">Async.StartChild</span><span class="sxs-lookup"><span data-stu-id="32703-171">Async.StartChild</span></span>

<span data-ttu-id="32703-172">Commence un calcul pour enfant dans un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="32703-173">Cela permet d’exécuter plusieurs calculs asynchrones en même temps.</span><span class="sxs-lookup"><span data-stu-id="32703-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="32703-174">Le calcul de l’enfant partage un jeton d’annulation avec le calcul parent.</span><span class="sxs-lookup"><span data-stu-id="32703-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="32703-175">Si le calcul parent est annulé, le calcul de l’enfant est également annulé.</span><span class="sxs-lookup"><span data-stu-id="32703-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="32703-176">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="32703-177">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-177">When to use:</span></span>

- <span data-ttu-id="32703-178">Lorsque vous voulez exécuter plusieurs calculs asynchrones en même temps plutôt qu’un à la fois, mais ne pas les avoir programmés en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="32703-179">Lorsque vous souhaitez lier la durée de vie d’un calcul enfant à celui d’un calcul parent.</span><span class="sxs-lookup"><span data-stu-id="32703-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="32703-180">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-180">What to watch out for:</span></span>

- <span data-ttu-id="32703-181">Démarrer plusieurs calculs avec `Async.StartChild` n’est pas la même chose que de les planifier en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="32703-182">Si vous souhaitez planifier les calculs en `Async.Parallel`parallèle, utilisez .</span><span class="sxs-lookup"><span data-stu-id="32703-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="32703-183">L’annulation d’un calcul parent déclenchera l’annulation de tous les calculs d’enfants qu’elle a commencés.</span><span class="sxs-lookup"><span data-stu-id="32703-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="32703-184">Async.StartImmediate</span><span class="sxs-lookup"><span data-stu-id="32703-184">Async.StartImmediate</span></span>

<span data-ttu-id="32703-185">Exécute un calcul asynchrone, en commençant immédiatement sur le thread du système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="32703-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="32703-186">Ceci est utile si vous avez besoin de mettre à jour quelque chose sur le fil d’appel pendant le calcul.</span><span class="sxs-lookup"><span data-stu-id="32703-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="32703-187">Par exemple, si un calcul asynchrone doit mettre à jour une interface `Async.StartImmediate` utilisateur (comme la mise à jour d’une barre de progression), il faut alors l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="32703-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="32703-188">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="32703-189">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-189">When to use:</span></span>

- <span data-ttu-id="32703-190">Lorsque vous avez besoin de mettre à jour quelque chose sur le fil d’appel au milieu d’un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="32703-191">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-191">What to watch out for:</span></span>

- <span data-ttu-id="32703-192">Code dans le calcul asynchrone s’exécutera sur n’importe quel fil on se trouve être programmé sur.</span><span class="sxs-lookup"><span data-stu-id="32703-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="32703-193">Cela peut être problématique si ce thread est en quelque sorte sensible, comme un thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="32703-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="32703-194">Dans de `Async.StartImmediate` tels cas, est probablement inapproprié à utiliser.</span><span class="sxs-lookup"><span data-stu-id="32703-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="32703-195">Async.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="32703-195">Async.StartAsTask</span></span>

<span data-ttu-id="32703-196">Exécute un calcul dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="32703-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="32703-197">Renvoie <xref:System.Threading.Tasks.Task%601> un qui sera complété sur l’état correspondant une fois que le calcul se termine (produit le résultat, jette l’exception, ou obtient annulé).</span><span class="sxs-lookup"><span data-stu-id="32703-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="32703-198">Si aucun jeton d’annulation n’est fourni, alors le jeton d’annulation par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="32703-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="32703-199">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="32703-200">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-200">When to use:</span></span>

- <span data-ttu-id="32703-201">Lorsque vous avez besoin d’appeler dans <xref:System.Threading.Tasks.Task%601> un API .NET qui s’attend à un pour représenter le résultat d’un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="32703-202">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-202">What to watch out for:</span></span>

- <span data-ttu-id="32703-203">Cet appel allouera `Task` un objet supplémentaire, qui peut augmenter les frais généraux s’il est utilisé souvent.</span><span class="sxs-lookup"><span data-stu-id="32703-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="32703-204">Async.Parallèle</span><span class="sxs-lookup"><span data-stu-id="32703-204">Async.Parallel</span></span>

<span data-ttu-id="32703-205">Planifie une séquence de calculs asynchrones à exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="32703-206">Le degré de parallélisme peut être réglé/étranglé `maxDegreesOfParallelism` en spécifiant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="32703-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="32703-207">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="32703-208">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-208">When to use it:</span></span>

- <span data-ttu-id="32703-209">Si vous avez besoin d’exécuter un ensemble de calculs en même temps et ne vous fiez pas à leur ordre d’exécution.</span><span class="sxs-lookup"><span data-stu-id="32703-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="32703-210">Si vous n’avez pas besoin de résultats de calculs programmés en parallèle jusqu’à ce qu’ils aient tous terminé.</span><span class="sxs-lookup"><span data-stu-id="32703-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="32703-211">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-211">What to watch out for:</span></span>

- <span data-ttu-id="32703-212">Vous ne pouvez accéder à la gamme de valeurs résultante qu’une fois que tous les calculs ont été terminés.</span><span class="sxs-lookup"><span data-stu-id="32703-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="32703-213">Les calculs seront exécutés chaque fois qu’ils finissent par être programmés.</span><span class="sxs-lookup"><span data-stu-id="32703-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="32703-214">Ce comportement signifie que vous ne pouvez pas compter sur leur ordre de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="32703-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="32703-215">Async.Sequential</span><span class="sxs-lookup"><span data-stu-id="32703-215">Async.Sequential</span></span>

<span data-ttu-id="32703-216">Planifie une séquence de calculs asynchrones à exécuter dans l’ordre de leur passage.</span><span class="sxs-lookup"><span data-stu-id="32703-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="32703-217">Le premier calcul sera exécuté, puis le suivant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="32703-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="32703-218">Aucun calcul ne sera exécuté en parallèle.</span><span class="sxs-lookup"><span data-stu-id="32703-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="32703-219">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="32703-220">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-220">When to use it:</span></span>

- <span data-ttu-id="32703-221">Si vous avez besoin d’exécuter plusieurs calculs dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="32703-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="32703-222">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-222">What to watch out for:</span></span>

- <span data-ttu-id="32703-223">Vous ne pouvez accéder à la gamme de valeurs résultante qu’une fois que tous les calculs ont été terminés.</span><span class="sxs-lookup"><span data-stu-id="32703-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="32703-224">Les calculs seront exécutés dans l’ordre qu’ils sont transmis à cette fonction, ce qui peut signifier que plus de temps s’écoulera avant que les résultats soient retournés.</span><span class="sxs-lookup"><span data-stu-id="32703-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="32703-225">Async.AwaitTask</span><span class="sxs-lookup"><span data-stu-id="32703-225">Async.AwaitTask</span></span>

<span data-ttu-id="32703-226">Retourne un calcul asynchrone qui attend que <xref:System.Threading.Tasks.Task%601> la donnée soit complète et retourne son résultat en tant que`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="32703-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="32703-227">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="32703-228">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-228">When to use:</span></span>

- <span data-ttu-id="32703-229">Lorsque vous consommez un API <xref:System.Threading.Tasks.Task%601> .NET qui renvoie un dans un calcul asynchrone F.</span><span class="sxs-lookup"><span data-stu-id="32703-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="32703-230">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-230">What to watch out for:</span></span>

- <span data-ttu-id="32703-231">Des exceptions <xref:System.AggregateException> sont enveloppées dans la suite de la convention de la Bibliothèque parallèle de tâche, et ce comportement est différent de la façon dont F 'async fait généralement surface exceptions.</span><span class="sxs-lookup"><span data-stu-id="32703-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="32703-232">Async.Catch</span><span class="sxs-lookup"><span data-stu-id="32703-232">Async.Catch</span></span>

<span data-ttu-id="32703-233">Crée un calcul asynchrone qui exécute `Async<'T>`un donné `Async<Choice<'T, exn>>`, le retour d’un .</span><span class="sxs-lookup"><span data-stu-id="32703-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="32703-234">Si l’donnée `Async<'T>` se termine `Choice1Of2` avec succès, alors un est retourné avec la valeur résultante.</span><span class="sxs-lookup"><span data-stu-id="32703-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="32703-235">Si une exception est lancée avant `Choice2of2` qu’elle ne se termine, alors un est retourné à l’exception soulevée.</span><span class="sxs-lookup"><span data-stu-id="32703-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="32703-236">S’il est utilisé sur un calcul asynchrone qui est lui-même composé de nombreux calculs, et l’un de ces calculs jette une exception, le calcul englobant sera arrêté entièrement.</span><span class="sxs-lookup"><span data-stu-id="32703-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="32703-237">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="32703-238">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-238">When to use:</span></span>

- <span data-ttu-id="32703-239">Lorsque vous exécutez un travail asynchrone qui peut échouer à une exception près et vous voulez gérer cette exception dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="32703-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="32703-240">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-240">What to watch out for:</span></span>

- <span data-ttu-id="32703-241">Lors de l’utilisation de calculs asynchrones combinés ou séquencés, le calcul englobant s’arrêtera complètement si l’un de ses calculs « internes » jette une exception.</span><span class="sxs-lookup"><span data-stu-id="32703-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="32703-242">Async.Ignorer</span><span class="sxs-lookup"><span data-stu-id="32703-242">Async.Ignore</span></span>

<span data-ttu-id="32703-243">Crée un calcul asynchrone qui exécute le calcul donné et ignore son résultat.</span><span class="sxs-lookup"><span data-stu-id="32703-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="32703-244">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="32703-245">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-245">When to use:</span></span>

- <span data-ttu-id="32703-246">Lorsque vous avez un calcul asynchrone dont le résultat n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="32703-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="32703-247">Ceci est analogue `ignore` au code pour le code non asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="32703-248">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-248">What to watch out for:</span></span>

- <span data-ttu-id="32703-249">Si vous `Async.Ignore` devez utiliser parce `Async.Start` que vous `Async<unit>`souhaitez utiliser ou une autre fonction qui nécessite , considérez si jeter le résultat est correct.</span><span class="sxs-lookup"><span data-stu-id="32703-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="32703-250">Évitez de jeter les résultats juste pour s’adapter à une signature de type.</span><span class="sxs-lookup"><span data-stu-id="32703-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="32703-251">Async.RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="32703-251">Async.RunSynchronously</span></span>

<span data-ttu-id="32703-252">Exécute un calcul asynchrone et attend son résultat sur le fil d’appel.</span><span class="sxs-lookup"><span data-stu-id="32703-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="32703-253">Cet appel bloque.</span><span class="sxs-lookup"><span data-stu-id="32703-253">This call is blocking.</span></span>

<span data-ttu-id="32703-254">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="32703-255">Quand l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="32703-255">When to use it:</span></span>

- <span data-ttu-id="32703-256">Si vous en avez besoin, ne l’utilisez qu’une seule fois dans une application - au point d’entrée pour un exécutable.</span><span class="sxs-lookup"><span data-stu-id="32703-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="32703-257">Lorsque vous ne vous souciez pas des performances et que vous voulez exécuter un ensemble d’autres opérations asynchrones à la fois.</span><span class="sxs-lookup"><span data-stu-id="32703-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="32703-258">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-258">What to watch out for:</span></span>

- <span data-ttu-id="32703-259">L’appel `Async.RunSynchronously` bloque le fil d’appel jusqu’à ce que l’exécution se termine.</span><span class="sxs-lookup"><span data-stu-id="32703-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="32703-260">Async.Start</span><span class="sxs-lookup"><span data-stu-id="32703-260">Async.Start</span></span>

<span data-ttu-id="32703-261">Démarre un calcul asynchrone dans le pool `unit`de fil qui revient .</span><span class="sxs-lookup"><span data-stu-id="32703-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="32703-262">N’attend pas son résultat.</span><span class="sxs-lookup"><span data-stu-id="32703-262">Doesn't wait for its result.</span></span> <span data-ttu-id="32703-263">Les calculs imbriqués `Async.Start` commencés avec sont commencés indépendamment du calcul parent qui les a appelés.</span><span class="sxs-lookup"><span data-stu-id="32703-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="32703-264">Leur vie n’est liée à aucun calcul parent.</span><span class="sxs-lookup"><span data-stu-id="32703-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="32703-265">Si le calcul parent est annulé, aucun calcul pour enfants n’est annulé.</span><span class="sxs-lookup"><span data-stu-id="32703-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="32703-266">Signature :</span><span class="sxs-lookup"><span data-stu-id="32703-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="32703-267">Utiliser uniquement lorsque :</span><span class="sxs-lookup"><span data-stu-id="32703-267">Use only when:</span></span>

- <span data-ttu-id="32703-268">Vous avez un calcul asynchrone qui ne donne pas de résultat et/ou qui nécessite un traitement d’un.</span><span class="sxs-lookup"><span data-stu-id="32703-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="32703-269">Vous n’avez pas besoin de savoir quand un calcul asynchrone se termine.</span><span class="sxs-lookup"><span data-stu-id="32703-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="32703-270">Vous ne vous souciez pas quel fil d’un calcul asynchrone fonctionne sur.</span><span class="sxs-lookup"><span data-stu-id="32703-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="32703-271">Vous n’avez pas besoin d’être au courant ou de signaler les exceptions résultant de la tâche.</span><span class="sxs-lookup"><span data-stu-id="32703-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="32703-272">Ce qu’il faut surveiller :</span><span class="sxs-lookup"><span data-stu-id="32703-272">What to watch out for:</span></span>

- <span data-ttu-id="32703-273">Les exceptions soulevées par `Async.Start` les calculs commencés ne sont pas propagées à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="32703-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="32703-274">La pile d’appels sera complètement dénouée.</span><span class="sxs-lookup"><span data-stu-id="32703-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="32703-275">Tout travail (comme `printfn`l’appel) commencé par `Async.Start` ne fera pas l’effet de se produire sur le fil principal de l’exécution d’un programme.</span><span class="sxs-lookup"><span data-stu-id="32703-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="32703-276">Interopér l’interopérabilité avec .NET</span><span class="sxs-lookup"><span data-stu-id="32703-276">Interoperate with .NET</span></span>

<span data-ttu-id="32703-277">Vous pouvez travailler avec une bibliothèque .NET ou une base de code Cmd qui utilise une programmation asynchrone asynchrone [de](../../../standard/async.md)style asynchrone.</span><span class="sxs-lookup"><span data-stu-id="32703-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="32703-278">Parce que C et la majorité <xref:System.Threading.Tasks.Task%601> des <xref:System.Threading.Tasks.Task> bibliothèques .NET utilisent `Async<'T>`le et les types comme leurs abstractions de base plutôt que , vous devez franchir une frontière entre ces deux approches de l’asynchronie.</span><span class="sxs-lookup"><span data-stu-id="32703-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="32703-279">Comment travailler avec .NET async et`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="32703-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="32703-280">Travailler avec des bibliothèques async .NET <xref:System.Threading.Tasks.Task%601> et des bases de code qui utilisent (c’est-à-dire, des calculs async qui ont des valeurs de retour) est simple et a intégré le soutien avec F.</span><span class="sxs-lookup"><span data-stu-id="32703-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="32703-281">Vous pouvez `Async.AwaitTask` utiliser la fonction pour attendre un calcul asynchrone .NET:</span><span class="sxs-lookup"><span data-stu-id="32703-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="32703-282">Vous pouvez `Async.StartAsTask` utiliser la fonction pour passer un calcul asynchrone à un appelant .NET:</span><span class="sxs-lookup"><span data-stu-id="32703-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="32703-283">Comment travailler avec .NET async et`Task`</span><span class="sxs-lookup"><span data-stu-id="32703-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="32703-284">Pour travailler avec des <xref:System.Threading.Tasks.Task> API qui utilisent (c’est-à-dire les calculs async .NET qui ne `Async<'T>` retournent <xref:System.Threading.Tasks.Task>pas de valeur), vous devrez peut-être ajouter une fonction supplémentaire qui convertira un :</span><span class="sxs-lookup"><span data-stu-id="32703-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="32703-285">Il y `Async.AwaitTask` a déjà <xref:System.Threading.Tasks.Task> un qui accepte un comme contribution.</span><span class="sxs-lookup"><span data-stu-id="32703-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="32703-286">Avec ceci et `startTaskFromAsyncUnit` la fonction précédemment définie, vous pouvez commencer et attendre <xref:System.Threading.Tasks.Task> des types à partir d’un calcul d’async de F.</span><span class="sxs-lookup"><span data-stu-id="32703-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="32703-287">Relation à multi-threading</span><span class="sxs-lookup"><span data-stu-id="32703-287">Relationship to multi-threading</span></span>

<span data-ttu-id="32703-288">Bien que le filetage est mentionné tout au long de cet article, il ya deux choses importantes à retenir:</span><span class="sxs-lookup"><span data-stu-id="32703-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="32703-289">Il n’y a pas d’affinité entre un calcul asynchrone et un thread, à moins d’avoir explicitement commencé sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="32703-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="32703-290">La programmation asynchrone dans F n’est pas une abstraction pour le multi-threading.</span><span class="sxs-lookup"><span data-stu-id="32703-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="32703-291">Par exemple, un calcul peut effectivement s’exécuter sur le fil de son appelant, selon la nature de l’œuvre.</span><span class="sxs-lookup"><span data-stu-id="32703-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="32703-292">Un calcul pourrait également « sauter » entre les threads, les empruntant pour une petite quantité de temps pour faire un travail utile entre les périodes d'« attente » (comme lorsqu’un appel réseau est en transit).</span><span class="sxs-lookup"><span data-stu-id="32703-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="32703-293">Bien que F fournit certaines capacités pour démarrer un calcul asynchrone sur le thread actuel (ou explicitement pas sur le thread actuel), asynchrony n’est généralement pas associée à une stratégie de threading particulier.</span><span class="sxs-lookup"><span data-stu-id="32703-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="32703-294">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32703-294">See also</span></span>

- [<span data-ttu-id="32703-295">Le modèle de programmation asynchrone FMD</span><span class="sxs-lookup"><span data-stu-id="32703-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="32703-296">Guide de voyage De Jet.com’s FMD Async</span><span class="sxs-lookup"><span data-stu-id="32703-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="32703-297">F POUR le plaisir et le profit Asynchrone Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="32703-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="32703-298">Async en C et F: Gotchas asynchrones en C #</span><span class="sxs-lookup"><span data-stu-id="32703-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
