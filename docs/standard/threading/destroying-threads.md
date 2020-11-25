---
title: Détruire des threads
description: Identifiez vos options lorsque vous devez détruire un thread dans .NET, par exemple l’annulation coopérative ou la méthode Thread. Abort. Apprenez à gérer ThreadAbortException.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: bdba09f5709cf99bc0d076e3875a914cc7c5a11e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723764"
---
# <a name="destroying-threads"></a><span data-ttu-id="80f4a-104">Détruire des threads</span><span class="sxs-lookup"><span data-stu-id="80f4a-104">Destroying threads</span></span>

<span data-ttu-id="80f4a-105">Pour mettre fin à l’exécution du thread, vous utilisez généralement le [modèle d’annulation coopérative](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="80f4a-105">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="80f4a-106">Parfois, il n’est pas possible d’arrêter un thread de manière coopérative, car il exécute du code tiers non conçu pour l’annulation coopérative.</span><span class="sxs-lookup"><span data-stu-id="80f4a-106">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="80f4a-107">La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode de .NET Framework peut être utilisée pour arrêter de force un thread managé.</span><span class="sxs-lookup"><span data-stu-id="80f4a-107">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="80f4a-108">Lorsque vous appelez <xref:System.Threading.Thread.Abort%2A> , le Common Language Runtime lève une exception <xref:System.Threading.ThreadAbortException> dans le thread cible, que le thread cible peut intercepter.</span><span class="sxs-lookup"><span data-stu-id="80f4a-108">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="80f4a-109">Pour plus d’informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80f4a-109">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80f4a-110">La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode n’est pas prise en charge dans .net 5 (y compris .net Core) et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="80f4a-110">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET 5 (including .NET Core) and later versions.</span></span> <span data-ttu-id="80f4a-111">Si vous devez mettre fin à l’exécution de code tiers de force dans .NET 5 +, exécutez-le dans le processus distinct et utilisez <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80f4a-111">If you need to terminate the execution of third-party code forcibly in .NET 5+, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="80f4a-112">Si un thread est en train d’exécuter du code non managé quand sa méthode <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime le marque comme <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80f4a-112">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80f4a-113">L’exception est levée quand le thread retourne au code managé.</span><span class="sxs-lookup"><span data-stu-id="80f4a-113">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="80f4a-114">Une fois un thread annulé, il ne peut pas être redémarré.</span><span class="sxs-lookup"><span data-stu-id="80f4a-114">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="80f4a-115">La méthode <xref:System.Threading.Thread.Abort%2A> n’entraîne pas l’annulation immédiate du thread, car le thread cible peut intercepter l’exception <xref:System.Threading.ThreadAbortException> et exécuter arbitrairement des quantités de code dans un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="80f4a-115">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="80f4a-116">Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous devez attendre que le thread se termine.</span><span class="sxs-lookup"><span data-stu-id="80f4a-116">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="80f4a-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> est un appel bloquant qui ne retourne de résultats que quand le thread a réellement arrêté son exécution ou qu’un intervalle de délai d’attente facultatif a expiré.</span><span class="sxs-lookup"><span data-stu-id="80f4a-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="80f4a-118">Le thread annulé pourrait appeler la méthode <xref:System.Threading.Thread.ResetAbort%2A> ou exécuter un traitement illimité dans un bloc `finally`. Par conséquent, si vous ne spécifiez pas de délai d’attente, l’attente pourrait ne jamais se terminer.</span><span class="sxs-lookup"><span data-stu-id="80f4a-118">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="80f4a-119">Les threads qui attendent suite à un appel à la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> peuvent être interrompus par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80f4a-119">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="80f4a-120">Gestion de ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="80f4a-120">Handling ThreadAbortException</span></span>  

 <span data-ttu-id="80f4a-121">Si vous pensez que votre thread sera annulé, soit suite à un appel de votre propre code à <xref:System.Threading.Thread.Abort%2A>, soit suite au déchargement d’un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer l’exception <xref:System.Threading.ThreadAbortException> et exécuter tout traitement final dans une clause `finally`, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="80f4a-121">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="80f4a-122">Votre code de nettoyage doit se trouver dans la clause `catch` ou la clause `finally`, car une exception <xref:System.Threading.ThreadAbortException> est de nouveau levée par le système à la fin de la clause `finally`, ou à la fin de la clause `catch` s’il n’existe pas de clause `finally`.</span><span class="sxs-lookup"><span data-stu-id="80f4a-122">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="80f4a-123">Vous pouvez empêcher le système de lever une nouvelle exception en appelant la méthode <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80f4a-123">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80f4a-124">Vous ne devez néanmoins le faire que si c’est votre propre code qui a provoqué l’exception <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="80f4a-124">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f4a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80f4a-125">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="80f4a-126">Utilisation de threads et de threads</span><span class="sxs-lookup"><span data-stu-id="80f4a-126">Using Threads and Threading</span></span>](using-threads-and-threading.md)
