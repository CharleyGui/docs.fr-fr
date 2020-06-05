---
title: Opérateurs de concaténation
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388788"
---
# <a name="concatenation-operators-in-visual-basic"></a>Opérateurs de concaténation (Visual Basic)

Les opérateurs de concaténation joignent plusieurs chaînes en une seule. Il existe deux opérateurs de concaténation, `+` et `&`. Les deux effectuent l'opération de concaténation de base, comme le montre l'exemple suivant.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Ces opérateurs peuvent également concaténer les variables `String`, comme illustré ici.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Différences entre ces deux opérateurs de concaténation

L' [opérateur +](../../../language-reference/operators/addition-operator.md) a l’objectif principal d’ajouter deux nombres. Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne. L'opérateur `+` comporte un ensemble complexe de règles qui déterminent s'il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exception <xref:System.InvalidCastException> d'exécution.

L' [opérateur&](../../../language-reference/operators/concatenation-operator.md) est défini uniquement pour les `String` opérandes, et il élargit toujours ses opérandes à `String` , quel que soit le paramètre de `Option Strict` . L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.

## <a name="performance-string-and-stringbuilder"></a>Performance : String et StringBuilder

Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, suppressions et remplacements, vos performances peuvent s'améliorer avec la classe <xref:System.Text.StringBuilder> de l'espace de noms <xref:System.Text>. Elle prend une instruction supplémentaire pour créer et initialiser un objet <xref:System.Text.StringBuilder>, et une autre instruction pour convertir sa valeur finale en une `String`, mais vous pouvez rattraper le retard induit car <xref:System.Text.StringBuilder> peut s'exécuter plus rapidement.

## <a name="see-also"></a>Voir aussi

- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
- [Types de méthodes de manipulation de chaînes en Visual Basic](../strings/types-of-string-manipulation-methods.md)
- [Opérateurs arithmétiques en Visual Basic](arithmetic-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](logical-and-bitwise-operators.md)
