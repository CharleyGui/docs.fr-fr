---
title: '&amp;= (Opérateur)'
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
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371984"
---
# <a name="amp-operator-visual-basic"></a>&amp;=, Opérateur (Visual Basic)
Concatène une `String` expression à une `String` variable ou une propriété et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Éléments  
 `variableorproperty`  
 Obligatoire. Toute `String` variable ou propriété.  
  
 `expression`  
 Obligatoire. Toute expression `String` .  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l' `&=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md). L' `&=` opérateur concatène l' `String` expression à droite à la `String` variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur&](concatenation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `&` opérateur affecte le comportement de l' `&=` opérateur. Si votre code utilise `&=` sur une classe ou une structure qui surcharge `&` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `&=` opérateur pour concaténer deux `String` variables et assigner le résultat à la première variable.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérateur&](concatenation-operator.md)
- [Opérateur + =](addition-assignment-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs de concaténation](concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Instructions](../../programming-guide/language-features/statements.md)
