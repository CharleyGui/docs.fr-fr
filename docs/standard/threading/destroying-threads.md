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
# <a name="destroying-threads"></a>Détruire des threads
La méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> permet d’arrêter définitivement un thread managé. Quand vous appelez <xref:System.Threading.Thread.Abort%2A>, le Common Language Runtime lève une exception <xref:System.Threading.ThreadAbortException> dans le thread cible, que ce dernier peut intercepter. Pour plus d’informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Si un thread est en train d’exécuter du code non managé quand sa méthode <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime le marque comme <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. L’exception est levée quand le thread retourne au code managé.  
  
 Une fois un thread annulé, il ne peut pas être redémarré.  
  
 La méthode <xref:System.Threading.Thread.Abort%2A> n’entraîne pas l’annulation immédiate du thread, car le thread cible peut intercepter l’exception <xref:System.Threading.ThreadAbortException> et exécuter arbitrairement des quantités de code dans un bloc `finally`. Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous devez attendre que le thread se termine. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> est un appel bloquant qui ne retourne de résultats que quand le thread a réellement arrêté son exécution ou qu’un intervalle de délai d’attente facultatif a expiré. Le thread annulé pourrait appeler la méthode <xref:System.Threading.Thread.ResetAbort%2A> ou exécuter un traitement illimité dans un bloc `finally`. Par conséquent, si vous ne spécifiez pas de délai d’attente, l’attente pourrait ne jamais se terminer.  
  
 Les threads qui attendent suite à un appel à la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> peuvent être interrompus par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Gestion de ThreadAbortException  
 Si vous pensez que votre thread sera annulé, soit suite à un appel de votre propre code à <xref:System.Threading.Thread.Abort%2A>, soit suite au déchargement d’un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer l’exception <xref:System.Threading.ThreadAbortException> et exécuter tout traitement final dans une clause `finally`, comme indiqué dans le code suivant.  
  
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
  
 Votre code de nettoyage doit se trouver dans la clause `catch` ou la clause `finally`, car une exception <xref:System.Threading.ThreadAbortException> est de nouveau levée par le système à la fin de la clause `finally`, ou à la fin de la clause `catch` s’il n’existe pas de clause `finally`.  
  
 Vous pouvez empêcher le système de lever une nouvelle exception en appelant la méthode <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>. Vous ne devez néanmoins le faire que si c’est votre propre code qui a provoqué l’exception <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
