---
title: CountdownEvent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 82fe4844728702e91190b55a833848c1c9ece40c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826571"
---
# <a name="countdownevent"></a>CountdownEvent

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> est une primitive de synchronisation qui débloque ses threads en attente après avoir été signalée un certain nombre de fois. <xref:System.Threading.CountdownEvent> est conçu pour les scénarios dans lesquels vous devriez sinon utiliser un <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> et décrémenter manuellement une variable avant de signaler l’événement. Par exemple, dans un scénario de duplication/jointure, vous pouvez simplement créer un <xref:System.Threading.CountdownEvent> avec 5 signaux, puis démarrer cinq éléments de travail sur le pool de threads, chaque élément de travail appellant <xref:System.Threading.CountdownEvent.Signal%2A> lorsqu’il est terminé. Chaque appel à <xref:System.Threading.CountdownEvent.Signal%2A> décrémente le nombre de signaux de 1. Sur le thread principal, l’appel à <xref:System.Threading.CountdownEvent.Wait%2A> sera bloqué jusqu’à ce que le nombre de signaux soit de zéro.  
  
> [!NOTE]
> Pour le code qui ne doit pas d’interagir avec les API de synchronisation .NET Framework héritées, envisagez d’utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou la méthode <xref:System.Threading.Tasks.Parallel.Invoke%2A> pour une approche plus facile de l’expression du parallélisme duplication-jointure.  
  
 <xref:System.Threading.CountdownEvent> a ces fonctionnalités supplémentaires :  
  
- L’opération d’attente peut être annulée à l’aide des jetons d’annulation.  
  
- Son nombre de signaux peut être incrémenté une fois que l’instance est créée.  
  
- Les instances peuvent être réutilisées après que <xref:System.Threading.CountdownEvent.Wait%2A> a retourné en appelant la méthode <xref:System.Threading.CountdownEvent.Reset%2A>.  
  
- Les instances exposent une <xref:System.Threading.WaitHandle> pour l’intégration à d’autres API de synchronisation .net, telles que <xref:System.Threading.WaitHandle.WaitAll%2A> .  
  
## <a name="basic-usage"></a>Utilisation de base  
 L’exemple suivant illustre comment utiliser un <xref:System.Threading.CountdownEvent> avec des éléments de travail <xref:System.Threading.ThreadPool>.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent avec annulation  
 L’exemple suivant montre comment annuler l’opération d’attente sur <xref:System.Threading.CountdownEvent> à l’aide d’un jeton d’annulation. Le modèle de base suit le modèle pour l’annulation unifiée, qui a été introduite dans .NET Framework 4. Pour plus d’informations, consultez [annulation dans les threads managés](cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Notez que l’opération d’attente n’annule pas les threads qui la signalent. En règle générale, l’annulation est appliquée à une opération logique, ceci pouvant inclure non seulement l’attente de l’événement, mais encore, tous les éléments de travail que l’attente est en train de synchroniser. Dans cet exemple, chaque élément de travail dispose d’une copie du même jeton d’annulation de manière à pouvoir répondre à la demande d’annulation.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
