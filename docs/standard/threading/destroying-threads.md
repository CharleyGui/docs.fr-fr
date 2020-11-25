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
# <a name="destroying-threads"></a>Détruire des threads

Pour mettre fin à l’exécution du thread, vous utilisez généralement le [modèle d’annulation coopérative](cancellation-in-managed-threads.md). Parfois, il n’est pas possible d’arrêter un thread de manière coopérative, car il exécute du code tiers non conçu pour l’annulation coopérative. La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode de .NET Framework peut être utilisée pour arrêter de force un thread managé. Lorsque vous appelez <xref:System.Threading.Thread.Abort%2A> , le Common Language Runtime lève une exception <xref:System.Threading.ThreadAbortException> dans le thread cible, que le thread cible peut intercepter. Pour plus d’informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode n’est pas prise en charge dans .net 5 (y compris .net Core) et les versions ultérieures. Si vous devez mettre fin à l’exécution de code tiers de force dans .NET 5 +, exécutez-le dans le processus distinct et utilisez <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

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
- [Utilisation de threads et de threads](using-threads-and-threading.md)
