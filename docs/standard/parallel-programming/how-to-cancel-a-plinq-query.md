---
title: 'Procédure : annuler une requête PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: f8ca723ca3b9b9428c95651ebe2fa7d92e48ebbb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713286"
---
# <a name="how-to-cancel-a-plinq-query"></a>Procédure : annuler une requête PLINQ

Les exemples suivants montrent deux façons de modifier une requête PLINQ. Le premier exemple montre comment annuler une requête principalement composée de parcours de données. Le deuxième exemple montre comment annuler une requête contenant une fonction d’utilisateur dont les calculs sont onéreux.

> [!NOTE]
> Quand l'option «Uniquement mon code» est activée, Visual Studio peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur « exception non gérée par le code utilisateur ». Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.
>
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).

## <a name="example"></a>Exemple

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

L’infrastructure PLINQ ne restaure pas un seul <xref:System.OperationCanceledException> dans un <xref:System.AggregateException?displayProperty=nameWithType> ; le <xref:System.OperationCanceledException> doit être géré dans un bloc catch séparé. Si un ou plusieurs délégués utilisateurs lèvent une OperationCanceledException(externalCT) (à l’aide d’un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externe), mais pas d’autre exception et que la requête était définie en tant que `AsParallel().WithCancellation(externalCT)`, PLINQ émettra un seul <xref:System.OperationCanceledException> (externalCT) plutôt qu’un <xref:System.AggregateException?displayProperty=nameWithType>. Toutefois, si un délégué utilisateur lève une <xref:System.OperationCanceledException>et qu’un autre délégué lève un autre type d’exception, les deux exceptions seront restaurées dans un <xref:System.AggregateException>.

Les recommandations générales pour l’annulation sont les suivantes :

1. Si vous effectuez l’annulation d’un délégué utilisateur, vous devez informer PLINQ de l’extérieur <xref:System.Threading.CancellationToken> et lever une <xref:System.OperationCanceledException> (externalCT).

2. Si l’annulation se produit et qu’aucune autre exception n’est levée, alors gérez un <xref:System.OperationCanceledException> plutôt qu’un <xref:System.AggregateException> .

## <a name="example"></a>Exemple

L’exemple suivant montre comment gérer l’annulation lorsque vous avez une fonction de calcul onéreux dans le code utilisateur.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Lorsque vous gérez l’annulation dans le code utilisateur, vous n’avez pas à utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> dans la définition de requête. Toutefois, nous vous recommandons d’utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> , car n' <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> a aucun effet sur les performances des requêtes et permet de gérer l’annulation par les opérateurs de requête et votre code utilisateur.

Pour garantir la réactivité du système, nous vous recommandons de vérifier les annulations toutes les millisecondes ; toutefois, une période jusqu'à 10 millisecondes est considérée comme acceptable. Cette fréquence ne doit pas avoir d’impact négatif sur le niveau de performance de votre code.

Lorsqu’un énumérateur est supprimé, par exemple lorsque le code s’arrête sur une boucle foreach (for each in Visual Basic) qui itère au sein des résultats de la requête, la requête est annulée, mais aucune exception n’est levée.

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
- [Annulation dans les threads managés](../threading/cancellation-in-managed-threads.md)
