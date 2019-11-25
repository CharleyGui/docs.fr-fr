---
title: Single, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343919"
---
# <a name="single-data-type-visual-basic"></a>Single, type de données (Visual Basic)

Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values. Single-precision numbers store an approximation of a real number.  
  
## <a name="remarks"></a>Notes  

 Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`. In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.  
  
 La valeur par défaut de `Single` est 0.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Precision.** When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory. This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator. For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Widening.** The `Single` data type widens to `Double`. This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.  
  
- **Trailing Zeros.** The floating-point data types do not have any internal representation of trailing 0 characters. For example, they do not distinguish between 4.2000 and 4.2. Consequently, trailing 0 characters do not appear when you display or print floating-point values.  
  
- **Type Characters.** L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`. L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.  
  
- **Framework Type.** Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Single?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double (type de données)](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
