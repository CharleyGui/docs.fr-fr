---
title: =, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350199"
---
# <a name="-operator-visual-basic"></a>=, opérateur (Visual Basic)
Assigns a value to a variable or property.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Any writable variable or any property.  
  
 `value`  
 Any literal, constant, or expression.  
  
## <a name="remarks"></a>Notes  
 The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). The `=` operator assigns the value on its right to the variable or property on its left.  
  
> [!NOTE]
> The `=` operator is also used as a comparison operator. For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Surcharge  
 The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 The following example demonstrates the assignment operator. The value on the right is assigned to the variable on the left.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [&= (opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= (opérateur)](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= (opérateur)](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= (opérateur)](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
- [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
