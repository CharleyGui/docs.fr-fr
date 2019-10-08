---
title: Aggregate, clause (Visual Basic)
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
ms.openlocfilehash: 50a53cd45cc428541c90fbf82089518be2212fae
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004807"
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
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. Variable utilisée pour itérer au sein des éléments de la collection.|  
|`type`|facultatif. Type d'élément `element`. Si aucun type n’est spécifié, le type de `element` est déduit à partir de `collection`.|  
|`collection`|Obligatoire. Fait référence à la collection sur laquelle opérer.|  
|`clause`|facultatif. Une ou plusieurs clauses de requête, telles qu’une clause `Where`, pour affiner le résultat de la requête afin d’appliquer la ou les clauses d’agrégation à.|  
|`expressionList`|Obligatoire. Une ou plusieurs expressions délimitées par des virgules qui identifient une fonction d’agrégation à appliquer à la collection. Vous pouvez appliquer un alias à une fonction d’agrégation pour spécifier un nom de membre pour le résultat de la requête. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé. Pour obtenir des exemples, consultez la section relative aux fonctions d’agrégation plus loin dans cette rubrique.|  
  
## <a name="remarks"></a>Notes  
 La clause `Aggregate` peut être utilisée pour inclure des fonctions d’agrégation dans vos requêtes. Les fonctions d’agrégation effectuent des vérifications et des calculs sur un ensemble de valeurs et retournent une valeur unique. Vous pouvez accéder à la valeur calculée à l’aide d’un membre du type de résultat de la requête. Les fonctions d’agrégation standard que vous pouvez utiliser sont les fonctions `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min` et `Sum`. Ces fonctions sont familières aux développeurs qui sont familiarisés avec les agrégats dans SQL. Ils sont décrits dans la section suivante de cette rubrique.  
  
 Le résultat d’une fonction d’agrégation est inclus dans le résultat de la requête en tant que champ du type de résultat de la requête. Vous pouvez fournir un alias pour le résultat de la fonction d’agrégation afin de spécifier le nom du membre du type de résultat de la requête qui contiendra la valeur d’agrégation. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé.  
  
 La clause `Aggregate` peut commencer une requête, ou elle peut être incluse en tant que clause supplémentaire dans une requête. Si la clause `Aggregate` commence une requête, le résultat est une valeur unique qui est le résultat de la fonction d’agrégation spécifiée dans la clause `Into`. Si plusieurs fonctions d’agrégation sont spécifiées dans la clause `Into`, la requête retourne un type unique avec une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la clause `Into`. Si la clause `Aggregate` est incluse en tant que clause supplémentaire dans une requête, le type retourné dans la collection de requêtes aura une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la clause `Into`.  
  
## <a name="aggregate-functions"></a>Fonctions d'agrégation

Les fonctions d’agrégation standard qui peuvent être utilisées avec la clause `Aggregate` sont les suivantes.  
  
### <a name="all"></a>Tous

Retourne `true` si tous les éléments de la collection satisfont à une condition spécifiée. Sinon, retourne `false`. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Any

Retourne `true` si un élément de la collection satisfait à une condition spécifiée ; Sinon, retourne `false`. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Average

Calcule la moyenne de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Nombre

Compte le nombre d’éléments dans la collection. Vous pouvez fournir une expression `Boolean` facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Regrouper

Fait référence aux résultats de requête regroupés à la suite d’une clause `Group By` ou `Group Join`. La fonction `Group` est valide uniquement dans la clause `Into` d’une clause `Group By` ou `Group Join`. Pour plus d’informations et d’exemples, consultez [Group by](../../../visual-basic/language-reference/queries/group-by-clause.md) , clause et Group [join clause](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Compte le nombre d’éléments dans la collection. Vous pouvez fournir une expression `Boolean` facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition. Retourne le résultat sous la forme d’un `Long`. Pour obtenir un exemple, consultez la fonction d’agrégation `Count`.

### <a name="max"></a>Max

Calcule la valeur maximale de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Calcule la valeur minimale de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

Calcule la somme de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection. Voici un exemple :

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Exemple  

L’exemple suivant montre comment utiliser la clause `Aggregate` pour appliquer des fonctions d’agrégation à un résultat de requête.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Création de fonctions d’agrégation définies par l’utilisateur

 Vous pouvez inclure vos propres fonctions d’agrégation personnalisées dans une expression de requête en ajoutant des méthodes d’extension au type <xref:System.Collections.Generic.IEnumerable%601>. Votre méthode personnalisée peut ensuite effectuer un calcul ou une opération sur la collection énumérable qui a référencé votre fonction d’agrégation. Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Par exemple, l’exemple suivant montre une fonction d’agrégation personnalisée qui calcule la valeur médiane d’une collection de nombres. Il existe deux surcharges de la méthode d’extension `Median`. La première surcharge accepte, en entrée, une collection de type `IEnumerable(Of Double)`. Si la fonction d’agrégation `Median` est appelée pour un champ de requête de type `Double`, cette méthode est appelée. La deuxième surcharge de la méthode `Median` peut être passée à n’importe quel type générique. La surcharge générique de la méthode `Median` prend un deuxième paramètre qui fait référence à l’expression lambda `Func(Of T, Double)` pour projeter une valeur pour un type (à partir d’une collection) comme valeur correspondante de type `Double`. Il délègue ensuite le calcul de la valeur médiane à l’autre surcharge de la méthode `Median`. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 L’exemple suivant montre des exemples de requêtes qui appellent la fonction d’agrégation `Median` sur une collection de type `Integer`, et une collection de type `Double`. La requête qui appelle la fonction d’agrégation `Median` sur la collection de type `Double` appelle la surcharge de la méthode `Median` qui accepte, en entrée, une collection de type `Double`. La requête qui appelle la fonction d’agrégation `Median` sur la collection de type `Integer` appelle la surcharge générique de la méthode `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By (clause)](../../../visual-basic/language-reference/queries/group-by-clause.md)
