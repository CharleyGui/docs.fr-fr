---
title: 'Comment : calculer des valeurs numériques'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348968"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Comment : calculer des valeurs numériques (Visual Basic)
You can calculate numeric values through the use of numeric expressions. A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.  
  
## <a name="calculating-numeric-values"></a>Calculating Numeric Values  
  
#### <a name="to-calculate-a-numeric-value"></a>To calculate a numeric value  
  
- Combine one or more numeric literals, constants, and variables into a numeric expression. The following example shows some valid numeric expressions.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     The first three lines show a literal, a constant, and a variable. Each one forms a valid numeric expression by itself. The final line shows a combination of a variable with two literals.  
  
     Note that a numeric expression does not form a complete Visual Basic statement by itself. You must use the expression as part of a complete statement.  
  
#### <a name="to-store-a-numeric-value"></a>To store a numeric value  
  
- You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.  
  
     Pour plus d’informations, consultez [Instructions](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Multiple Operators  
 If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence. To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.  
  
#### <a name="to-override-normal-operator-precedence"></a>To override normal operator precedence  
  
- Use parentheses to enclose the operations you want to be performed first. The following example shows two different results with the same operands and operators.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69). The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).  
  
     For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instructions](../../../../visual-basic/language-reference/statements/index.md)
- [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
