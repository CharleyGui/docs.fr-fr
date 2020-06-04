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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409315"
---
# <a name="-operator-visual-basic"></a>*, opérateur (Visual Basic)
Multiplie deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`number1`|Obligatoire. Toute expression numérique.|  
|`number2`|Obligatoire. Toute expression numérique.|  
  
## <a name="result"></a>Résultats  
 Le résultat est le produit de `number1` et `number2` .  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types à virgule flottante non signée et `Decimal` .  
  
## <a name="remarks"></a>Notes  
 Le type de données du résultat dépend des types des opérandes. Le tableau suivant montre comment le type de données du résultat est déterminé.  
  
|Types de données des opérandes|Type de données de résultat|  
|---|---|  
|Les deux expressions sont des types de données intégraux ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))|Type de données numérique approprié pour les types de données de `number1` et `number2` . Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).|  
|Les deux expressions sont [décimales](../data-types/decimal-data-type.md)|`Decimal`|  
|Les deux expressions sont [uniques](../data-types/single-data-type.md)|`Single`|  
|L’une des expressions est un type de données à virgule flottante ( `Single` ou [double](../data-types/double-data-type.md)), mais pas les deux `Single` (Notez qu' `Decimal` il ne s’agit pas d’un type de données à virgule flottante)|`Double`|  
  
 Si une expression prend la valeur [Nothing](../nothing.md), elle est considérée comme égale à zéro.  
  
## <a name="overloading"></a>Surcharge  
 L' `*` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l' `*` opérateur pour multiplier deux nombres. Le résultat est le produit des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [* = (Opérateur)](multiplication-assignment-operator.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
