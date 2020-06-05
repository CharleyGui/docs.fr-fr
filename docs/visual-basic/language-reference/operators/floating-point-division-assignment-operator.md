---
title: /=, opérateur
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
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371243"
---
# <a name="-operator-visual-basic"></a>/=, opérateur (Visual Basic)
Divise la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Éléments  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l' `/=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).  
  
 L' `/=` opérateur divise d’abord la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur affecte ensuite le résultat à virgule flottante de cette opération à la variable ou à la propriété.  
  
 Cette instruction affecte une `Double` valeur à la variable ou à la propriété située à gauche. Si `Option Strict` est `On` , `variableorproperty` doit être un `Double` . Si `Option Strict` est `Off` , Visual Basic effectue une conversion implicite et assigne la valeur résultante à `variableorproperty` , avec une erreur possible au moment de l’exécution. Pour plus d’informations, consultez [conversions étendues et restrictives](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict Statement](../statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur/(Visual Basic)](floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `/` opérateur affecte le comportement de l' `/=` opérateur. Si votre code utilise `/=` sur une classe ou une structure qui surcharge `/` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `/=` opérateur pour diviser une `Integer` variable par une seconde et assigner le quotient à la première variable.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [/, Opérateur (Visual Basic)](floating-point-division-operator.md)
- [\\= (Opérateur)](integer-division-assignment-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Instructions](../../programming-guide/language-features/statements.md)
