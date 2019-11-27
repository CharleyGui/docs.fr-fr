---
title: ^=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5e8fc2b64b9e7c33483612071d338a0ee22768
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331293"
---
# <a name="-operator-visual-basic"></a>^=, opérateur (Visual Basic)
Élève la valeur d’une variable ou d’une propriété à la puissance d’une expression et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Requis. Toute variable ou propriété numérique.  
  
 `expression`  
 Requis. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l’opérateur `^=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L’opérateur `^=` commence par déclencher la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) à la puissance de la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.  
  
 Visual Basic effectue toujours une élévation à la puissance dans le [type de données double](../../../visual-basic/language-reference/data-types/double-data-type.md). Les opérandes de tout type différent sont convertis en `Double`, et le résultat est toujours `Double`.  
  
 La valeur de `expression` peut être fractionnaire, négative ou les deux.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l’opérateur `^` affecte le comportement de l’opérateur `^=`. Si votre code utilise `^=` sur une classe ou une structure qui surcharge `^`, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `^=` pour élever la valeur d’une variable `Integer` à la puissance d’une deuxième variable et assigner le résultat à la première variable.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- [^, opérateur](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
