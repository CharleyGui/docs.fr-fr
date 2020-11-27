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
ms.openlocfilehash: 707e3e339cb8a692f862afc15328eef53f0547e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286082"
---
# <a name="dangerousthreadingapi-mda"></a>Assistant Débogage managé dangerousThreadingAPI

L’Assistant Débogage managé (MDA, Managed Debugging Assistant) `dangerousThreadingAPI` est activé quand la méthode <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> est appelée sur un thread autre que le thread actif.  
  
## <a name="symptoms"></a>Symptômes  

 Une application ne répond pas ou se bloque indéfiniment. Les données système ou d’application peuvent se retrouver dans un état imprévisible de façon temporaire ou même après l’arrêt d’une application. Certaines opérations ne se terminent pas comme prévu.  
  
 Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.  
  
## <a name="cause"></a>Cause  

 Un thread est suspendu de façon asynchrone par un autre thread à l’aide de la méthode <xref:System.Threading.Thread.Suspend%2A>. Il n’existe aucun moyen de déterminer le moment le plus sûr pour suspendre un autre thread pouvant se trouver en cours d’opération. La suspension du thread peut entraîner l’altération des données ou des invariants. Si un thread est suspendu et n’est jamais repris à l’aide de la méthode <xref:System.Threading.Thread.Resume%2A>, l’application peut se bloquer indéfiniment et même endommager les données d’application. Ces méthodes ont été marquées comme obsolètes.  
  
 Si les primitives de synchronisation sont détenues par le thread cible, elles restent détenues pendant la suspension. Cela peut entraîner des interblocages si un autre thread, par exemple le thread qui exécute <xref:System.Threading.Thread.Suspend%2A>, tente d’acquérir un verrou sur la primitive. Dans ce cas, le problème se manifeste sous le forme d’un interblocage.  
  
## <a name="resolution"></a>Résolution  

 Évitez les conceptions qui nécessitent l’utilisation de <xref:System.Threading.Thread.Suspend%2A> et <xref:System.Threading.Thread.Resume%2A>. Pour la coopération entre les threads, utilisez des primitives de synchronisation telles que <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> ou l’instruction C# `lock`. Si vous devez utiliser ces méthodes, réduisez la durée et la quantité de code qui s’exécute pendant que le thread est suspendu.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il signale uniquement les données relatives aux opérations de thread dangereuses.  
  
## <a name="output"></a>Output  

 L’Assistant Débogage managé identifie la méthode de thread dangereuse qui a entraîné son activation.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant illustre un appel à la méthode <xref:System.Threading.Thread.Suspend%2A> qui entraîne l’activation de `dangerousThreadingAPI`.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [lock, instruction](../../csharp/language-reference/keywords/lock-statement.md)
