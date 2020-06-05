---
title: +=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372205"
---
# <a name="-operator-visual-basic"></a>+= (opérateur Visual Basic)
Ajoute la valeur d’une expression numérique à la valeur d’une variable ou d’une propriété numérique et assigne le résultat à la variable ou à la propriété. Peut également être utilisé pour concaténer une `String` expression à une `String` variable ou une propriété et assigner le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Éléments  
 `variableorproperty`  
 Obligatoire. Toute variable ou `String` propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression ou numérique `String` .  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l' `+=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).  
  
 L' `+=` opérateur ajoute la valeur à droite à la variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche. L' `+=` opérateur peut également être utilisé pour concaténer l' `String` expression à droite à la `String` variable ou à la propriété à sa gauche, et assigner le résultat à la variable ou à la propriété à sa gauche.  
  
> [!NOTE]
> Lorsque vous utilisez l' `+=` opérateur, vous ne pourrez peut-être pas déterminer si l’addition ou la concaténation de chaînes aura lieu. Utilisez l' `&=` opérateur pour la concaténation afin d’éliminer toute ambiguïté et de fournir du code auto-documenté.  
  
 Cet opérateur d’assignation effectue implicitement des conversions étendues mais non restrictives si l’environnement de compilation impose une sémantique stricte. Pour plus d’informations sur ces conversions, consultez [élargissement et conversions restrictives](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Pour plus d’informations sur la sémantique stricte et permissive, consultez [Option Strict Statement](../statements/option-strict-statement.md).  
  
 Si la sémantique permissive est autorisée, l' `+=` opérateur effectue implicitement une variété de conversions de chaîne et numériques identiques à celles effectuées par l' `+` opérateur. Pour plus d’informations sur ces conversions, consultez [opérateur +](addition-operator.md).  
  
## <a name="overloading"></a>Surcharge  
 L' `+` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `+` opérateur affecte le comportement de l' `+=` opérateur. Si votre code utilise `+=` sur une classe ou une structure qui surcharge `+` , assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `+=` opérateur pour combiner la valeur d’une variable à une autre. La première partie utilise `+=` des variables numériques pour ajouter une valeur à une autre. La deuxième partie utilise `+=` avec des `String` variables pour concaténer une valeur avec une autre. Dans les deux cas, le résultat est affecté à la première variable.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 La valeur de `num1` est maintenant 13 et la valeur de `str1` est maintenant « 103 ».  
  
## <a name="see-also"></a>Voir aussi

- [Opérateur +](addition-operator.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Opérateurs de concaténation](concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Instructions](../../programming-guide/language-features/statements.md)
