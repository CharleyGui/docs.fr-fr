---
title: Opérateur OrElse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835242"
---
# <a name="orelse-operator-visual-basic"></a>Opérateur OrElse (Visual Basic)
Effectue une disjonction logique inclusive de court-circuit sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute expression `Boolean` .  
  
 `expression1`  
 Obligatoire. Toute expression `Boolean` .  
  
 `expression2`  
 Obligatoire. Toute expression `Boolean` .  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final. Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si l’une ou les deux expressions ont la valeur `True`, `result` est `True`. Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(non évalué)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Types de données  
 L’opérateur `OrElse` est défini uniquement pour le [type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire pour `Boolean` avant d’évaluer l’expression. Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type de sorte que `False` devient `0` et `True` devient `-1`.
Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur or](../../../visual-basic/language-reference/operators/or-operator.md) et l' [opérateur IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge des opérateurs `Or` et `IsTrue` affecte le comportement de l’opérateur `OrElse`. Si votre code utilise `OrElse` sur une classe ou une structure qui surcharge `Or` et `IsTrue`, assurez-vous que vous comprenez le comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `OrElse` pour effectuer une disjonction logique sur deux expressions. Le résultat est une valeur `Boolean` qui indique si l’une ou l’autre des deux expressions a la valeur true. Si la première expression est `True`, la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 L’exemple précédent produit les résultats de `True`, `True` et `False`, respectivement. Dans le calcul de `firstCheck`, la deuxième expression n’est pas évaluée, car la première est déjà `True`. Toutefois, la deuxième expression est évaluée dans le calcul de `secondCheck`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une instruction `If`... `Then` contenant deux appels de procédure. Si le premier appel retourne `True`, la deuxième procédure n’est pas appelée. Cela peut produire des résultats inattendus si la deuxième procédure exécute des tâches importantes qui doivent toujours être exécutées lorsque cette section du code s’exécute.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or (opérateur)](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue (opérateur)](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
