---
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412999"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate, clause (Visual Basic)
Applique une ou plusieurs fonctions d’agrégation à une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. Variable utilisée pour itérer au sein des éléments de la collection.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun type n’est spécifié, le type de `element` est déduit à partir de `collection` .|  
|`collection`|Obligatoire. Fait référence à la collection sur laquelle opérer.|  
|`clause`|Facultatif. Une ou plusieurs clauses de requête, telles qu’une `Where` clause, pour affiner le résultat de la requête afin d’appliquer la ou les clauses d’agrégation à.|  
|`expressionList`|Obligatoire. Une ou plusieurs expressions délimitées par des virgules qui identifient une fonction d’agrégation à appliquer à la collection. Vous pouvez appliquer un alias à une fonction d’agrégation pour spécifier un nom de membre pour le résultat de la requête. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé. Pour obtenir des exemples, consultez la section relative aux fonctions d’agrégation plus loin dans cette rubrique.|  
  
## <a name="remarks"></a>Notes  
 La `Aggregate` clause peut être utilisée pour inclure des fonctions d’agrégation dans vos requêtes. Les fonctions d’agrégation effectuent des vérifications et des calculs sur un ensemble de valeurs et retournent une valeur unique. Vous pouvez accéder à la valeur calculée à l’aide d’un membre du type de résultat de la requête. Les fonctions d’agrégation standard que vous pouvez utiliser sont `All` les `Any` fonctions,, `Average` ,,,, `Count` `LongCount` `Max` `Min` et `Sum` . Ces fonctions sont familières aux développeurs qui sont familiarisés avec les agrégats dans SQL. Ils sont décrits dans la section suivante de cette rubrique.  
  
 Le résultat d’une fonction d’agrégation est inclus dans le résultat de la requête en tant que champ du type de résultat de la requête. Vous pouvez fournir un alias pour le résultat de la fonction d’agrégation afin de spécifier le nom du membre du type de résultat de la requête qui contiendra la valeur d’agrégation. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé.  
  
 La `Aggregate` clause peut commencer une requête, ou elle peut être incluse en tant que clause supplémentaire dans une requête. Si la `Aggregate` clause commence une requête, le résultat est une valeur unique qui est le résultat de la fonction d’agrégation spécifiée dans la `Into` clause. Si plusieurs fonctions d’agrégation sont spécifiées dans la `Into` clause, la requête retourne un type unique avec une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause. Si la `Aggregate` clause est incluse en tant que clause supplémentaire dans une requête, le type retourné dans la collection de requêtes aura une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause.  
  
## <a name="aggregate-functions"></a>Fonctions d’agrégation

Les fonctions d’agrégation standard qui peuvent être utilisées avec la clause sont les suivantes `Aggregate` .  
  
### <a name="all"></a>Tous

Retourne `true` si tous les éléments de la collection satisfont à une condition spécifiée ; sinon, retourne `false` . Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Quelconque

Retourne `true` si un élément de la collection satisfait à une condition spécifiée ; sinon, retourne `false` . Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Average

Calcule la moyenne de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Count

Compte le nombre d’éléments dans la collection. Vous pouvez fournir une `Boolean` expression facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Groupe

Fait référence aux résultats de requête regroupés à la suite d' `Group By` une `Group Join` clause ou. La `Group` fonction est valide uniquement dans la `Into` clause d’une `Group By` `Group Join` clause ou. Pour plus d’informations et d’exemples, consultez [Group by](group-by-clause.md) , clause et Group [join clause](group-join-clause.md).

### <a name="longcount"></a>LongCount

Compte le nombre d’éléments dans la collection. Vous pouvez fournir une `Boolean` expression facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition. Retourne le résultat sous forme de `Long` . Pour obtenir un exemple, consultez la `Count` fonction Aggregate.

### <a name="max"></a>Max

Calcule la valeur maximale de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Calcule la valeur minimale de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>SUM

Calcule la somme de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Exemple  

L’exemple suivant montre comment utiliser la `Aggregate` clause pour appliquer des fonctions d’agrégation à un résultat de requête.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Création de fonctions d’agrégation définies par l’utilisateur

 Vous pouvez inclure vos propres fonctions d’agrégation personnalisées dans une expression de requête en ajoutant des méthodes d’extension au <xref:System.Collections.Generic.IEnumerable%601> type. Votre méthode personnalisée peut ensuite effectuer un calcul ou une opération sur la collection énumérable qui a référencé votre fonction d’agrégation. Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../programming-guide/language-features/procedures/extension-methods.md).  
  
 Par exemple, l’exemple suivant montre une fonction d’agrégation personnalisée qui calcule la valeur médiane d’une collection de nombres. Il existe deux surcharges de la `Median` méthode d’extension. La première surcharge accepte, en entrée, une collection de type `IEnumerable(Of Double)` . Si la `Median` fonction d’agrégation est appelée pour un champ de requête de type `Double` , cette méthode est appelée. La deuxième surcharge de la `Median` méthode peut être passée à n’importe quel type générique. La surcharge générique de la `Median` méthode prend un deuxième paramètre qui fait référence `Func(Of T, Double)` à l’expression lambda pour projeter une valeur pour un type (à partir d’une collection) comme valeur correspondante de type `Double` . Il délègue ensuite le calcul de la valeur médiane à l’autre surcharge de la `Median` méthode. Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 L’exemple suivant montre des exemples de requêtes qui appellent la `Median` fonction d’agrégation sur une collection de type `Integer` , et une collection de type `Double` . La requête qui appelle la `Median` fonction d’agrégation sur la collection de type `Double` appelle la surcharge de la `Median` méthode qui accepte, en entrée, une collection de type `Double` . La requête qui appelle la `Median` fonction d’agrégation sur la collection de type `Integer` appelle la surcharge générique de la `Median` méthode.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Clause WHERE](where-clause.md)
- [Group by, clause](group-by-clause.md)
