---
title: Détruire des threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960088"
---
# <a name="destroying-threads"></a><span data-ttu-id="b215d-102">Détruire des threads</span><span class="sxs-lookup"><span data-stu-id="b215d-102">Destroying threads</span></span>
<span data-ttu-id="b215d-103">La méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> permet d’arrêter définitivement un thread managé.</span><span class="sxs-lookup"><span data-stu-id="b215d-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="b215d-104">Quand vous appelez <xref:System.Threading.Thread.Abort%2A>, le Common Language Runtime lève une exception <xref:System.Threading.ThreadAbortException> dans le thread cible, que ce dernier peut intercepter.</span><span class="sxs-lookup"><span data-stu-id="b215d-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="b215d-105">Pour plus d’informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b215d-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b215d-106">Si un thread est en train d’exécuter du code non managé quand sa méthode <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime le marque comme <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b215d-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b215d-107">L’exception est levée quand le thread retourne au code managé.</span><span class="sxs-lookup"><span data-stu-id="b215d-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="b215d-108">Une fois un thread annulé, il ne peut pas être redémarré.</span><span class="sxs-lookup"><span data-stu-id="b215d-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="b215d-109">La méthode <xref:System.Threading.Thread.Abort%2A> n’entraîne pas l’annulation immédiate du thread, car le thread cible peut intercepter l’exception <xref:System.Threading.ThreadAbortException> et exécuter arbitrairement des quantités de code dans un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="b215d-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="b215d-110">Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous devez attendre que le thread se termine.</span><span class="sxs-lookup"><span data-stu-id="b215d-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="b215d-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> est un appel bloquant qui ne retourne de résultats que quand le thread a réellement arrêté son exécution ou qu’un intervalle de délai d’attente facultatif a expiré.</span><span class="sxs-lookup"><span data-stu-id="b215d-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="b215d-112">Le thread annulé pourrait appeler la méthode <xref:System.Threading.Thread.ResetAbort%2A> ou exécuter un traitement illimité dans un bloc `finally`. Par conséquent, si vous ne spécifiez pas de délai d’attente, l’attente pourrait ne jamais se terminer.</span><span class="sxs-lookup"><span data-stu-id="b215d-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="b215d-113">Les threads qui attendent suite à un appel à la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> peuvent être interrompus par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b215d-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="b215d-114">Gestion de ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="b215d-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="b215d-115">Si vous pensez que votre thread sera annulé, soit suite à un appel de votre propre code à <xref:System.Threading.Thread.Abort%2A>, soit suite au déchargement d’un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer l’exception <xref:System.Threading.ThreadAbortException> et exécuter tout traitement final dans une clause `finally`, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b215d-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b215d-116">Votre code de nettoyage doit se trouver dans la clause `catch` ou la clause `finally`, car une exception <xref:System.Threading.ThreadAbortException> est de nouveau levée par le système à la fin de la clause `finally`, ou à la fin de la clause `catch` s’il n’existe pas de clause `finally`.</span><span class="sxs-lookup"><span data-stu-id="b215d-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="b215d-117">Vous pouvez empêcher le système de lever une nouvelle exception en appelant la méthode <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b215d-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b215d-118">Vous ne devez néanmoins le faire que si c’est votre propre code qui a provoqué l’exception <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="b215d-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b215d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b215d-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="b215d-120">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="b215d-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
