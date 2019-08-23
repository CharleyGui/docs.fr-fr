---
title: += (opérateur Visual Basic)
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
ms.openlocfilehash: f615df50643912beb12eb89d80b922fc30a3e6df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944475"
---
# <a name="-operator-visual-basic"></a>+= (opérateur Visual Basic)
Ajoute la valeur d’une expression numérique à la valeur d’une variable ou d’une propriété numérique et assigne le résultat à la variable ou à la propriété. Peut également être utilisé pour concaténer une `String` expression à une `String` variable ou une propriété et assigner le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Requis. Toute `String` variable ou propriété numérique.  
  
 `expression`  
 Requis. Toute expression ou `String` numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l' `+=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L' `+=` opérateur ajoute la valeur à droite à la variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche. L' `+=` opérateur peut également être utilisé pour concaténer l' `String` expression à droite à la variable `String` ou à la propriété à sa gauche, et assigner le résultat à la variable ou à la propriété à sa gauche.  
  
> [!NOTE]
> Lorsque vous utilisez l' `+=` opérateur, vous ne pourrez peut-être pas déterminer si l’addition ou la concaténation de chaînes aura lieu. Utilisez l' `&=` opérateur pour la concaténation afin d’éliminer toute ambiguïté et de fournir du code auto-documenté.  
  
 Cet opérateur d’assignation effectue implicitement des conversions étendues mais non restrictives si l’environnement de compilation impose une sémantique stricte. Pour plus d’informations sur ces conversions, consultez [élargissement et](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)conversions restrictives. Pour plus d’informations sur la sémantique stricte et permissive, consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Si la sémantique permissive est autorisée `+=` , l’opérateur effectue implicitement une variété de conversions de chaîne et numériques identiques à celles `+` effectuées par l’opérateur. Pour plus d’informations sur ces conversions, consultez [opérateur +](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Surcharge  
 L' `+` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l' `+` opérateur affecte le comportement de l' `+=` opérateur. Si votre code utilise `+=` sur une classe ou une structure qui `+`surcharge, assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise l' `+=` opérateur pour combiner la valeur d’une variable à une autre. La première partie utilise `+=` des variables numériques pour ajouter une valeur à une autre. La deuxième partie utilise `+=` avec `String` des variables pour concaténer une valeur avec une autre. Dans les deux cas, le résultat est affecté à la première variable.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 La valeur de `num1` est maintenant 13 et la valeur de `str1` est maintenant «103».  
  
## <a name="see-also"></a>Voir aussi

- [+, opérateur](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
