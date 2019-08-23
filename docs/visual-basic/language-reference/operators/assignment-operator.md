---
title: =, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962017"
---
# <a name="-operator-visual-basic"></a>=, opérateur (Visual Basic)
Assigne une valeur à une variable ou à une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Toute variable accessible en écriture ou toute propriété.  
  
 `value`  
 Tout littéral, constante ou expression.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche du signe égal (`=`) peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). L' `=` opérateur assigne la valeur à droite à la variable ou à la propriété à sa gauche.  
  
> [!NOTE]
> L' `=` opérateur est également utilisé comme un opérateur de comparaison. Pour plus d’informations, consultez [opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Surcharge  
 L' `=` opérateur peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’opérateur d’assignation. La valeur à droite est assignée à la variable située à gauche.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [&= (opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= (opérateur)](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= (opérateur)](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= (Opérateur)](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= (opérateur)](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
- [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
