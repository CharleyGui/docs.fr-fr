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
ms.openlocfilehash: f86245c649647be4e040a61083d8b93eee4d7422
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353687"
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

L' [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md) a l’objectif principal d’ajouter deux nombres. Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne. L'opérateur `+` comporte un ensemble complexe de règles qui déterminent s'il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exception <xref:System.InvalidCastException> d'exécution.

L' [opérateur &](../../../../visual-basic/language-reference/operators/concatenation-operator.md) est défini uniquement pour les opérandes `String`, et élargit toujours ses opérandes à `String`, quel que soit le paramètre de `Option Strict`. L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.

## <a name="performance-string-and-stringbuilder"></a>Performance : String et StringBuilder

Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, suppressions et remplacements, vos performances peuvent s'améliorer avec la classe <xref:System.Text.StringBuilder> de l'espace de noms <xref:System.Text>. Elle prend une instruction supplémentaire pour créer et initialiser un objet <xref:System.Text.StringBuilder>, et une autre instruction pour convertir sa valeur finale en une `String`, mais vous pouvez rattraper le retard induit car <xref:System.Text.StringBuilder> peut s'exécuter plus rapidement.

## <a name="see-also"></a>Voir aussi

- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Types de méthodes de manipulation de chaînes dans Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Opérateurs de comparaison dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
