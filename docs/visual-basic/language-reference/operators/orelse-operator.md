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
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860141"
---
# <a name="orelse-operator-visual-basic"></a>Opérateur OrElse (Visual Basic)
Effectue une disjonction logique inclusive sur deux expressions de court-circuit.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute expression `Boolean` .  
  
 `expression1`  
 Requis. Toute expression `Boolean` .  
  
 `expression2`  
 Requis. Toute expression `Boolean` .  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut ignorer l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire pour évaluer la deuxième expression, car elle ne peut pas changer le résultat final. Un court-circuit peut améliorer les performances si l’expression ignorée est complexe, ou si elle implique des appels de procédure.  
  
 Si une ou les deux expressions ont pour `True`, `result` est `True`. Le tableau suivant illustre comment `result` est déterminée.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(non évalué)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Types de données  
 Le `OrElse` opérateur est défini uniquement pour le [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’évaluer l’expression. Si vous affectez le résultat à un type numérique, Visual Basic convertit à partir `Boolean` à ce type de telle sorte que `False` devient `0` et `True` devient `-1`.
Pour plus d’informations, consultez [des Conversions de Type Boolean](../data-types/boolean-data-type.md#type-conversions)
  
## <a name="overloading"></a>Surcharge  
 Le [ou opérateur](../../../visual-basic/language-reference/operators/or-operator.md) et le [opérateur IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de cette classe ou une structure. La surcharge la `Or` et `IsTrue` opérateurs affecte le comportement de la `OrElse` opérateur. Si votre code utilise `OrElse` sur une classe ou structure qui surcharge `Or` et `IsTrue`, vérifiez que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise le `OrElse` opérateur effectue une disjonction logique sur deux expressions. Le résultat est un `Boolean` valeur qui représente si une des deux expressions est vraie. Si la première expression est `True`, la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 L’exemple précédent produit des résultats de `True`, `True`, et `False` respectivement. Dans le calcul de `firstCheck`, la seconde expression n’est pas évaluée, car le premier est déjà `True`. Toutefois, la seconde expression est évaluée dans le calcul de `secondCheck`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un `If`... `Then` instruction contenant deux appels de procédure. Si le premier appel retourne `True`, la deuxième procédure n’est pas appelée. Cela peut produire des résultats inattendus si la deuxième procédure effectue des tâches importantes qui doivent toujours être effectuées lors de l’exécution de cette section du code.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or (opérateur)](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue (opérateur)](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
