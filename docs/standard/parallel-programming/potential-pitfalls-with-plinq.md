---
title: Pièges potentiels avec PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: b4d58734fba4b834d5f5819a6bf19da0b7b7e8db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285311"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="0ec0f-102">Pièges potentiels avec PLINQ</span><span class="sxs-lookup"><span data-stu-id="0ec0f-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="0ec0f-103">Dans de nombreux cas, PLINQ permet d’améliorer les performances de manière significative par rapport à des requêtes LINQ to Objects séquentielles.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="0ec0f-104">Toutefois, le travail de parallélisation de l’exécution de la requête présente une certaine complexité pouvant entraîner des problèmes qui, dans du code séquentiel, ne sont pas si courants ou ne surviennent pas du tout.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="0ec0f-105">Cette rubrique répertorie des pratiques à éviter lorsque vous écrivez des requêtes PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="0ec0f-106">Ne partez pas du principe que Parallel est toujours plus rapide</span><span class="sxs-lookup"><span data-stu-id="0ec0f-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="0ec0f-107">Parfois, la parallélisation entraîne l’exécution plus lente d’une requête PLINQ que son LINQ to Objects équivalent.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="0ec0f-108">La règle empirique de base veut que les requêtes ayant peu d’éléments source et des délégués utilisateurs rapides ne sont pas susceptibles d’apporter une grande accélération.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="0ec0f-109">Toutefois, étant donné que de nombreux facteurs sont impliqués dans les performances, nous vous recommandons de mesurer les résultats réels avant de décider si vous utiliserez PLINW.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="0ec0f-110">Pour plus d’informations, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0f-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="0ec0f-111">Éviter d’écrire dans des emplacements de mémoire partagée</span><span class="sxs-lookup"><span data-stu-id="0ec0f-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="0ec0f-112">Dans du code séquentiel, il n’est pas rare de lire des variables statiques ou d’écrire dans ces dernières ou dans des champs de classe.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="0ec0f-113">Toutefois, l’accès simultané de plusieurs threads à de telles variables entraîne un fort risque d’engorgement.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="0ec0f-114">Bien que vous puissiez utiliser des verrous pour synchroniser l’accès à la variable, le coût de synchronisation peut nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="0ec0f-115">Par conséquent, nous vous recommandons d’éviter, ou au moins de limiter autant que possible l’accès à un état partagé dans une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="0ec0f-116">Éviter les surparallélisations</span><span class="sxs-lookup"><span data-stu-id="0ec0f-116">Avoid over-parallelization</span></span>

<span data-ttu-id="0ec0f-117">À l’aide de la `AsParallel` méthode, vous encourez les frais généraux liés au partitionnement de la collection source et à la synchronisation des threads de travail.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="0ec0f-118">Les avantages de la parallélisation sont également limités par le nombre de processeurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="0ec0f-119">L’exécution de plusieurs threads liés au calcul sur un seul processeur ne permet aucune accélération.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="0ec0f-120">Par conséquent, vous devez veiller à ne pas surparalléliser une requête.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="0ec0f-121">Les requêtes imbriquées sont le scénario le plus courant dans lequel une surparallélisation peut se produire, comme le montre l’extrait suivant.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="0ec0f-122">Dans ce cas, il est préférable de paralléliser uniquement la source de données externe (clients), sauf si une ou plusieurs conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="0ec0f-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="0ec0f-123">La source de données interne (cust.Orders) est connue pour être très longue.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="0ec0f-124">Vous effectuez un calcul coûteux sur chaque commande.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="0ec0f-125">(l’opération montrée dans l’exemple n’est pas coûteuse)</span><span class="sxs-lookup"><span data-stu-id="0ec0f-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="0ec0f-126">Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads produits en parallélisant la requête sur `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="0ec0f-127">Dans tous les cas, le test et la mesure sont la meilleure façon de déterminer la forme de requête optimale.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="0ec0f-128">Pour plus d’informations, consultez [Comment : mesurer les performances des requêtes PLINQ](how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0f-128">For more information, see [How to: Measure PLINQ Query Performance](how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="0ec0f-129">Éviter les appels à des méthodes non thread-safe</span><span class="sxs-lookup"><span data-stu-id="0ec0f-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="0ec0f-130">L’écriture dans des méthodes d’instance qui ne sont pas thread-safe à partir d’une requête PLINQ peut entraîner une corruption des données qui peut être détectée ou non dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="0ec0f-131">Cela peut également entraîner des exceptions.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-131">It can also lead to exceptions.</span></span> <span data-ttu-id="0ec0f-132">Dans l’exemple suivant, plusieurs threads tenteraient d’appeler simultanément la méthode `FileStream.Write`, qui n’est pas prise en charge par la classe.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="0ec0f-133">Limiter les appels aux méthodes thread-safe</span><span class="sxs-lookup"><span data-stu-id="0ec0f-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="0ec0f-134">La plupart des méthodes statiques du .NET Framework sont thread-safe et peuvent être appelées à partir de plusieurs threads simultanément.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="0ec0f-135">Toutefois, même dans ces cas, la synchronisation impliquée peut entraîner un ralentissement significatif de la requête.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="0ec0f-136">Vous pouvez le tester vous-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="0ec0f-137">Bien que cette méthode soit utilisée dans les exemples de documentation destinés à la démonstration, ne l’utilisez pas dans les requêtes PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="0ec0f-138">Éviter les opérations de tri inutiles</span><span class="sxs-lookup"><span data-stu-id="0ec0f-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="0ec0f-139">Lorsque PLINQ exécute une requête en parallèle, il divise la séquence source en partitions qui peuvent être traitées simultanément sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="0ec0f-140">Par défaut, l’ordre dans lequel les partitions sont traitées et les résultats sont remis n’est pas prévisible (à l’exception des opérateurs tels que `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="0ec0f-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="0ec0f-141">Vous pouvez demander à PLINQ de conserver le classement de toute séquence source, mais cela a un impact négatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="0ec0f-142">Si possible, la meilleure pratique consiste à structurer les requêtes afin qu’elles ne reposent pas sur la conservation de l’ordre.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="0ec0f-143">Pour plus d’informations, consultez [Order Preservation in PLINQ](order-preservation-in-plinq.md) (Conservation de l’ordre dans PLINQ).</span><span class="sxs-lookup"><span data-stu-id="0ec0f-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="0ec0f-144">Préférer ForAll à ForEach quand c’est possible</span><span class="sxs-lookup"><span data-stu-id="0ec0f-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="0ec0f-145">Bien que PLINQ exécute une requête sur plusieurs threads, si vous consommez les résultats dans une boucle `foreach` (`For Each` en Visual Basic), les résultats de la requête doivent être fusionnés dans un thread et consultés de façon séquentielle par l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="0ec0f-146">Dans certains cas, c’est inévitable ; toutefois, si possible, utilisez la méthode `ForAll` pour activer chaque thread afin qu’il sorte ses propres résultats, par exemple, en écrivant dans une collection thread-safe, telle que <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0ec0f-147">Le même problème s’applique à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0ec0f-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0ec0f-148">En d’autres termes, `source.AsParallel().Where().ForAll(...)` doit être fortement préféré à `Parallel.ForEach(source.AsParallel().Where(), ...)` .</span><span class="sxs-lookup"><span data-stu-id="0ec0f-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="0ec0f-149">Tenez compte des problèmes d’affinité de thread</span><span class="sxs-lookup"><span data-stu-id="0ec0f-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="0ec0f-150">Certaines technologies, par exemple, les composants STA (Single-Threaded Apartment), Windows Forms et Windows Presentation Foundation (WPF) imposent des restrictions d’affinité de thread qui requièrent l’exécution de code sur un thread spécifique.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="0ec0f-151">Par exemple, dans Windows Forms et WPF, un contrôle est uniquement accessible sur le thread sur lequel il a été créé.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="0ec0f-152">Si vous essayez d’accéder à l’état partagé d’un contrôle Windows Forms dans une requête PLINQ, une exception est levée si vous exécutez dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="0ec0f-153">(Ce paramètre peut être désactivé.) Toutefois, si votre requête est consommée sur le thread d’interface utilisateur, vous pouvez accéder au contrôle à partir de la `foreach` boucle qui énumère les résultats de la requête, car ce code s’exécute sur un seul thread.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="0ec0f-154">Ne partez pas du principe que les itérations de ForEach, for et ForAll s’exécutent toujours en parallèle</span><span class="sxs-lookup"><span data-stu-id="0ec0f-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="0ec0f-155">Il est important de garder à l’esprit que les itérations individuelles dans une <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> boucle, ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> peuvent, mais n’ont pas besoin de s’exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="0ec0f-156">Par conséquent, vous devez éviter d’écrire du code dont l’exactitude dépend de l’exécution parallèle d’itérations ou de l’exécution d’itérations dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="0ec0f-157">Par exemple, ce code est susceptible d’interbloquer :</span><span class="sxs-lookup"><span data-stu-id="0ec0f-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="0ec0f-158">Dans cet exemple, une itération définit un événement que toutes les autres itérations attendent.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="0ec0f-159">Aucune des itérations en attente ne peut s’achever tant que l’itération de définition d’événement n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="0ec0f-160">Toutefois, il est possible que les itérations en attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant que l’itération de définition d’événement ait eu une chance de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="0ec0f-161">Cela provoque un interblocage : l’itération de définition d’événement ne s’exécute jamais et les itérations en attente ne s’activent pas non plus.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="0ec0f-162">En particulier, une itération de boucle parallèle ne doit jamais attendre une autre itération de la boucle pour progresser.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="0ec0f-163">Si la boucle parallèle décide de planifier les itérations de manière séquentielle, mais dans l’ordre inverse, un interblocage se produit.</span><span class="sxs-lookup"><span data-stu-id="0ec0f-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec0f-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ec0f-164">See also</span></span>

- [<span data-ttu-id="0ec0f-165">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0ec0f-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
