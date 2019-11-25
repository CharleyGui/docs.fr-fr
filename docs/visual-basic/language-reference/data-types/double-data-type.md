---
title: Double, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344016"
---
# <a name="double-data-type-visual-basic"></a>Double, type de données (Visual Basic)

Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values. Double-precision numbers store an approximation of a real number.

## <a name="remarks"></a>Notes

The `Double` data type provides the largest and smallest possible magnitudes for a number.

La valeur par défaut de `Double` est 0.

## <a name="programming-tips"></a>Conseils de programmation

- **Precision.** When you work with floating-point numbers, remember that they do not always have a precise representation in memory. This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator. For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Trailing Zeros.** The floating-point data types do not have any internal representation of trailing zero characters. For example, they do not distinguish between 4.2000 and 4.2. Consequently, trailing zero characters do not appear when you display or print floating-point values.

- **Type Characters.** L'ajout du caractère de type littéral `R` à un littéral force ce dernier en type de données `Double`. For example, if an integer value is followed by `R`, the value is changed to a `Double`.

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  L'ajout du caractère de type identificateur `#` à un identificateur force ce dernier en type `Double`. In the following example, the variable `num` is typed as a `Double`:

  ```vb
  Dim num# = 3
  ```

- **Framework Type.** Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Double?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single (type de données)](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
