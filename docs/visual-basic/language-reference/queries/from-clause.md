---
title: From (clause)
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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396179"
---
# <a name="from-clause-visual-basic"></a>From, clause (Visual Basic)
Spécifie une ou plusieurs variables de plage et une collection à interroger.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. *Variable de portée* utilisée pour itérer au sein des éléments de la collection. Une variable de portée est utilisée pour faire référence à chaque membre du au `collection` fur et à mesure que la requête itère au sein de `collection` . Doit être un type énumérable.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun `type` n’est spécifié, le type de `element` est déduit à partir de `collection` .|  
|`collection`|Obligatoire. Fait référence à la collection à interroger. Doit être un type énumérable.|  
  
## <a name="remarks"></a>Notes  
 La `From` clause est utilisée pour identifier les données sources d’une requête et les variables utilisées pour faire référence à un élément de la collection source. Ces variables sont appelées *variables de portée*. La `From` clause est requise pour une requête, sauf lorsque la `Aggregate` clause est utilisée pour identifier une requête qui retourne uniquement des résultats agrégés. Pour plus d’informations, consultez [Aggregate, clause](aggregate-clause.md).  
  
 Vous pouvez spécifier plusieurs `From` clauses dans une requête pour identifier plusieurs collections à joindre. Lorsque plusieurs regroupements sont spécifiés, ils sont itérés indépendamment ou vous pouvez les joindre s’ils sont liés. Vous pouvez joindre implicitement des collections à l’aide de la `Select` clause, ou explicitement à l’aide des `Join` `Group Join` clauses ou. En guise d’alternative, vous pouvez spécifier plusieurs variables de plage et collections dans une seule `From` clause, chaque variable de portée et collection étant séparée des autres par une virgule. L’exemple de code suivant montre les deux options de syntaxe pour la `From` clause.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 La `From` clause définit la portée d’une requête, qui est similaire à la portée d’une `For` boucle. Par conséquent, chaque variable de portée `element` dans l’étendue d’une requête doit avoir un nom unique. Étant donné que vous pouvez spécifier plusieurs `From` clauses pour une requête, `From` les clauses suivantes peuvent faire référence à des variables de portée dans la `From` clause, ou elles peuvent faire référence à des variables de portée dans une `From` clause précédente. Par exemple, l’exemple suivant montre une clause imbriquée dans `From` laquelle la collection de la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Chaque `From` clause peut être suivie d’une combinaison quelconque de clauses de requête supplémentaires pour affiner la requête. Vous pouvez affiner la requête de l’une des manières suivantes :  
  
- Combinez plusieurs collections implicitement en utilisant `From` les `Select` clauses et, ou explicitement à l’aide des `Join` `Group Join` clauses ou.  
  
- Utilisez la `Where` clause pour filtrer le résultat de la requête.  
  
- Triez le résultat à l’aide de la `Order By` clause.  
  
- Regroupez les résultats similaires en utilisant la `Group By` clause.  
  
- Utilisez la `Aggregate` clause pour identifier les fonctions d’agrégation à évaluer pour l’ensemble du résultat de la requête.  
  
- Utilisez la `Let` clause pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.  
  
- Utilisez la `Distinct` clause pour ignorer les résultats de la requête en double.  
  
- Identifiez les parties du résultat à retourner à l’aide des `Skip` `Take` `Skip While` clauses,, et `Take While` .  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une `From` clause pour déclarer une variable `cust` de portée pour chaque `Customer` objet de la `customers` collection. La `Where` clause utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée. La `For Each` boucle affiche le nom de la société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes](index.md)
- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next (instruction)](../statements/for-each-next-statement.md)
- [For...Next (instruction)](../statements/for-next-statement.md)
- [Clause SELECT](select-clause.md)
- [Clause WHERE](where-clause.md)
- [Aggregate Clause](aggregate-clause.md)
- [Distinct (clause)](distinct-clause.md)
- [Join (clause)](join-clause.md)
- [Group Join (clause)](group-join-clause.md)
- [Order By (clause)](order-by-clause.md)
- [Clause let](let-clause.md)
- [Skip (clause)](skip-clause.md)
- [Take (clause)](take-clause.md)
- [SkipWhile (clause)](skip-while-clause.md)
- [Take While (clause)](take-while-clause.md)
