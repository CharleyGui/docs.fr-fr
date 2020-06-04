---
title: Classification des opérateurs de requête standard en fonction de leur mode d’exécution
ms.date: 07/20/2015
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
ms.openlocfilehash: e1ba5d8bdc2b7a521a11ca5c055323fde4bcb9d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410901"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Classification des opérateurs de requête standard par mode d’exécution (Visual Basic)
Les implémentations LINQ to Objects des méthodes d’opérateur de requête standard s’exécutent de deux manières principales : immédiate ou différée. En outre, les opérateurs de requête qui utilisent l’exécution différée peuvent être divisés en deux catégories : ceux prenant en charge la diffusion en continu et ceux ne la prenant pas en charge. Le fait de connaître le mode d’exécution des différents opérateurs de requête peut vous aider à comprendre les résultats obtenus à partir d’une requête donnée. Ceci est particulièrement vrai si la source de données change ou si vous générez une requête sur une autre requête. Cette rubrique classe les opérateurs de requête standard selon leur mode d’exécution.  
  
## <a name="manners-of-execution"></a>Modes d’exécution  
  
### <a name="immediate"></a>Immédiat  
 L’exécution immédiate signifie que la source de données est lue et que l’opération est effectuée au point où la requête est déclarée dans le code. Tous les opérateurs de requête standard qui retournent un résultat unique et non énumérable s’exécutent immédiatement.  
  
### <a name="deferred"></a>Différé  
 L’exécution différée signifie que l’opération n’est pas effectuée au point où la requête est déclarée dans le code. L’opération est effectuée uniquement quand la variable de requête est énumérée, par exemple à l’aide d’une instruction `For Each`. Cela signifie que les résultats de l’exécution de la requête dépendent du contenu de la source de données au moment de l’exécution de la requête, et non au moment de sa définition. Si la variable de requête est énumérée plusieurs fois, les résultats peuvent différer chaque fois. Presque tous les opérateurs de requête standard dont le type de retour est <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IOrderedEnumerable%601> s’exécutent de manière différée.  
  
 Les opérateurs de requête qui utilisent l’exécution différée peuvent également être classés comme prenant en charge la diffusion en continu ou non.  
  
#### <a name="streaming"></a>Diffusion en continu  
 Les opérateurs prenant en charge la diffusion en continu n’ont pas à lire toutes les données sources avant de générer des éléments. Au moment de l’exécution, un opérateur prenant en charge la diffusion en continu effectue son opération sur chaque élément source à mesure qu’il est lu et génère l’élément si nécessaire. Ce type d’opérateur continue à lire des éléments source jusqu’à ce qu’un élément de résultat puisse être produit. Cela signifie que plusieurs éléments source peuvent être lus pour produire un élément de résultat.  
  
#### <a name="non-streaming"></a>Sans diffusion en continu  
 Les opérateurs ne prenant pas en charge la diffusion en continu doivent lire toutes les données source avant de générer un élément de résultat. Les opérations telles que le tri ou le regroupement font partie de cette catégorie. Au moment de l’exécution, les opérateurs de requête ne prenant pas en charge la diffusion en continu lisent toutes les données source, les placent dans une structure de données, puis effectuent l’opération et génèrent les éléments de résultat.  
  
## <a name="classification-table"></a>Tableau de classification  
 Le tableau suivant classe chaque méthode d’opérateur de requête standard en fonction de son mode d’exécution.  
  
> [!NOTE]
> Si un opérateur est présent dans deux colonnes, deux séquences d’entrée sont impliquées dans l’opération et chacune d’elles est évaluée différemment. Dans ces cas, la première séquence dans la liste de paramètres est toujours évaluée de façon différée, avec diffusion en continu.  
  
|Opérateur de requête standard|Type de retour|Exécution immédiate|Exécution différée avec diffusion en continu|Exécution différée sans diffusion en continu|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Valeur numérique unique|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|Valeur numérique unique, TSource ou TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Valeur numérique unique, TSource ou TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|Valeur numérique unique|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|Tableau TSource|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Syntaxe des expressions de requête pour les opérateurs de requête standard (Visual Basic)](query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
