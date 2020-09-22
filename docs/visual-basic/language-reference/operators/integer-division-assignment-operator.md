---
title: '\=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 6e749e13c0427354db9e361538d4bef10b6c6b04
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873411"
---
# <a name="-operator"></a>\\= (Opérateur)

Divise la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat entier à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Éléments  

 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  

 L’élément situé à gauche de l' `\=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).  
  
 L' `\=` opérateur divise la valeur d’une variable ou d’une propriété à sa gauche par la valeur de sa droite, et assigne le résultat entier à la variable ou à la propriété à sa gauche  
  
 Pour plus d’informations sur la Division d’entiers, consultez [\ Operator (Visual Basic)](integer-division-operator.md).  
  
## <a name="overloading"></a>Surcharge  

 L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `\` opérateur affecte le comportement de l' `\=` opérateur. Si votre code utilise `\=` sur une classe ou une structure qui surcharge `\` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `\=` opérateur pour diviser une `Integer` variable par une seconde et assigner le résultat de l’entier à la première variable.  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [\, Opérateur (Visual Basic)](integer-division-operator.md)
- [/=, Opérateur (Visual Basic)](floating-point-division-assignment-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Publication](../../programming-guide/language-features/statements.md)
