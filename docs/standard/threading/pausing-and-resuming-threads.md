---
title: Suspension et interruption de threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 3020694b93479d5f1d64d31c203f8fe033a10320
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129008"
---
# <a name="pausing-and-interrupting-threads"></a>Suspension et interruption de threads

Les méthodes les plus courantes permettant de synchroniser les activités de threads consistent à bloquer et à diffuser des threads, ou à verrouiller des objets ou des régions du code. Pour plus d’informations sur ces mécanismes de verrouillage et de blocage, voir [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Vous pouvez également avoir des threads en veille. Quand des threads sont bloqués ou en veille, vous pouvez utiliser une <xref:System.Threading.ThreadInterruptedException> pour les débloquer ou les réveiller.  
  
## <a name="the-threadsleep-method"></a>La méthode Thread.Sleep

 L'appel de la méthode <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> entraîne le blocage immédiat du thread actuel pendant le nombre de millisecondes ou l’intervalle de temps que dure le passage à la méthode et cède le reste de sa tranche horaire à un autre thread. Une fois l’intervalle expiré, l’exécution du thread en veille reprend.  
  
 Un thread ne peut pas appeler <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> sur un autre thread.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> est une méthode statique qui entraîne systématiquement la mise en veille du thread actuel.  
  
 L'appel de <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> avec  une valeur de <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> entraîne la mise en veille du thread jusqu'à ce qu'elle soit interrompue par un autre thread qui appelle la méthode <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, ou jusqu'à ce qu'elle soit terminée par un appel à sa méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  L’exemple suivant illustre les deux méthodes d’interruption d’un thread en veille.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Interruption de threads

 Vous pouvez interrompre un thread en attente en appelant la méthode <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> sur le thread bloqué pour lever une <xref:System.Threading.ThreadInterruptedException>, ce qui retirera le thread de l'appel bloquant. Le thread doit intercepter la <xref:System.Threading.ThreadInterruptedException> et faire tout le nécessaire pour continuer à fonctionner. Si le thread ignore l'exception, le runtime intercepte l'exception et arrête le thread.  
  
> [!NOTE]
> Si le thread cible n'est pas bloqué quand <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> est appelé, le thread ne sera pas interrompu avant d'être bloqué. Si le thread n'est jamais bloqué, il peut se terminer sans jamais être interrompu.  
  
 En cas d'attente managée, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> réveillent le thread immédiatement. En cas d'attente non managée (par exemple, dans le cas d'un appel de code non managé à la fonction Win32 [WaitForSingleObject ](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)), ni <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ni <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ne pourront prendre le contrôle du thread tant qu'il ne sera pas retourné dans du code managé ou tant qu'il n'effectuera pas d'appel depuis du code managé. Dans du code managé, le comportement est le suivant :  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> réveille un thread en attente et provoque la levée d'une <xref:System.Threading.ThreadInterruptedException> dans le thread de destination.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> réveille un thread en attente et provoque la levée d'une <xref:System.Threading.ThreadAbortException> dans le thread. Pour plus d’informations, voir [Destruction de threads](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Thread](../../../docs/standard/threading/index.md)
- [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
- [Aperçu des primitifs de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
