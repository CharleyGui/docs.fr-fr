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
ms.openlocfilehash: eccea0b43564a4980778c9d1a5b8f9a8c2a9207d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874818"
---
# <a name="-operator-visual-basic"></a>=, opérateur (Visual Basic)

Assigne une valeur à une variable ou à une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Éléments  

 `variableorproperty`  
 Toute variable accessible en écriture ou toute propriété.  
  
 `value`  
 Tout littéral, constante ou expression.  
  
## <a name="remarks"></a>Notes  

 L’élément situé à gauche du signe égal ( `=` ) peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md). L' `=` opérateur assigne la valeur à droite à la variable ou à la propriété à sa gauche.  
  
> [!NOTE]
> L' `=` opérateur est également utilisé comme un opérateur de comparaison. Pour plus d’informations, consultez [opérateurs de comparaison](comparison-operators.md).  
  
## <a name="overloading"></a>Surcharge  

 L' `=` opérateur peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant illustre l’opérateur d’assignation. La valeur à droite est assignée à la variable située à gauche.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [&=, opérateur](and-assignment-operator.md)
- [* = (Opérateur)](multiplication-assignment-operator.md)
- [Opérateur + =](addition-assignment-operator.md)
- [-=, Opérateur (Visual Basic)](subtraction-assignment-operator.md)
- [/=, Opérateur (Visual Basic)](floating-point-division-assignment-operator.md)
- [\\= (Opérateur)](integer-division-assignment-operator.md)
- [^ = (Opérateur)](exponentiation-assignment-operator.md)
- [Publication](../../programming-guide/language-features/statements.md)
- [Opérateurs de comparaison](comparison-operators.md)
- [Lecture seule](../modifiers/readonly.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
