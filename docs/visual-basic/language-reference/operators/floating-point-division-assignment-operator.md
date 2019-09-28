---
title: /=, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592174"
---
# <a name="-operator-visual-basic"></a>/=, opérateur (Visual Basic)
Divise la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l’opérateur `/=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L’opérateur `/=` divise d’abord la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur affecte ensuite le résultat à virgule flottante de cette opération à la variable ou à la propriété.  
  
 Cette instruction affecte une valeur `Double` à la variable ou à la propriété située à gauche. Si `Option Strict` est `On`, `variableorproperty` doit être un `Double`. Si `Option Strict` est `Off`, Visual Basic effectue une conversion implicite et assigne la valeur résultante à `variableorproperty`, avec une erreur possible au moment de l’exécution. Pour plus d’informations, consultez [conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l’opérateur `/` affecte le comportement de l’opérateur `/=`. Si votre code utilise `/=` sur une classe ou une structure qui surcharge `/`, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `/=` pour diviser une variable `Integer` par une seconde et assigner le quotient à la première variable.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\ =, opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
