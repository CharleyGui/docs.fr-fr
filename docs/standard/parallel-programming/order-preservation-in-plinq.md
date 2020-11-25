---
title: Conservation de l'ordre en PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
ms.openlocfilehash: 997bb80b6e30d4769613c4a1df647e6cd475a8ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730602"
---
# <a name="order-preservation-in-plinq"></a>Conservation de l'ordre en PLINQ

Dans PLINQ, l’objectif est d’augmenter les performances tout en préservant l’exactitude. Une requête doit s’exécuter aussi rapidement que possible, mais toujours générer des résultats corrects. Dans certains cas, l’exactitude requiert que l’ordre de la séquence source soit conservé ; toutefois, le classement peut coûter cher en calcul. Par conséquent, par défaut, PLINQ ne conserve pas l’ordre de la séquence source. À cet égard, PLINQ est similaire à [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], mais pas à LINQ to Objects, qui conserve le classement.  
  
 Pour remplacer le comportement par défaut, vous pouvez activer la conservation de l’ordre à l’aide de l’opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sur la séquence source. Vous pouvez désactiver la préservation de l’ordre plus loin dans la requête à l’aide de la méthode <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>. Ces deux méthodes permettent de traiter la requête en fonction des paramètres heuristiques, qui déterminent s’il faut exécuter la requête en parallèle ou de manière séquentielle. Pour plus d’informations, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
 L’exemple suivant montre une requête parallèle non classée qui filtre tous les éléments qui correspondent à une condition, sans essayer de classer les résultats de quelque manière que ce soit.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Cette requête ne produit pas nécessairement les 1 000 premières villes de la séquence source qui remplissent la condition, mais plutôt un ensemble de 1 000 villes qui remplissent la condition. Les opérateurs de requête PLINQ partitionnent la séquence source en plusieurs sous-séquences qui sont traitées comme des tâches simultanées. Si la conservation de l’ordre n’est pas spécifiée, les résultats de chaque partition sont remis à l’étape suivante de la requête dans un ordre arbitraire. Par ailleurs, une partition peut donner un sous-ensemble de ses résultats avant de continuer à traiter les éléments restants. L’ordre résultant peut être différent à chaque fois. Ceci ne peut pas être contrôlé par votre application, car cela dépend de la manière dont le système d’exploitation planifie les threads.  
  
 L’exemple suivant remplace le comportement par défaut à l’aide de l’opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sur la séquence source. Cela garantit que la méthode <xref:System.Linq.ParallelEnumerable.Take%2A> retourne les 1 000 premières villes de la séquence source qui remplissent la condition.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Toutefois, cette requête ne s’exécute probablement pas aussi rapidement que la version non classée, car elle doit surveiller l’ordre d’origine dans toutes les partitions et s’assurer que le classement est cohérent au moment de la fusion. Par conséquent, nous vous recommandons de n’utiliser <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> que si c’est nécessaire, et uniquement pour les parties de la requête qui l’exigent. Lorsque la conservation de l’ordre n’est plus nécessaire, utilisez <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> pour la désactiver. L’exemple suivant obtient ce résultat en composant deux requêtes.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Notez que PLINQ conserve le classement d’une séquence produite par des opérateurs imposant un ordre pour le reste de la requête. En d’autres termes, les opérateurs tels que <xref:System.Linq.ParallelEnumerable.OrderBy%2A> et <xref:System.Linq.ParallelEnumerable.ThenBy%2A> sont traités comme s’ils étaient suivis d’un appel à <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Opérateurs de requête et de classement  

 Les opérateurs de requête suivants présentent la conservation de l’ordre dans toutes les opérations suivantes d’une requête, ou jusqu'à ce que <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> soit appelée :  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 dans certains cas, les opérateurs de requête PLINQ suivants peuvent exiger des séquences source classées pour produire des résultats corrects :  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 certains opérateurs de requête PLINQ se comportent différemment, selon que leur séquence source est classée ou non classée. Le tableau suivant répertorie ces opérateurs.  
  
|Opérateur|Résultat lorsque la séquence source est classée|Résultat de la séquence source n’est pas classée|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Résultats non classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Exécute de façon non déterministe en parallèle|Exécute de façon non déterministe en parallèle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Retourner un élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Réorganise la séquence|Démarre une nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Réorganise la séquence|Démarre une nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Non applicable (même valeur par défaut que <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Non applicable (même valeur par défaut que <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Inverse|Sans effet|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indexé)|Résultats classés|Résultats non classés.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Résultats classés.|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indexé)|Résultats classés.|Résultats non classés.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Comparaison classée|Comparaison non classée|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Ignore les *n* premiers éléments|Ignore les *n* éléments|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Résultats classés.|Non déterministe. Exécute SkipWhile dans l’ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Prend les premiers éléments `n`|Prend tous les éléments `n`|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Résultats classés|Non déterministe. Exécute TakeWhile dans l’ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Complète `OrderBy`|Complète `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Complète `OrderBy`|Complète `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indexé)|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Résultats classés|Résultats non classés|  
  
 Les résultats non classés ne sont pas mélangés de manière active ; aucune logique de classement spéciale ne leur est appliquée. Dans certains cas, une requête non classée peut conserver le classement de la séquence source. Pour les requêtes utilisant l’opérateur Select indexé, PLINQ garantit que les éléments de sortie arriveront dans l’ordre des indices croissant, mais n’offre aucune garantie quant aux index qui seront affectés aux éléments respectifs.  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
- [Programmation parallèle](index.md)
