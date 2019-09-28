---
title: '&amp; =, opérateur (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591634"
---
# <a name="amp-operator-visual-basic"></a>&amp; =, opérateur (Visual Basic)
Concatène une expression `String` à une variable ou une propriété `String` et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété `String`.  
  
 `expression`  
 Obligatoire. Toute expression `String` .  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l’opérateur `&=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). L’opérateur `&=` concatène l’expression `String` de son côté droit à la variable ou à la propriété `String` à gauche, et assigne le résultat à la variable ou à la propriété située à gauche.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur &](../../../visual-basic/language-reference/operators/concatenation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l’opérateur `&` affecte le comportement de l’opérateur `&=`. Si votre code utilise `&=` sur une classe ou une structure qui surcharge `&`, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `&=` pour concaténer deux variables `String` et assigner le résultat à la première variable.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [& (opérateur)](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= (opérateur)](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
