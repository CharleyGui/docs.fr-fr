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
# <a name="barrier"></a>Cloisonnement

Un <xref:System.Threading.Barrier?displayProperty=nameWithType> est une primitive de synchronisation définie par l’utilisateur qui permet à plusieurs threads (appelés *participants*) de travailler simultanément sur un algorithme en plusieurs phases. Chaque participant s'exécute jusqu'à ce qu'il atteigne le point de cloisonnement dans le code. Le cloisonnement représente la fin d'une phase de travail. Quand un participant atteint le cloisonnement, il se bloque jusqu'à ce que tous les participants aient atteint le même cloisonnement. Une fois que tous les participants ont atteint le cloisonnement, vous pouvez éventuellement appeler une action post-phase. Cette action post-phase peut être utilisée pour effectuer des actions avec un thread unique alors que tous les autres threads sont encore bloqués. Une fois l'action exécutée, tous les participants sont débloqués.  
  
 L’extrait de code suivant montre un modèle de cloisonnement de base.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Pour obtenir un exemple complet, voir [Guide pratique : synchroniser des opérations simultanées avec un objet Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Ajout et suppression de participants

 Quand vous créez une instance <xref:System.Threading.Barrier>, spécifiez le nombre de participants. Vous pouvez également ajouter ou supprimer des participants dynamiquement à tout moment. Par exemple, si un participant résout sa part du problème, vous pouvez stocker le résultat, arrêter l'exécution sur ce thread et appeler <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> pour décrémenter le nombre de participants du cloisonnement. Quand vous ajoutez un participant en appelant <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, la valeur de retour spécifie le numéro de la phase actuelle, ce qui peut être utile pour initialiser le travail du nouveau participant.  
  
## <a name="broken-barriers"></a>Cloisonnements cassés

 Des blocages peuvent se produire si un participant ne parvient pas à atteindre le cloisonnement. Pour éviter ces blocages, utilisez les surcharges de la méthode <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> pour spécifier un délai d'attente et un jeton d'annulation. Ces surcharges retournent une valeur booléenne que chaque participant peut vérifier avant de passer à la phase suivante.  
  
## <a name="post-phase-exceptions"></a>Exceptions post-phase

 Si le délégué post-phase lève une exception, il est encapsulé dans un objet <xref:System.Threading.BarrierPostPhaseException> qui est ensuite propagé à tous les participants.  
  
## <a name="barrier-versus-continuewhenall"></a>Cloisonnement et ContinueWhenAll

 Les cloisonnements sont particulièrement utiles quand les threads exécutent plusieurs phases dans des boucles. Si votre code requiert uniquement une ou deux phases de travail, songez à utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> avec n'importe quel type de jointure implicite, notamment :  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Pour plus d’informations, consultez [Chaînage des tâches à l’aide de tâches de continuation](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Voir aussi

- [Objets et fonctionnalités de Threading](threading-objects-and-features.md)
- [Comment : synchroniser des opérations simultanées avec un cloisonnement](how-to-synchronize-concurrent-operations-with-a-barrier.md)
