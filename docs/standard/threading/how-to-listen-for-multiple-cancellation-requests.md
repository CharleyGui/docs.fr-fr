---
title: "Comment : écouter plusieurs demandes d'annulation"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: e5ec32d486dd5eafc8c456c5a4b0b3297f043499
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728522"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Comment : écouter plusieurs demandes d'annulation

Cet exemple montre comment écouter simultanément deux jetons d’annulation afin de pouvoir annuler une opération si un des jetons le demande.  
  
> [!NOTE]
> Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.  
  
## <a name="example"></a>Exemple  

 Dans l'exemple suivant, la méthode <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> permet de fusionner deux jetons en un seul. Cela permet de transmettre le jeton à des méthodes qui n’acceptent qu’un seul jeton d’annulation comme argument. L’exemple illustre un scénario courant dans lequel une méthode doit observer à la fois un jeton reçu depuis l’extérieur de la classe et un jeton généré à l’intérieur de la classe.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Lorsque le jeton lié lève une <xref:System.OperationCanceledException>, le jeton transmis à l’exception est le jeton lié, et non un des jetons prédécesseurs. Pour déterminer quel jeton a été annulé, vérifiez directement l’état des jetons prédécesseurs.  
  
 Dans cet exemple, <xref:System.AggregateException> ne doit jamais être levée, mais elle est interceptée ici car, dans les scénarios réels, toutes les autres exceptions, hormis <xref:System.OperationCanceledException>, levées à partir du délégué de tâche sont encapsulées dans une <xref:System.AggregateException>.  
  
## <a name="see-also"></a>Voir aussi

- [Annulation dans les threads managés](cancellation-in-managed-threads.md)
