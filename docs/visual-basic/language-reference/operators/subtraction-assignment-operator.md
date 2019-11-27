---
title: -=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 44cb226d64e9f0b86c6566eb25fbafd6323a6d4c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347809"
---
# <a name="--operator-visual-basic"></a>-=, opérateur (Visual Basic)
Soustrait la valeur d’une expression de la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Requis. Toute variable ou propriété numérique.  
  
 `expression`  
 Requis. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l’opérateur `-=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L’opérateur `-=` soustrait d’abord la valeur de l’expression (sur le côté droit de l’opérateur) de la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur). L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur-(Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge de l’opérateur `-` affecte le comportement de l’opérateur `-=`. Si votre code utilise `-=` sur une classe ou une structure qui surcharge `-`, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `-=` pour soustraire une variable `Integer` d’une autre et assigner le résultat à cette dernière variable.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- [-, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
