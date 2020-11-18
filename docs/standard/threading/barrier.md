---
title: Cloisonnement
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 4eab74ef07ac56a4d3ff65e67bb9fbd45dbfc9bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819940"
---
# <a name="barrier"></a><span data-ttu-id="28aef-102">Cloisonnement</span><span class="sxs-lookup"><span data-stu-id="28aef-102">Barrier</span></span>

<span data-ttu-id="28aef-103">Un <xref:System.Threading.Barrier?displayProperty=nameWithType> est une primitive de synchronisation définie par l’utilisateur qui permet à plusieurs threads (appelés *participants*) de travailler simultanément sur un algorithme en plusieurs phases.</span><span class="sxs-lookup"><span data-stu-id="28aef-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="28aef-104">Chaque participant s'exécute jusqu'à ce qu'il atteigne le point de cloisonnement dans le code.</span><span class="sxs-lookup"><span data-stu-id="28aef-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="28aef-105">Le cloisonnement représente la fin d'une phase de travail.</span><span class="sxs-lookup"><span data-stu-id="28aef-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="28aef-106">Quand un participant atteint le cloisonnement, il se bloque jusqu'à ce que tous les participants aient atteint le même cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="28aef-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="28aef-107">Une fois que tous les participants ont atteint le cloisonnement, vous pouvez éventuellement appeler une action post-phase.</span><span class="sxs-lookup"><span data-stu-id="28aef-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="28aef-108">Cette action post-phase peut être utilisée pour effectuer des actions avec un thread unique alors que tous les autres threads sont encore bloqués.</span><span class="sxs-lookup"><span data-stu-id="28aef-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="28aef-109">Une fois l'action exécutée, tous les participants sont débloqués.</span><span class="sxs-lookup"><span data-stu-id="28aef-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="28aef-110">L’extrait de code suivant montre un modèle de cloisonnement de base.</span><span class="sxs-lookup"><span data-stu-id="28aef-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="28aef-111">Pour obtenir un exemple complet, voir [Guide pratique : synchroniser des opérations simultanées avec un objet Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="28aef-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="28aef-112">Ajout et suppression de participants</span><span class="sxs-lookup"><span data-stu-id="28aef-112">Adding and removing participants</span></span>

 <span data-ttu-id="28aef-113">Quand vous créez une instance <xref:System.Threading.Barrier>, spécifiez le nombre de participants.</span><span class="sxs-lookup"><span data-stu-id="28aef-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="28aef-114">Vous pouvez également ajouter ou supprimer des participants dynamiquement à tout moment.</span><span class="sxs-lookup"><span data-stu-id="28aef-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="28aef-115">Par exemple, si un participant résout sa part du problème, vous pouvez stocker le résultat, arrêter l'exécution sur ce thread et appeler <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> pour décrémenter le nombre de participants du cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="28aef-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="28aef-116">Quand vous ajoutez un participant en appelant <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, la valeur de retour spécifie le numéro de la phase actuelle, ce qui peut être utile pour initialiser le travail du nouveau participant.</span><span class="sxs-lookup"><span data-stu-id="28aef-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="28aef-117">Cloisonnements cassés</span><span class="sxs-lookup"><span data-stu-id="28aef-117">Broken barriers</span></span>

 <span data-ttu-id="28aef-118">Des blocages peuvent se produire si un participant ne parvient pas à atteindre le cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="28aef-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="28aef-119">Pour éviter ces blocages, utilisez les surcharges de la méthode <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> pour spécifier un délai d'attente et un jeton d'annulation.</span><span class="sxs-lookup"><span data-stu-id="28aef-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="28aef-120">Ces surcharges retournent une valeur booléenne que chaque participant peut vérifier avant de passer à la phase suivante.</span><span class="sxs-lookup"><span data-stu-id="28aef-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="28aef-121">Exceptions post-phase</span><span class="sxs-lookup"><span data-stu-id="28aef-121">Post-phase exceptions</span></span>

 <span data-ttu-id="28aef-122">Si le délégué post-phase lève une exception, il est encapsulé dans un objet <xref:System.Threading.BarrierPostPhaseException> qui est ensuite propagé à tous les participants.</span><span class="sxs-lookup"><span data-stu-id="28aef-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="28aef-123">Cloisonnement et ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="28aef-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="28aef-124">Les cloisonnements sont particulièrement utiles quand les threads exécutent plusieurs phases dans des boucles.</span><span class="sxs-lookup"><span data-stu-id="28aef-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="28aef-125">Si votre code requiert uniquement une ou deux phases de travail, songez à utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> avec n'importe quel type de jointure implicite, notamment :</span><span class="sxs-lookup"><span data-stu-id="28aef-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="28aef-126">Pour plus d’informations, consultez [Chaînage des tâches à l’aide de tâches de continuation](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="28aef-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28aef-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28aef-127">See also</span></span>

- [<span data-ttu-id="28aef-128">Objets et fonctionnalités de Threading</span><span class="sxs-lookup"><span data-stu-id="28aef-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="28aef-129">Comment : synchroniser des opérations simultanées avec un cloisonnement</span><span class="sxs-lookup"><span data-stu-id="28aef-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
