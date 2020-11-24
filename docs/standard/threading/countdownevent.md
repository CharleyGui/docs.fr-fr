---
title: CountdownEvent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 15ff3ee8f4ea18b243f5c3070f1c59df4646a1a4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676476"
---
# <a name="countdownevent"></a><span data-ttu-id="8bd08-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="8bd08-102">CountdownEvent</span></span>

<span data-ttu-id="8bd08-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> est une primitive de synchronisation qui débloque ses threads en attente après avoir été signalée un certain nombre de fois.</span><span class="sxs-lookup"><span data-stu-id="8bd08-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="8bd08-104"><xref:System.Threading.CountdownEvent> est conçu pour les scénarios dans lesquels vous devriez sinon utiliser un <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> et décrémenter manuellement une variable avant de signaler l’événement.</span><span class="sxs-lookup"><span data-stu-id="8bd08-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="8bd08-105">Par exemple, dans un scénario de duplication/jointure, vous pouvez simplement créer un <xref:System.Threading.CountdownEvent> avec 5 signaux, puis démarrer cinq éléments de travail sur le pool de threads, chaque élément de travail appellant <xref:System.Threading.CountdownEvent.Signal%2A> lorsqu’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="8bd08-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="8bd08-106">Chaque appel à <xref:System.Threading.CountdownEvent.Signal%2A> décrémente le nombre de signaux de 1.</span><span class="sxs-lookup"><span data-stu-id="8bd08-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="8bd08-107">Sur le thread principal, l’appel à <xref:System.Threading.CountdownEvent.Wait%2A> sera bloqué jusqu’à ce que le nombre de signaux soit de zéro.</span><span class="sxs-lookup"><span data-stu-id="8bd08-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bd08-108">Pour le code qui ne doit pas d’interagir avec les API de synchronisation .NET Framework héritées, envisagez d’utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou la méthode <xref:System.Threading.Tasks.Parallel.Invoke%2A> pour une approche plus facile de l’expression du parallélisme duplication-jointure.</span><span class="sxs-lookup"><span data-stu-id="8bd08-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="8bd08-109"><xref:System.Threading.CountdownEvent> a ces fonctionnalités supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="8bd08-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="8bd08-110">L’opération d’attente peut être annulée à l’aide des jetons d’annulation.</span><span class="sxs-lookup"><span data-stu-id="8bd08-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="8bd08-111">Son nombre de signaux peut être incrémenté une fois que l’instance est créée.</span><span class="sxs-lookup"><span data-stu-id="8bd08-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="8bd08-112">Les instances peuvent être réutilisées après que <xref:System.Threading.CountdownEvent.Wait%2A> a retourné en appelant la méthode <xref:System.Threading.CountdownEvent.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bd08-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="8bd08-113">Les instances exposent une <xref:System.Threading.WaitHandle> pour l’intégration à d’autres API de synchronisation .net, telles que <xref:System.Threading.WaitHandle.WaitAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="8bd08-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET synchronization APIs, such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="8bd08-114">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="8bd08-114">Basic Usage</span></span>  

 <span data-ttu-id="8bd08-115">L’exemple suivant illustre comment utiliser un <xref:System.Threading.CountdownEvent> avec des éléments de travail <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="8bd08-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="8bd08-116">CountdownEvent avec annulation</span><span class="sxs-lookup"><span data-stu-id="8bd08-116">CountdownEvent With Cancellation</span></span>  

 <span data-ttu-id="8bd08-117">L’exemple suivant montre comment annuler l’opération d’attente sur <xref:System.Threading.CountdownEvent> à l’aide d’un jeton d’annulation.</span><span class="sxs-lookup"><span data-stu-id="8bd08-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="8bd08-118">Le modèle de base suit le modèle pour l’annulation unifiée, qui a été introduite dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8bd08-118">The basic pattern follows the model for unified cancellation, which was introduced in .NET Framework 4.</span></span> <span data-ttu-id="8bd08-119">Pour plus d’informations, consultez [annulation dans les threads managés](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="8bd08-119">For more information, see [Cancellation in Managed Threads](cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="8bd08-120">Notez que l’opération d’attente n’annule pas les threads qui la signalent.</span><span class="sxs-lookup"><span data-stu-id="8bd08-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="8bd08-121">En règle générale, l’annulation est appliquée à une opération logique, ceci pouvant inclure non seulement l’attente de l’événement, mais encore, tous les éléments de travail que l’attente est en train de synchroniser.</span><span class="sxs-lookup"><span data-stu-id="8bd08-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="8bd08-122">Dans cet exemple, chaque élément de travail dispose d’une copie du même jeton d’annulation de manière à pouvoir répondre à la demande d’annulation.</span><span class="sxs-lookup"><span data-stu-id="8bd08-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd08-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bd08-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
