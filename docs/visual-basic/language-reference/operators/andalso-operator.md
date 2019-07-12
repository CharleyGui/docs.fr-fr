---
title: Opérateur AndAlso (Visual Basic)
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
ms.openlocfilehash: 1cb4d372d3ac228f29c6fa45f124796e5dfb6709
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859884"
---
# <a name="andalso-operator-visual-basic"></a>Opérateur AndAlso (Visual Basic)
Effectue une conjonction logique sur deux expressions de court-circuit.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`result`|Requis. Toute expression `Boolean` . Le résultat est le `Boolean` résultat de la comparaison des deux expressions.|  
|`expression1`|Requis. Toute expression `Boolean` .|  
|`expression2`|Requis. Toute expression `Boolean` .|  
  
## <a name="remarks"></a>Notes  
 Une opération logique est dite *court-circuit* si le code compilé peut ignorer l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire pour évaluer la deuxième expression, car elle ne peut pas changer le résultat final. Un court-circuit peut améliorer les performances si l’expression ignorée est complexe, ou si elle implique des appels de procédure.  
  
 Si les deux expressions ont `True`, `result` est `True`. Le tableau suivant illustre comment `result` est déterminée.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(non évalué)|`False`|  
  
## <a name="data-types"></a>Types de données  
 Le `AndAlso` opérateur est défini uniquement pour le [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’évaluer l’expression. Si vous affectez le résultat à un type numérique, Visual Basic convertit à partir `Boolean` à ce type de telle sorte que `False` devient `0` et `True` devient `-1`.
Pour plus d’informations, consultez [des Conversions de Type Boolean](../data-types/boolean-data-type.md#type-conversions)
  
## <a name="overloading"></a>Surcharge  
 Le [opérateur et](../../../visual-basic/language-reference/operators/and-operator.md) et le [opérateur IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de ce classe ou structure. La surcharge la `And` et `IsFalse` opérateurs affecte le comportement de la `AndAlso` opérateur. Si votre code utilise `AndAlso` sur une classe ou structure qui surcharge `And` et `IsFalse`, vérifiez que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise le `AndAlso` opérateur effectue une conjonction logique sur deux expressions. Le résultat est un `Boolean` valeur qui indique si l’ensemble unies expression a la valeur true. Si la première expression est `False`, la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 L’exemple précédent produit des résultats de `True`, `False`, et `False`, respectivement. Dans le calcul de `secondCheck`, la seconde expression n’est pas évaluée, car le premier est déjà `False`. Toutefois, la seconde expression est évaluée dans le calcul de `thirdCheck`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un `Function` procédure recherche une valeur donnée parmi les éléments d’un tableau. Si le tableau est vide ou si la longueur du tableau a été dépassée, le `While` instruction ne teste pas l’élément de tableau par rapport à la valeur de recherche.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And (opérateur)](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse (opérateur)](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
