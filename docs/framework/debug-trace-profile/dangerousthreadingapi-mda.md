---
title: Assistant Débogage managé dangerousThreadingAPI
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174769"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="10965-102">Assistant Débogage managé dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="10965-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="10965-103">L’Assistant Débogage managé (MDA, Managed Debugging Assistant) `dangerousThreadingAPI` est activé quand la méthode <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> est appelée sur un thread autre que le thread actif.</span><span class="sxs-lookup"><span data-stu-id="10965-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="10965-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="10965-104">Symptoms</span></span>  
 <span data-ttu-id="10965-105">Une application ne répond pas ou se bloque indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="10965-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="10965-106">Les données système ou d’application peuvent se retrouver dans un état imprévisible de façon temporaire ou même après l’arrêt d’une application.</span><span class="sxs-lookup"><span data-stu-id="10965-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="10965-107">Certaines opérations ne se terminent pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="10965-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="10965-108">Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.</span><span class="sxs-lookup"><span data-stu-id="10965-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="10965-109">Cause :</span><span class="sxs-lookup"><span data-stu-id="10965-109">Cause</span></span>  
 <span data-ttu-id="10965-110">Un thread est suspendu de façon asynchrone par un autre thread à l’aide de la méthode <xref:System.Threading.Thread.Suspend%2A>.</span><span class="sxs-lookup"><span data-stu-id="10965-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="10965-111">Il n’existe aucun moyen de déterminer le moment le plus sûr pour suspendre un autre thread pouvant se trouver en cours d’opération.</span><span class="sxs-lookup"><span data-stu-id="10965-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="10965-112">La suspension du thread peut entraîner l’altération des données ou des invariants.</span><span class="sxs-lookup"><span data-stu-id="10965-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="10965-113">Si un thread est suspendu et n’est jamais repris à l’aide de la méthode <xref:System.Threading.Thread.Resume%2A>, l’application peut se bloquer indéfiniment et même endommager les données d’application.</span><span class="sxs-lookup"><span data-stu-id="10965-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="10965-114">Ces méthodes ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="10965-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="10965-115">Si les primitives de synchronisation sont détenues par le thread cible, elles restent détenues pendant la suspension.</span><span class="sxs-lookup"><span data-stu-id="10965-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="10965-116">Cela peut entraîner des interblocages si un autre thread, par exemple le thread qui exécute <xref:System.Threading.Thread.Suspend%2A>, tente d’acquérir un verrou sur la primitive.</span><span class="sxs-lookup"><span data-stu-id="10965-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="10965-117">Dans ce cas, le problème se manifeste sous le forme d’un interblocage.</span><span class="sxs-lookup"><span data-stu-id="10965-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="10965-118">Résolution</span><span class="sxs-lookup"><span data-stu-id="10965-118">Resolution</span></span>  
 <span data-ttu-id="10965-119">Évitez les conceptions qui nécessitent l’utilisation de <xref:System.Threading.Thread.Suspend%2A> et <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="10965-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="10965-120">Pour la coopération entre les threads, utilisez des primitives de synchronisation telles que <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> ou l’instruction C# `lock`.</span><span class="sxs-lookup"><span data-stu-id="10965-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="10965-121">Si vous devez utiliser ces méthodes, réduisez la durée et la quantité de code qui s’exécute pendant que le thread est suspendu.</span><span class="sxs-lookup"><span data-stu-id="10965-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="10965-122">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="10965-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="10965-123">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="10965-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="10965-124">Il signale uniquement les données relatives aux opérations de thread dangereuses.</span><span class="sxs-lookup"><span data-stu-id="10965-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="10965-125">Output</span><span class="sxs-lookup"><span data-stu-id="10965-125">Output</span></span>  
 <span data-ttu-id="10965-126">L’Assistant Débogage managé identifie la méthode de thread dangereuse qui a entraîné son activation.</span><span class="sxs-lookup"><span data-stu-id="10965-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="10965-127">Configuration</span><span class="sxs-lookup"><span data-stu-id="10965-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="10965-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="10965-128">Example</span></span>  
 <span data-ttu-id="10965-129">L’exemple de code suivant illustre un appel à la méthode <xref:System.Threading.Thread.Suspend%2A> qui entraîne l’activation de `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="10965-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="10965-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10965-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="10965-131">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="10965-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="10965-132">lock, instruction</span><span class="sxs-lookup"><span data-stu-id="10965-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
