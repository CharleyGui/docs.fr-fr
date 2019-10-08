---
title: From, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004782"
---
# <a name="from-clause-visual-basic"></a>From, clause (Visual Basic)
Spécifie une ou plusieurs variables de plage et une collection à interroger.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. *Variable de portée* utilisée pour itérer au sein des éléments de la collection. Une variable de portée est utilisée pour faire référence à chaque membre du `collection`, car la requête itère au sein de la `collection`. Doit être un type énumérable.|  
|`type`|facultatif. Type d'élément `element`. Si aucun `type` n’est spécifié, le type de `element` est déduit à partir de `collection`.|  
|`collection`|Obligatoire. Fait référence à la collection à interroger. Doit être un type énumérable.|  
  
## <a name="remarks"></a>Notes  
 La clause `From` est utilisée pour identifier les données sources d’une requête et les variables utilisées pour faire référence à un élément de la collection source. Ces variables sont appelées *variables de portée*. La clause `From` est requise pour une requête, sauf lorsque la clause `Aggregate` est utilisée pour identifier une requête qui retourne uniquement des résultats agrégés. Pour plus d’informations, consultez [Aggregate, clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Vous pouvez spécifier plusieurs clauses `From` dans une requête pour identifier plusieurs collections à joindre. Lorsque plusieurs regroupements sont spécifiés, ils sont itérés indépendamment ou vous pouvez les joindre s’ils sont liés. Vous pouvez joindre implicitement des collections à l’aide de la clause `Select`, ou explicitement à l’aide des clauses `Join` ou `Group Join`. En guise d’alternative, vous pouvez spécifier plusieurs variables et collections de portée dans une seule clause `From`, avec chaque variable de portée associée et chaque collection, séparées par une virgule. L’exemple de code suivant affiche les deux options de syntaxe pour la clause `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 La clause `From` définit la portée d’une requête, qui est similaire à la portée d’une boucle `For`. Par conséquent, chaque variable de portée `element` dans l’étendue d’une requête doit avoir un nom unique. Étant donné que vous pouvez spécifier plusieurs clauses `From` pour une requête, les clauses `From` suivantes peuvent faire référence à des variables de portée dans la clause `From`, ou elles peuvent faire référence à des variables de portée dans une clause `From` précédente. Par exemple, l’exemple suivant montre une clause `From` imbriquée dans laquelle la collection de la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Chaque clause `From` peut être suivie d’une combinaison quelconque de clauses de requête supplémentaires pour affiner la requête. Vous pouvez affiner la requête de l’une des manières suivantes :  
  
- Combinez plusieurs collections implicitement en utilisant les clauses `From` et `Select`, ou explicitement à l’aide des clauses `Join` ou `Group Join`.  
  
- Utilisez la clause `Where` pour filtrer le résultat de la requête.  
  
- Triez le résultat à l’aide de la clause `Order By`.  
  
- Regroupez les résultats similaires en utilisant la clause `Group By`.  
  
- Utilisez la clause `Aggregate` pour identifier les fonctions d’agrégation à évaluer pour l’ensemble du résultat de la requête.  
  
- Utilisez la clause `Let` pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.  
  
- Utilisez la clause `Distinct` pour ignorer les résultats de la requête en double.  
  
- Identifiez les parties du résultat à retourner à l’aide des clauses `Skip`, `Take`, `Skip While` et `Take While`.  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour chaque objet `Customer` dans la collection `customers`. La clause `Where` utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée. La boucle `For Each` affiche le nom de la société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate (clause)](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct (clause)](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join (clause)](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join (clause)](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let (clause)](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip (clause)](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While (clause)](../../../visual-basic/language-reference/queries/take-while-clause.md)
