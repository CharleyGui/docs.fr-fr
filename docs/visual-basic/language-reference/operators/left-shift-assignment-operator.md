---
title: <<=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 72fc842002586a4d5e48bc39b5c785fc6a9e9451
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866906"
---
# <a name="-operator-visual-basic"></a>\<\<=, Opérateur (Visual Basic)

Effectue un décalage arithmétique vers la gauche sur la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Éléments  

 `variableorproperty`  
 Obligatoire. Variable ou propriété d’un type intégral ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` ou `ULong` ).  
  
 `amount`  
 Obligatoire. Expression numérique d’un type de données qui s’étend à `Integer` .  
  
## <a name="remarks"></a>Notes  

 L’élément situé à gauche de l' `<<=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).  
  
 L' `<<=` opérateur effectue d’abord un décalage arithmétique vers la gauche sur la valeur de la variable ou de la propriété. L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.  
  
## <a name="overloading"></a>Surcharge  

 L' [ opérateur<< ](left-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `<<` opérateur affecte le comportement de l' `<<=` opérateur. Si votre code utilise `<<=` sur une classe ou une structure qui surcharge `<<` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `<<=` opérateur pour décaler le modèle binaire d’une variable vers la `Integer` gauche selon la valeur spécifiée et assigner le résultat à la variable.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Voir aussi

- [ Opérateur<< ](left-shift-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs de décalage de bits](bit-shift-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Publication](../../programming-guide/language-features/statements.md)
