---
title: OrElse, opérateur
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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401405"
---
# <a name="orelse-operator-visual-basic"></a>Opérateur OrElse (Visual Basic)
Effectue une disjonction logique inclusive de court-circuit sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Éléments  
 `result`  
 Obligatoire. Toute expression `Boolean` .  
  
 `expression1`  
 Obligatoire. Toute expression `Boolean` .  
  
 `expression2`  
 Obligatoire. Toute expression `Boolean` .  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final. Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si l’une ou l’autre ou les deux expressions ont la valeur `True` , `result` est `True` . Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est |Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(non évalué)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Types de données  
 L' `OrElse` opérateur est défini uniquement pour le [type de données booléen](../data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’évaluer l’expression. Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type qui `False` devient `0` et `True` devient `-1` .
Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur or](or-operator.md) et l' [opérateur IsTrue](istrue-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge `Or` `IsTrue` des opérateurs et affecte le comportement de l' `OrElse` opérateur. Si votre code utilise `OrElse` sur une classe ou une structure qui surcharge `Or` et `IsTrue` , veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `OrElse` opérateur pour effectuer une disjonction logique sur deux expressions. Le résultat est une `Boolean` valeur qui indique si l’une ou l’autre des deux expressions a la valeur true. Si la première expression est `True` , la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 L’exemple précédent produit les résultats de `True` , `True` et `False` respectivement. Dans le calcul de `firstCheck` , la deuxième expression n’est pas évaluée, car la première est déjà `True` . Toutefois, la deuxième expression est évaluée dans le calcul de `secondCheck` .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une `If` instruction... `Then` contenant deux appels de procédure. Si le premier appel retourne `True` , la deuxième procédure n’est pas appelée. Cela peut produire des résultats inattendus si la deuxième procédure exécute des tâches importantes qui doivent toujours être exécutées lorsque cette section du code s’exécute.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Or, opérateur](or-operator.md)
- [IsTrue, opérateur](istrue-operator.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
