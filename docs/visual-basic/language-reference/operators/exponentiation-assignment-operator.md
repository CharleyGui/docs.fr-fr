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
ms.openlocfilehash: e631cc9a484b56ee059449ca1fbd9fc69405333d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371399"
---
# <a name="-operator-visual-basic"></a>^=, opérateur (Visual Basic)
Élève la valeur d’une variable ou d’une propriété à la puissance d’une expression et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Éléments  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l' `^=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).  
  
 L' `^=` opérateur commence par déclencher la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) à la puissance de la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.  
  
 Visual Basic effectue toujours une élévation à la puissance dans le [type de données double](../data-types/double-data-type.md). Les opérandes de tout type différent sont convertis en `Double` , et le résultat est toujours `Double` .  
  
 La valeur de `expression` peut être fractionnaire, négative ou les deux.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur ^](exponentiation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `^` opérateur affecte le comportement de l' `^=` opérateur. Si votre code utilise `^=` sur une classe ou une structure qui surcharge `^` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `^=` opérateur pour élever la valeur d’une `Integer` variable à la puissance d’une deuxième variable et assigner le résultat à la première variable.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- [^ (Opérateur)](exponentiation-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Instructions](../../programming-guide/language-features/statements.md)
