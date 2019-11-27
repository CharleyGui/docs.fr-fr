---
title: '* Opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4f6a8ea2c5f4e23791afdfe98d2a08bf67219048
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348362"
---
# <a name="-operator-visual-basic"></a>*, opérateur (Visual Basic)
Multiplie deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`number1`|Requis. Toute expression numérique.|  
|`number2`|Requis. Toute expression numérique.|  
  
## <a name="result"></a>Résultat  
 Le résultat est le produit de `number1` et `number2`.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, et `Decimal`.  
  
## <a name="remarks"></a>Notes  
 Le type de données du résultat dépend des types des opérandes. Le tableau suivant montre comment le type de données du résultat est déterminé.  
  
|Types de données des opérandes|Type de données de résultat|  
|---|---|  
|Les deux expressions sont des types de données intégraux ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Type de données numérique approprié pour les types de données de `number1` et `number2`. Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Les deux expressions sont [décimales](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Les deux expressions sont [uniques](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|L’une des expressions est un type de données à virgule flottante (`Single` ou [double](../../../visual-basic/language-reference/data-types/double-data-type.md)), mais pas les deux `Single` (Notez `Decimal` n’est pas un type de données à virgule flottante)|`Double`|  
  
 Si une expression prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), elle est considérée comme égale à zéro.  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `*` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’opérateur `*` pour multiplier deux nombres. Le résultat est le produit des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [*=, opérateur](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
