---
title: /, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 537d8b0c703b59743f1a7c531448118058707645
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331050"
---
# <a name="-operator-visual-basic"></a>/, opérateur (Visual Basic)
Divise deux nombres et retourne un résultat à virgule flottante.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Composants  
 `expression1`  
 Requis. Toute expression numérique.  
  
 `expression2`  
 Requis. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, et `Decimal`.  
  
## <a name="result"></a>Résultat  
 Le résultat est le quotient complet de `expression1` divisé par `expression2`, y compris tout reste.  
  
 L' [opérateur \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retourne le quotient entier, qui supprime le reste.  
  
## <a name="remarks"></a>Notes  
 Le type de données du résultat dépend des types des opérandes. Le tableau suivant montre comment le type de données du résultat est déterminé.  
  
|Types de données des opérandes|Type de données de résultat|  
|------------------------|----------------------|  
|Les deux expressions sont des types de données intégraux ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Une expression est un type de données [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) et l’autre n’est pas un [double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Une expression est un type de données [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) et l’autre n’est pas un [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) ou un [double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|L’une des expressions est un type de données [double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
  
 Avant l’exécution de la Division, toutes les expressions numériques entières sont élargies à `Double`. Si vous assignez le résultat à un type de données intégral, Visual Basic tente de convertir le résultat de `Double` en ce type. Cela peut lever une exception si le résultat ne tient pas dans ce type. En particulier, consultez « tentative de division par zéro » dans cette page d’aide.  
  
 Si `expression1` ou `expression2` a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), il est traité comme zéro.  
  
## <a name="attempted-division-by-zero"></a>Division par zéro  
 Si `expression2` a la valeur zéro, l’opérateur `/` se comporte différemment pour les différents types de données d’opérande. Le tableau suivant présente les comportements possibles.  
  
|Types de données des opérandes|Comportement si `expression2` est égal à zéro|  
|------------------------|---------------------------------------|  
|Virgule flottante (`Single` ou `Double`)|Retourne l’infini (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>) ou <xref:System.Double.NaN> (pas un nombre) si `expression1` est également égal à zéro|  
|`Decimal`|Lève <xref:System.DivideByZeroException>|  
|Intégral (signé ou non signé)|La tentative de conversion en type intégral lève <xref:System.OverflowException>, car les types intégraux ne peuvent pas accepter <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>ou <xref:System.Double.NaN>|  
  
> [!NOTE]
> L’opérateur `/` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’opérateur `/` pour effectuer une division à virgule flottante. Le résultat est le quotient des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Les expressions de l’exemple précédent renvoient les valeurs 2,5 et 3,333333. Notez que le résultat est toujours à virgule flottante (`Double`), même si les deux opérandes sont des constantes entières.  
  
## <a name="see-also"></a>Voir aussi

- [/=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
