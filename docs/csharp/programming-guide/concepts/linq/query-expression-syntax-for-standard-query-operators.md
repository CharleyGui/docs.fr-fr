---
title: Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: dac63ae165b88924cb0e91336571173f764569ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591427"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)
Certains des opérateurs de requête standard les plus courants ont une syntaxe de mots clés C# dédiée qui permet de les appeler dans le cadre d’une *expression de requête*. Une expression de requête est une façon différente et plus lisible d’exprimer une requête que son équivalent *fondé sur une méthode*. Les clauses d'expression de requête sont traduites en appels aux méthodes de requête lors de la compilation.  
  
## <a name="query-expression-syntax-table"></a>Tableau de syntaxe des expressions de requête  
 Le tableau ci-dessous répertorie les opérateurs de requête standard qui comportent des clauses d’expression de requête équivalentes.  
  
|Méthode|Syntaxe d'expression de requête C#|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Utilisez une variable de portée explicitement typée, par exemple :<br /><br /> `from int i in numbers`<br /><br /> (Pour plus d’informations, consultez [from, clause](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -ou-<br /><br /> `group … by … into …`<br /><br /> (Pour plus d’informations, consultez [group, clause](../../../language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Pour plus d’informations, consultez [join, clause](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Pour plus d’informations, consultez [join, clause](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Pour plus d’informations, consultez [select, clause](../../../language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Plusieurs clauses `from`.<br /><br /> (Pour plus d’informations, consultez [from, clause](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Pour plus d’informations, consultez [where, clause](../../../language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Classification des opérateurs de requête standard en fonction de leur mode d’exécution](./classification-of-standard-query-operators-by-manner-of-execution.md)
