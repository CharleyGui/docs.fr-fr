---
title: Meilleures pratiques pour le threading managé
description: Découvrez les meilleures pratiques de Threading managé dans .NET. Travaillez avec des situations difficiles, telles que la coordination de nombreux threads ou la gestion des threads de blocage.
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: fa0af1461ba568583127316934b9d55577dd4c5a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662821"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="ae185-104">Bonnes pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="ae185-104">Managed threading best practices</span></span>
<span data-ttu-id="ae185-105">Le multithreading nécessite une programmation attentive.</span><span class="sxs-lookup"><span data-stu-id="ae185-105">Multithreading requires careful programming.</span></span> <span data-ttu-id="ae185-106">Pour réduire la complexité de la plupart des tâches, il vous suffit de mettre en file d’attente les requêtes à exécuter par les threads d’un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="ae185-106">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="ae185-107">Cet article vous permet de remédier aux situations plus complexes, telles que la coordination du travail de plusieurs threads ou la gestion des threads bloqués.</span><span class="sxs-lookup"><span data-stu-id="ae185-107">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae185-108">À partir de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API qui atténuent une partie de la complexité et des risques de la programmation multithread.</span><span class="sxs-lookup"><span data-stu-id="ae185-108">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="ae185-109">Pour plus d’informations, consultez la page [Programmation parallèle dans .NET](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae185-109">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="ae185-110">Interblocages et conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="ae185-110">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="ae185-111">Le multithreading résout les problèmes de débit et de réactivité, mais, ce faisant, occasionne de nouveaux problèmes : les interblocages et les conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="ae185-111">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="ae185-112">Blocages</span><span class="sxs-lookup"><span data-stu-id="ae185-112">Deadlocks</span></span>  
 <span data-ttu-id="ae185-113">Un interblocage se produit lorsque chacun des deux threads tente de verrouiller une ressource déjà verrouillée par l’autre thread.</span><span class="sxs-lookup"><span data-stu-id="ae185-113">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="ae185-114">Aucun des deux threads ne peut donc poursuivre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ae185-114">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="ae185-115">De nombreuses méthodes des classes de threading managé fournissent des délais d’expiration conçus pour faciliter la détection des interblocages.</span><span class="sxs-lookup"><span data-stu-id="ae185-115">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="ae185-116">Par exemple, le code ci-après tente d’acquérir un verrou sur un objet nommé `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="ae185-116">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="ae185-117">Si le verrou n’est pas obtenu en 300 millisecondes, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="ae185-117">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="ae185-118">Conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="ae185-118">Race conditions</span></span>  
 <span data-ttu-id="ae185-119">Une condition de concurrence est un bogue qui survient lorsque le résultat d’un programme dépend du thread qui atteint le premier un bloc de code spécifique.</span><span class="sxs-lookup"><span data-stu-id="ae185-119">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="ae185-120">L’exécution du programme à plusieurs reprises produit des résultats différents, et le résultat d’une exécution donnée n’est donc pas prévisible.</span><span class="sxs-lookup"><span data-stu-id="ae185-120">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="ae185-121">Un exemple simple de condition de concurrence correspond à l’incrémentation d’un champ.</span><span class="sxs-lookup"><span data-stu-id="ae185-121">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="ae185-122">Supposons qu’une classe comporte un champ **static** privé (**Shared** en Visual Basic) qui est incrémenté chaque fois qu’une instance de la classe est créée, à l’aide d’un code tel que `objCt++;` (C#) ou `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ae185-122">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="ae185-123">Cette opération nécessite le chargement de la valeur de `objCt` dans un registre, l’incrémentation de la valeur, puis son stockage dans `objCt`.</span><span class="sxs-lookup"><span data-stu-id="ae185-123">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="ae185-124">Dans une application multithread, il est possible qu’un thread ayant chargé et incrémenté la valeur soit devancé par un autre thread qui exécute ces trois étapes ; lorsque le premier thread reprend l’exécution et stocke sa valeur, il remplace alors la valeur de `objCt` sans tenir compte du fait qu’elle a changé dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="ae185-124">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="ae185-125">Cette condition de concurrence particulière est facile à éviter en utilisant des méthodes de la classe <xref:System.Threading.Interlocked>, telles que <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae185-125">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ae185-126">Pour découvrir d’autres techniques de synchronisation des données entre plusieurs threads, consultez l’article [Synchronisation des données pour le multithreading](synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="ae185-126">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="ae185-127">Des conditions de concurrence peuvent également survenir lorsque vous synchronisez les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="ae185-127">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="ae185-128">Chaque fois que vous écrivez une ligne de code, vous devez prendre en compte ce qui peut se produire si un thread est devancé par un autre thread avant d’avoir exécuté la ligne (ou avant toute instruction machine individuelle composant la ligne).</span><span class="sxs-lookup"><span data-stu-id="ae185-128">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="ae185-129">Membres static et constructeurs static</span><span class="sxs-lookup"><span data-stu-id="ae185-129">Static members and static constructors</span></span>  
 <span data-ttu-id="ae185-130">Une classe n’est pas initialisée tant que son constructeur de classe (constructeur `static` en C#, `Shared Sub New` en Visual Basic) n’a pas fini de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ae185-130">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="ae185-131">Pour empêcher l’exécution de code sur un type qui n’est pas initialisé, le common language runtime bloque tous les appels d’autres threads aux membres `static` de la classe (membres `Shared` en Visual Basic) jusqu’à la fin de l’exécution du constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="ae185-131">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="ae185-132">Par exemple, si un constructeur de classe démarre un nouveau thread, et que la procédure de thread appelle un membre `static` de la classe, le nouveau thread se bloque jusqu’à la fin du constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="ae185-132">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="ae185-133">Cela s’applique à n’importe quel type pouvant comporter un constructeur `static`.</span><span class="sxs-lookup"><span data-stu-id="ae185-133">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="ae185-134">Nombre de processeurs</span><span class="sxs-lookup"><span data-stu-id="ae185-134">Number of processors</span></span>

<span data-ttu-id="ae185-135">Le fait que plusieurs processeurs ou un seul soient disponibles sur un système peut influencer l’architecture multithread.</span><span class="sxs-lookup"><span data-stu-id="ae185-135">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="ae185-136">Pour plus d’informations, consultez [Nombre de processeurs](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="ae185-136">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="ae185-137">Utilisez la <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> propriété pour déterminer le nombre de processeurs disponibles au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ae185-137">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="ae185-138">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="ae185-138">General recommendations</span></span>  
 <span data-ttu-id="ae185-139">Lorsque vous utilisez plusieurs threads, tenez compte des recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae185-139">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="ae185-140">N’utilisez pas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour mettre fin à d’autres threads.</span><span class="sxs-lookup"><span data-stu-id="ae185-140">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="ae185-141">L’appel de la méthode **Abort** sur un autre thread équivaut à lever une exception sur ce dernier sans connaître le stade précis du traitement atteint par ce thread.</span><span class="sxs-lookup"><span data-stu-id="ae185-141">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="ae185-142">N’utilisez pas <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> pour synchroniser les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="ae185-142">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="ae185-143">Utilisez <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="ae185-143">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="ae185-144">Ne contrôlez pas l’exécution des threads de travail à partir de votre programme principal (à l’aide d’événements, par exemple).</span><span class="sxs-lookup"><span data-stu-id="ae185-144">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="ae185-145">Concevez plutôt votre programme pour que les threads de travail soient chargés d’attendre que le travail devienne disponible, d’exécuter ce travail, puis d’en informer les autres parties de votre programme lorsqu’ils ont terminé.</span><span class="sxs-lookup"><span data-stu-id="ae185-145">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="ae185-146">Si vos threads de travail ne se bloquent pas, envisagez d’utiliser les threads d’un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="ae185-146">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="ae185-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> est utile dans les situations où les threads de travail se bloquent.</span><span class="sxs-lookup"><span data-stu-id="ae185-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="ae185-148">N’utilisez pas de types en tant qu’objets de verrou.</span><span class="sxs-lookup"><span data-stu-id="ae185-148">Don't use types as lock objects.</span></span> <span data-ttu-id="ae185-149">Autrement dit, évitez un code tel que `lock(typeof(X))` en C# ou `SyncLock(GetType(X))` en Visual Basic, ou l’utilisation de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> avec des objets <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="ae185-149">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="ae185-150">Pour un type donné, il existe une seule instance de <xref:System.Type?displayProperty=nameWithType> par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ae185-150">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="ae185-151">Si le type sur lequel vous utilisez un verrou est public, un code différent du vôtre peut utiliser des verrous sur ce type, entraînant ainsi des interblocages.</span><span class="sxs-lookup"><span data-stu-id="ae185-151">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="ae185-152">Pour découvrir les autres problèmes, consultez l’article [Meilleures pratiques pour la fiabilité](../../framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="ae185-152">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="ae185-153">Procédez avec précaution lorsque vous utilisez des verrous sur des instances, par exemple `lock(this)` en C# ou `SyncLock(Me)` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae185-153">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="ae185-154">Si un autre code de votre application, externe au type, utilise un verrou sur l’objet, des interblocages risquent de se produire.</span><span class="sxs-lookup"><span data-stu-id="ae185-154">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="ae185-155">Assurez-vous qu’un thread entré dans un moniteur quitte toujours ce dernier, même si une exception se produit pendant que le thread se trouve dans le moniteur.</span><span class="sxs-lookup"><span data-stu-id="ae185-155">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="ae185-156">L’instruction C# [lock](../../csharp/language-reference/keywords/lock-statement.md) et l’instruction Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) assurent automatiquement ce comportement, en employant un bloc **finally** pour garantir l’appel de la méthode <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae185-156">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="ae185-157">Si vous n’êtes pas en mesure de garantir l’appel de la méthode **Exit**, vous pouvez modifier votre conception de façon à utiliser **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="ae185-157">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="ae185-158">Un mutex est automatiquement libéré lorsque le thread auquel il appartient a terminé.</span><span class="sxs-lookup"><span data-stu-id="ae185-158">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="ae185-159">Utilisez plusieurs threads pour les tâches qui nécessitent des ressources différentes, et évitez d’attribuer plusieurs threads à une même ressource.</span><span class="sxs-lookup"><span data-stu-id="ae185-159">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="ae185-160">Par exemple, vous tirerez avantage du fait que les tâches impliquant des E/S disposent de leur propre thread, car ce thread se bloquera lors des opérations d’E/S et permettra ainsi à d’autres threads de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ae185-160">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="ae185-161">L’entrée utilisateur est une autre ressource tirant profit d’un thread dédié.</span><span class="sxs-lookup"><span data-stu-id="ae185-161">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="ae185-162">Sur un ordinateur monoprocesseur, une tâche qui exige de multiples calculs coexiste avec l’entrée utilisateur et avec les tâches qui impliquent des E/S, mais plusieurs tâches nécessitant de nombreux calculs entrent en concurrence les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="ae185-162">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="ae185-163">Envisagez d’utiliser les méthodes de la classe <xref:System.Threading.Interlocked> pour les modifications d’état simples, plutôt que de recourir à l’instruction `lock` (`SyncLock` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ae185-163">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="ae185-164">L’instruction `lock` est un outil à usage général efficace, mais la classe <xref:System.Threading.Interlocked> offre de meilleures performances pour les mises à jour qui doivent être atomiques.</span><span class="sxs-lookup"><span data-stu-id="ae185-164">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="ae185-165">En interne, elle exécute un seul préfixe de verrou s’il n’existe aucun conflit.</span><span class="sxs-lookup"><span data-stu-id="ae185-165">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="ae185-166">Lors des phases de révision du code, examinez le code semblable à celui des exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ae185-166">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="ae185-167">Dans le premier exemple, une variable d’état est incrémentée :</span><span class="sxs-lookup"><span data-stu-id="ae185-167">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="ae185-168">Vous pouvez améliorer les performances en utilisant la méthode <xref:System.Threading.Interlocked.Increment%2A> au lieu de l’instruction`lock`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ae185-168">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="ae185-169">Dans .NET Framework 2.0 et les versions ultérieures, utilisez la méthode <xref:System.Threading.Interlocked.Add%2A> pour les incréments atomiques supérieurs à 1.</span><span class="sxs-lookup"><span data-stu-id="ae185-169">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="ae185-170">Dans le second exemple, une variable de type référence est uniquement mise à jour s’il s’agit d’une référence null (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ae185-170">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="ae185-171">Les performances peuvent être améliorées en utilisant à la place la méthode <xref:System.Threading.Interlocked.CompareExchange%2A> comme suit :</span><span class="sxs-lookup"><span data-stu-id="ae185-171">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="ae185-172">À compter de .NET Framework 2.0, la surcharge de méthode <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> fournit une alternative de type sécurisé pour les types référence.</span><span class="sxs-lookup"><span data-stu-id="ae185-172">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="ae185-173">Recommandations relatives aux bibliothèques de classes</span><span class="sxs-lookup"><span data-stu-id="ae185-173">Recommendations for class libraries</span></span>  
 <span data-ttu-id="ae185-174">Lorsque vous concevez des bibliothèques de classes pour le multithreading, tenez compte des recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae185-174">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="ae185-175">Dans la mesure du possible, évitez toute nécessité de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="ae185-175">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="ae185-176">Cette consigne s’applique tout particulièrement pour le code très sollicité.</span><span class="sxs-lookup"><span data-stu-id="ae185-176">This is especially true for heavily used code.</span></span> <span data-ttu-id="ae185-177">Par exemple, un algorithme peut être ajusté de façon à tolérer une condition de concurrence plutôt que de l’éliminer.</span><span class="sxs-lookup"><span data-stu-id="ae185-177">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="ae185-178">Une synchronisation inutile dégrade les performances et entraîne un risque d’interblocages et de conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="ae185-178">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="ae185-179">Définissez les données static (`Shared` en Visual Basic) comme thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae185-179">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="ae185-180">Ne définissez pas les données d’instance comme thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae185-180">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="ae185-181">L’ajout de verrous pour créer un code thread-safe diminue les performances, multiplie les conflits de verrou et occasionne un risque d’interblocages.</span><span class="sxs-lookup"><span data-stu-id="ae185-181">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="ae185-182">Dans les modèles d’application communs, le code utilisateur n’est exécuté que par un seul thread à la fois, ce qui minimise la nécessité d’une cohérence de thread.</span><span class="sxs-lookup"><span data-stu-id="ae185-182">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="ae185-183">C’est la raison pour laquelle les bibliothèques de classes .NET Framework ne sont pas thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae185-183">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="ae185-184">Évitez de fournir des méthodes statiques qui modifient l’état statique.</span><span class="sxs-lookup"><span data-stu-id="ae185-184">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="ae185-185">Dans les scénarios de serveur courants, l’état statique est partagé entre les requêtes, ce qui signifie que plusieurs threads peuvent exécuter ce code en même temps.</span><span class="sxs-lookup"><span data-stu-id="ae185-185">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="ae185-186">Ceci occasionne un risque de bogues de threading.</span><span class="sxs-lookup"><span data-stu-id="ae185-186">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="ae185-187">Envisagez d’utiliser un modèle de conception qui encapsule les données dans des instances non partagées entre les requêtes.</span><span class="sxs-lookup"><span data-stu-id="ae185-187">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="ae185-188">En outre, si les données static sont synchronisées, les appels entre les méthodes statiques qui modifient l’état peuvent entraîner des interblocages ou une synchronisation redondante et dégrader ainsi les performances.</span><span class="sxs-lookup"><span data-stu-id="ae185-188">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae185-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae185-189">See also</span></span>

- [<span data-ttu-id="ae185-190">Threads</span><span class="sxs-lookup"><span data-stu-id="ae185-190">Threading</span></span>](index.md)
- [<span data-ttu-id="ae185-191">Threads et threads</span><span class="sxs-lookup"><span data-stu-id="ae185-191">Threads and Threading</span></span>](threads-and-threading.md)
