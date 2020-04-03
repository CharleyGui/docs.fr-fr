---
title: 'Comment : annuler une requête PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635877"
---
# <a name="how-to-cancel-a-plinq-query"></a>Comment : annuler une requête PLINQ
Les exemples suivants montrent deux façons de modifier une requête PLINQ. Le premier exemple montre comment annuler une requête principalement composée de parcours de données. Le deuxième exemple montre comment annuler une requête contenant une fonction d’utilisateur dont les calculs sont onéreux.

> [!NOTE]
> Quand l'option «Uniquement mon code» est activée, Visual Studio peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur « exception non gérée par le code utilisateur ». Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.
>
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Exemple

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

L’infrastructure PLINQ ne restaure pas un seul <xref:System.OperationCanceledException> dans un <xref:System.AggregateException?displayProperty=nameWithType> ; le <xref:System.OperationCanceledException> doit être géré dans un bloc catch séparé. Si un ou plusieurs délégués utilisateurs lèvent une OperationCanceledException(externalCT) (à l’aide d’un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externe), mais pas d’autre exception et que la requête était définie en tant que `AsParallel().WithCancellation(externalCT)`, PLINQ émettra un seul <xref:System.OperationCanceledException> (externalCT) plutôt qu’un <xref:System.AggregateException?displayProperty=nameWithType>. Toutefois, si un délégué utilisateur lève une <xref:System.OperationCanceledException>et qu’un autre délégué lève un autre type d’exception, les deux exceptions seront restaurées dans un <xref:System.AggregateException>.

Les recommandations générales pour l’annulation sont les suivantes :

1. Si vous effectuez l’annulation utilisateur-délégué, vous <xref:System.Threading.CancellationToken> devez <xref:System.OperationCanceledException>informer PLINQ de l’externe et lancer un (externalCT).

2. Si l’annulation se produit et aucune <xref:System.OperationCanceledException> autre <xref:System.AggregateException>exception n’est lancée, alors manipulez un plutôt que un .

## <a name="example"></a>Exemple

L’exemple suivant montre comment gérer l’annulation lorsque vous avez une fonction de calcul onéreux dans le code utilisateur.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Lorsque vous gérez l’annulation dans le code utilisateur, vous n’avez pas à utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> dans la définition de requête. Cependant, nous vous avons <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>recommandé <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> d’utiliser, car n’a aucun effet sur les performances de requête et il permet à l’annulation d’être traitée par les opérateurs de requête et votre code utilisateur.

Pour garantir la réactivité du système, nous vous recommandons de vérifier les annulations toutes les millisecondes ; toutefois, une période jusqu'à 10 millisecondes est considérée comme acceptable. Cette fréquence ne doit pas avoir d’impact négatif sur le niveau de performance de votre code.

Lorsqu’un enumérateur est éliminé, par exemple lorsque le code sort d’une boucle de préach (pour chacun dans Visual Basic) qui s’agite sur les résultats des requêtes, la requête est annulée, mais aucune exception n’est lancée.

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
