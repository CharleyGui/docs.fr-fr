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
ms.openlocfilehash: b3801c7e05142e1bc793e3c9d49a6f6991756f9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350237"
---
# <a name="andalso-operator-visual-basic"></a>Opérateur AndAlso (Visual Basic)
Effectue une conjonction logique de court-circuit sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`result`|Requis. Toute expression `Boolean` . Le résultat est le résultat `Boolean` de la comparaison des deux expressions.|  
|`expression1`|Requis. Toute expression `Boolean` .|  
|`expression2`|Requis. Toute expression `Boolean` .|  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final. Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si les deux expressions ont la valeur `True`, `result` est `True`. Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(non évalué)|`False`|  
  
## <a name="data-types"></a>Types de données  
 L’opérateur `AndAlso` est défini uniquement pour le [type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire pour `Boolean` avant l’évaluation de l’expression. Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type de sorte que `False` devienne `0` et `True` devient `-1`.
Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur and](../../../visual-basic/language-reference/operators/and-operator.md) et l' [opérateur IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge des opérateurs `And` et `IsFalse` affecte le comportement de l’opérateur `AndAlso`. Si votre code utilise `AndAlso` sur une classe ou une structure qui surcharge `And` et `IsFalse`, veillez à bien comprendre leur comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `AndAlso` pour effectuer une conjonction logique sur deux expressions. Le résultat est une valeur `Boolean` qui indique si l’intégralité de l’expression conjointe a la valeur true. Si la première expression est `False`, la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 L’exemple précédent produit respectivement les résultats de `True`, `False`et `False`. Dans le calcul de `secondCheck`, la deuxième expression n’est pas évaluée, car la première est déjà `False`. Toutefois, la deuxième expression est évaluée dans le calcul de `thirdCheck`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une procédure `Function` qui recherche une valeur donnée parmi les éléments d’un tableau. Si le tableau est vide ou si la longueur du tableau a été dépassée, l’instruction `While` ne teste pas l’élément de tableau par rapport à la valeur de recherche.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And (opérateur)](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse (opérateur)](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
