---
title: AndAlso, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371932"
---
# <a name="andalso-operator-visual-basic"></a>Opérateur AndAlso (Visual Basic)
Effectue une conjonction logique de court-circuit sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`result`|Obligatoire. Toute expression `Boolean` . Le résultat est le `Boolean` résultat de la comparaison des deux expressions.|  
|`expression1`|Obligatoire. Toute expression `Boolean` .|  
|`expression2`|Obligatoire. Toute expression `Boolean` .|  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final. Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si les deux expressions ont la valeur `True` , `result` est `True` . Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est |Et `expression2` est|La valeur de `result` est|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(non évalué)|`False`|  
  
## <a name="data-types"></a>Types de données  
 L' `AndAlso` opérateur est défini uniquement pour le [type de données booléen](../data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’évaluer l’expression. Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type qui `False` devient `0` et `True` devient `-1` .
Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur and](and-operator.md) et l' [opérateur IsFalse](isfalse-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge `And` `IsFalse` des opérateurs et affecte le comportement de l' `AndAlso` opérateur. Si votre code utilise `AndAlso` sur une classe ou une structure qui surcharge `And` et `IsFalse` , veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `AndAlso` opérateur pour effectuer une conjonction logique sur deux expressions. Le résultat est une `Boolean` valeur qui indique si l’intégralité de l’expression conjointe a la valeur true. Si la première expression est `False` , la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 L’exemple précédent produit les résultats de `True` , `False` et `False` , respectivement. Dans le calcul de `secondCheck` , la deuxième expression n’est pas évaluée, car la première est déjà `False` . Toutefois, la deuxième expression est évaluée dans le calcul de `thirdCheck` .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une `Function` procédure qui recherche une valeur donnée parmi les éléments d’un tableau. Si le tableau est vide ou si la longueur du tableau a été dépassée, l' `While` instruction ne teste pas l’élément de tableau par rapport à la valeur de recherche.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [And, opérateur](and-operator.md)
- [IsFalse, opérateur](isfalse-operator.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
