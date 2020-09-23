---
title: Syntaxe des expressions de requête pour les opérateurs de requête standard
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: 57a08f6540cbf3e091ee1b2e202e0e181487e3be
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090246"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>Syntaxe des expressions de requête pour les opérateurs de requête standard (Visual Basic)

Certains des opérateurs de requête standard les plus fréquemment utilisés ont une syntaxe de mot clé de langage Visual Basic dédiée qui leur permet d’être appelés dans le cadre d’une *expression de requête*. Une expression de requête est une façon différente et plus lisible d’exprimer une requête que son équivalent *fondé sur une méthode*. Les clauses d'expression de requête sont traduites en appels aux méthodes de requête lors de la compilation.  
  
## <a name="query-expression-syntax-table"></a>Tableau de syntaxe des expressions de requête  

 Le tableau ci-dessous répertorie les opérateurs de requête standard qui comportent des clauses d’expression de requête équivalentes.  
  
|Méthode|Syntaxe des expressions de requête Visual Basic|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (Pour plus d’informations, consultez [from, clause](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (Pour plus d’informations, consultez [clause distinct](../../../language-reference/queries/distinct-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (Pour plus d’informations, consultez [Group by, clause](../../../language-reference/queries/group-by-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (Pour plus d’informations, consultez [Group Join, clause](../../../language-reference/queries/group-join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> - ou -<br /><br /> `Join … [As …]In … On …`<br /><br /> (Pour plus d’informations, consultez [join, clause](../../../language-reference/queries/join-clause.md).)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (Pour plus d’informations, consultez [Select, clause](../../../language-reference/queries/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Plusieurs `From` clauses<br /><br /> (Pour plus d’informations, consultez [from, clause](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (Pour plus d’informations, consultez [Skip, clause](../../../language-reference/queries/skip-clause.md).)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (Pour plus d’informations, consultez [clause Skip While](../../../language-reference/queries/skip-while-clause.md).)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (Pour plus d’informations, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (Pour plus d’informations, consultez [Take, clause](../../../language-reference/queries/take-clause.md).)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (Pour plus d’informations, consultez [clause Take While](../../../language-reference/queries/take-while-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (Pour plus d’informations, consultez [Where, clause](../../../language-reference/queries/where-clause.md).)|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Classification des opérateurs de requête standard par mode d’exécution (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
