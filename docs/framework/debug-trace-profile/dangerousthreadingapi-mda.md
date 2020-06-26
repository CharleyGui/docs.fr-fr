---
title: Assistant Débogage managé dangerousThreadingAPI
description: Passez en revue l’Assistant Débogage managé dangerousThreadingAPI (MDA) qui est activé lorsque thread. suspend est appelé sur un thread autre que le thread actuel.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416003"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="c38d7-103">Assistant Débogage managé dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="c38d7-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="c38d7-104">L’Assistant Débogage managé (MDA, Managed Debugging Assistant) `dangerousThreadingAPI` est activé quand la méthode <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> est appelée sur un thread autre que le thread actif.</span><span class="sxs-lookup"><span data-stu-id="c38d7-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c38d7-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c38d7-105">Symptoms</span></span>  
 <span data-ttu-id="c38d7-106">Une application ne répond pas ou se bloque indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="c38d7-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="c38d7-107">Les données système ou d’application peuvent se retrouver dans un état imprévisible de façon temporaire ou même après l’arrêt d’une application.</span><span class="sxs-lookup"><span data-stu-id="c38d7-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="c38d7-108">Certaines opérations ne se terminent pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c38d7-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="c38d7-109">Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.</span><span class="sxs-lookup"><span data-stu-id="c38d7-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c38d7-110">Cause</span><span class="sxs-lookup"><span data-stu-id="c38d7-110">Cause</span></span>  
 <span data-ttu-id="c38d7-111">Un thread est suspendu de façon asynchrone par un autre thread à l’aide de la méthode <xref:System.Threading.Thread.Suspend%2A>.</span><span class="sxs-lookup"><span data-stu-id="c38d7-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="c38d7-112">Il n’existe aucun moyen de déterminer le moment le plus sûr pour suspendre un autre thread pouvant se trouver en cours d’opération.</span><span class="sxs-lookup"><span data-stu-id="c38d7-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="c38d7-113">La suspension du thread peut entraîner l’altération des données ou des invariants.</span><span class="sxs-lookup"><span data-stu-id="c38d7-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="c38d7-114">Si un thread est suspendu et n’est jamais repris à l’aide de la méthode <xref:System.Threading.Thread.Resume%2A>, l’application peut se bloquer indéfiniment et même endommager les données d’application.</span><span class="sxs-lookup"><span data-stu-id="c38d7-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="c38d7-115">Ces méthodes ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="c38d7-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="c38d7-116">Si les primitives de synchronisation sont détenues par le thread cible, elles restent détenues pendant la suspension.</span><span class="sxs-lookup"><span data-stu-id="c38d7-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="c38d7-117">Cela peut entraîner des interblocages si un autre thread, par exemple le thread qui exécute <xref:System.Threading.Thread.Suspend%2A>, tente d’acquérir un verrou sur la primitive.</span><span class="sxs-lookup"><span data-stu-id="c38d7-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="c38d7-118">Dans ce cas, le problème se manifeste sous le forme d’un interblocage.</span><span class="sxs-lookup"><span data-stu-id="c38d7-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c38d7-119">Résolution</span><span class="sxs-lookup"><span data-stu-id="c38d7-119">Resolution</span></span>  
 <span data-ttu-id="c38d7-120">Évitez les conceptions qui nécessitent l’utilisation de <xref:System.Threading.Thread.Suspend%2A> et <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="c38d7-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="c38d7-121">Pour la coopération entre les threads, utilisez des primitives de synchronisation telles que <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> ou l’instruction C# `lock`.</span><span class="sxs-lookup"><span data-stu-id="c38d7-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="c38d7-122">Si vous devez utiliser ces méthodes, réduisez la durée et la quantité de code qui s’exécute pendant que le thread est suspendu.</span><span class="sxs-lookup"><span data-stu-id="c38d7-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c38d7-123">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c38d7-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="c38d7-124">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="c38d7-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c38d7-125">Il signale uniquement les données relatives aux opérations de thread dangereuses.</span><span class="sxs-lookup"><span data-stu-id="c38d7-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c38d7-126">Output</span><span class="sxs-lookup"><span data-stu-id="c38d7-126">Output</span></span>  
 <span data-ttu-id="c38d7-127">L’Assistant Débogage managé identifie la méthode de thread dangereuse qui a entraîné son activation.</span><span class="sxs-lookup"><span data-stu-id="c38d7-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c38d7-128">Configuration</span><span class="sxs-lookup"><span data-stu-id="c38d7-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c38d7-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="c38d7-129">Example</span></span>  
 <span data-ttu-id="c38d7-130">L’exemple de code suivant illustre un appel à la méthode <xref:System.Threading.Thread.Suspend%2A> qui entraîne l’activation de `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="c38d7-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c38d7-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c38d7-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="c38d7-132">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="c38d7-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c38d7-133">lock, instruction</span><span class="sxs-lookup"><span data-stu-id="c38d7-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
