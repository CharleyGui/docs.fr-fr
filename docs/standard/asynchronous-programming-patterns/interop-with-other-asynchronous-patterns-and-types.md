---
title: Interopérabilité avec d’autres types et modèles asynchrones
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 2ae1c514185152dd709fe06018df513fb54b874b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726715"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="dcf9c-102">Interopérabilité avec d’autres types et modèles asynchrones</span><span class="sxs-lookup"><span data-stu-id="dcf9c-102">Interop with Other Asynchronous Patterns and Types</span></span>

<span data-ttu-id="dcf9c-103">Bref historique des modèles asynchrones dans .NET :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-103">A brief history of asynchronous patterns in .NET:</span></span>

- <span data-ttu-id="dcf9c-104">.NET Framework 1,0 a introduit le <xref:System.IAsyncResult> modèle, également connu sous le nom de [modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md), ou le modèle `Begin/End` .</span><span class="sxs-lookup"><span data-stu-id="dcf9c-104">.NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>
- <span data-ttu-id="dcf9c-105">.NET Framework 2,0 a ajouté le [modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="dcf9c-105">.NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>
- <span data-ttu-id="dcf9c-106">.NET Framework 4 a introduit le [modèle asynchrone basé sur des tâches (TAP)](task-based-asynchronous-pattern-tap.md), qui remplace à la fois APM et EAP et fournit la possibilité de créer facilement des routines de migration à partir des modèles précédents.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-106">.NET Framework 4 introduced the [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md), which supersedes both APM and EAP and provides the ability to easily build migration routines from the earlier patterns.</span></span>
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="dcf9c-107">Tâches et APM</span><span class="sxs-lookup"><span data-stu-id="dcf9c-107">Tasks and the Asynchronous Programming Model (APM)</span></span>

### <a name="from-apm-to-tap"></a><span data-ttu-id="dcf9c-108">APM vers modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="dcf9c-108">From APM to TAP</span></span>  

 <span data-ttu-id="dcf9c-109">Étant donné que le modèle [APM (Asynchronous Programming Model)](asynchronous-programming-model-apm.md) est structuré, il est assez facile de créer un wrapper pour exposer une implémentation APM en tant qu’implémentation TAP.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-109">Because the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) pattern is structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="dcf9c-110">.NET Framework 4 et versions ultérieures incluent des routines d’assistance sous la forme de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> surcharges de méthode pour fournir cette traduction.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-110">.NET Framework 4 and later versions include helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="dcf9c-111">Imaginez la classe <xref:System.IO.Stream> et ses méthodes <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> , qui représentent la contrepartie AMP de méthode <xref:System.IO.Stream.Read%2A> synchrone :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-111">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="dcf9c-112">Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> pour implémenter un wrapper TAP pour cette opération, comme le montre l’exemple ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-112">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="dcf9c-113">Cette implémentation est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-113">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a><span data-ttu-id="dcf9c-114">TAP vers APM</span><span class="sxs-lookup"><span data-stu-id="dcf9c-114">From TAP to APM</span></span>  

 <span data-ttu-id="dcf9c-115">Si votre infrastructure existante attend le modèle APM, vous voudrez également prendre une implémentation TAP et l’utiliser lorsque l’implémentation APM est attendue.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-115">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="dcf9c-116">Étant donné que les tâches peuvent être composées et que la classe <xref:System.Threading.Tasks.Task> implémente <xref:System.IAsyncResult>, vous pouvez utiliser une fonction d’assistance simple pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-116">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="dcf9c-117">Le code suivant utilise une extension de la classe <xref:System.Threading.Tasks.Task%601> , mais vous pouvez utiliser une fonction presque identique pour les tâches non génériques.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-117">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="dcf9c-118">À présent, imaginez une situation dans laquelle vous avez l’implémentation TAP suivante :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-118">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="dcf9c-119">et que vous souhaitez fournir cette implémentation APM :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-119">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="dcf9c-120">L’exemple suivant montre une migration vers APM :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-120">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="dcf9c-121">Tâches et EAP</span><span class="sxs-lookup"><span data-stu-id="dcf9c-121">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  

 <span data-ttu-id="dcf9c-122">Envelopper une implémentation [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) est plus complexe qu’envelopper un modèle APM, car le modèle EAP est plus variable et moins structuré qu’un modèle APM.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-122">Wrapping an [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="dcf9c-123">Par exemple, le code suivant enveloppe la méthode `DownloadStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="dcf9c-123">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="dcf9c-124">`DownloadStringAsync` accepte un URI, déclenche l’événement `DownloadProgressChanged` lors du téléchargement afin de générer plusieurs statistiques sur la progression et déclenche l’événement `DownloadStringCompleted` lorsque l’événement précédent est terminé.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-124">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="dcf9c-125">Le résultat final est une chaîne qui détient le contenu de la page au niveau de l’URI spécifié.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-125">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="dcf9c-126">Tâches et handles d’attente</span><span class="sxs-lookup"><span data-stu-id="dcf9c-126">Tasks and Wait Handles</span></span>  
  
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="dcf9c-127">handles d’attente vers TAP</span><span class="sxs-lookup"><span data-stu-id="dcf9c-127">From Wait Handles to TAP</span></span>  

 <span data-ttu-id="dcf9c-128">Bien que les handles d’attente n’implémentent pas un modèle asynchrone, les développeurs expérimentés peuvent utiliser la classe <xref:System.Threading.WaitHandle> et la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pour recevoir des notifications asynchrones lorsqu’un handle d’attente est défini.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-128">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="dcf9c-129">Vous pouvez envelopper la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> pour autoriser une alternative basée sur les tâches pour toute attente synchrone sur un handle d’attente :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-129">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="dcf9c-130">Cette méthode vous permet d’utiliser les implémentations <xref:System.Threading.WaitHandle> existantes dans les méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-130">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="dcf9c-131">Par exemple, si vous souhaitez limiter le nombre d’opérations asynchrones en cours d’exécution à un moment donné, vous pouvez utiliser un sémaphore (un objet <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="dcf9c-131">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="dcf9c-132">Vous pouvez limiter à *n* le nombre d’opérations qui s’exécutent simultanément en initialisant le nombre du sémaphore à *n*, en attendant le sémaphore chaque fois que vous souhaitez effectuer une opération, puis libérer le sémaphore lorsque vous avez terminé une opération :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-132">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore's count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you're done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="dcf9c-133">Vous pouvez également créer un sémaphore asynchrone qui ne repose pas sur les handles d’attente, mais sur les tâches.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-133">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="dcf9c-134">Pour ce faire, vous pouvez utiliser des techniques telles que celles abordées dans [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) pour la création de structures de données sur <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-134">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="dcf9c-135">TAP vers handles d’attente</span><span class="sxs-lookup"><span data-stu-id="dcf9c-135">From TAP to Wait Handles</span></span>  

 <span data-ttu-id="dcf9c-136">Comme mentionné précédemment, la classe <xref:System.Threading.Tasks.Task> implémente <xref:System.IAsyncResult>, et cette implémentation expose une propriété <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> qui renvoie un handle d’attente qui sera défini une fois la <xref:System.Threading.Tasks.Task> terminée.</span><span class="sxs-lookup"><span data-stu-id="dcf9c-136">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="dcf9c-137">Vous pouvez obtenir un <xref:System.Threading.WaitHandle> pour une <xref:System.Threading.Tasks.Task> comme suit :</span><span class="sxs-lookup"><span data-stu-id="dcf9c-137">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="dcf9c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcf9c-138">See also</span></span>

- [<span data-ttu-id="dcf9c-139">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="dcf9c-139">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="dcf9c-140">Implémentation du modèle asynchrone basé sur des tâches</span><span class="sxs-lookup"><span data-stu-id="dcf9c-140">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="dcf9c-141">Utilisation du modèle asynchrone basé sur les tâches</span><span class="sxs-lookup"><span data-stu-id="dcf9c-141">Consuming the Task-based Asynchronous Pattern</span></span>](consuming-the-task-based-asynchronous-pattern.md)
