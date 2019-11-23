---
title: Types de données des résultats d'opérateur
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331467"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Types de données des résultats d'opérateur (Visual Basic)
Visual Basic determines the result data type of an operation based on the data types of the operands. In some cases this might be a data type with a greater range than that of either operand.  
  
## <a name="data-type-ranges"></a>plages de types de données  
 The ranges of the relevant data types, in order from smallest to largest, are as follows:  
  
- [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — two possible values  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 possible integral values  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65,536 (6.5...E+4) possible integral values  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4,294,967,296 (4.2...E+9) possible integral values  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8...E+19) possible integral values  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1.5...E+29 possible integral values, maximum range 7.9...E+28 (absolute value)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) — maximum range 3.4...E+38 (absolute value)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — maximum range 1.7...E+308 (absolute value)  
  
 For more information on Visual Basic data types, see [Data Types](../../../visual-basic/language-reference/data-types/index.md).  
  
 If an operand evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the Visual Basic arithmetic operators treat it as zero.  
  
## <a name="decimal-arithmetic"></a>Decimal Arithmetic  
 Note that the [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type is neither floating-point nor integer.  
  
 If either operand of a `+`, `–`, `*`, `/`, or `Mod` operation is `Decimal` and the other is not `Single` or `Double`, Visual Basic widens the other operand to `Decimal`. It performs the operation in `Decimal`, and the result data type is `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Floating-Point Arithmetic  
 Visual Basic performs most floating-point arithmetic in [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), which is the most efficient data type for such operations. However, if one operand is [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) and the other is not `Double`, Visual Basic performs the operation in `Single`. It widens each operand as necessary to the appropriate data type before the operation, and the result has that data type.  
  
### <a name="-and--operators"></a>/ and ^ Operators  
 The `/` operator is defined only for the [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md), and [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data types. Visual Basic widens each operand as necessary to the appropriate data type before the operation, and the result has that data type.  
  
 The following table shows the result data types for the `/` operator. Note that this table is symmetric; for a given combination of operand data types, the result data type is the same regardless of the order of the operands.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Any integer type|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Any integer type|Decimal|Single|Double|Double|  
  
 The `^` operator is defined only for the `Double` data type. Visual Basic widens each operand as necessary to `Double` before the operation, and the result data type is always `Double`.  
  
## <a name="integer-arithmetic"></a>Integer Arithmetic  
 The result data type of an integer operation depends on the data types of the operands. In general, Visual Basic uses the following policies for determining the result data type:  
  
- If both operands of a binary operator have the same data type, the result has that data type. An exception is `Boolean`, which is forced to `Short`.  
  
- If an unsigned operand participates with a signed operand, the result has a signed type with at least as large a range as either operand.  
  
- Otherwise, the result usually has the larger of the two operand data types.  
  
 Note that the result data type might not be the same as either operand data type.  
  
> [!NOTE]
> The result data type is not always large enough to hold all possible values resulting from the operation. An <xref:System.OverflowException> exception can occur if the value is too large for the result data type.  
  
### <a name="unary--and--operators"></a>Unary + and – Operators  
 The following table shows the result data types for the two unary operators, `+` and `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unary `+`|Courte|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|Unary `–`|Courte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Decimal|  
  
### <a name="-and--operators"></a><\< and >> Operators  
 The following table shows the result data types for the two bit-shift operators, `<<` and `>>`. Visual Basic treats each bit-shift operator as a unary operator on its left operand (the bit pattern to be shifted).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Courte|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
  
 If the left operand is `Decimal`, `Single`, `Double`, or `String`, Visual Basic attempts to convert it to `Long` before the operation, and the result data type is `Long`. The right operand (the number of bit positions to shift) must be `Integer` or a type that widens to `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binary +, –, \*, and Mod Operators  
 The following table shows the result data types for the binary `+` and `–` operators and the `*` and `Mod` operators. Note that this table is symmetric; for a given combination of operand data types, the result data type is the same regardless of the order of the operands.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Decimal|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Decimal|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|Longue|Longue|Decimal|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Longue|Longue|Decimal|  
|`UInteger`|Longue|Longue|UInteger|Longue|UInteger|Longue|UInteger|Longue|ULong|  
|`Long`|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\\, opérateur  
 The following table shows the result data types for the `\` operator. Note that this table is symmetric; for a given combination of operand data types, the result data type is the same regardless of the order of the operands.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Longue|Longue|Longue|  
|`UInteger`|Longue|Longue|UInteger|Longue|UInteger|Longue|UInteger|Longue|ULong|  
|`Long`|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Longue|  
|`ULong`|Longue|Longue|ULong|Longue|ULong|Longue|ULong|Longue|ULong|  
  
 If either operand of the `\` operator is [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md), or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic attempts to convert it to [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) before the operation, and the result data type is `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relational and Bitwise Comparisons  
 The result data type of a relational operation (`=`, `<>`, `<`, `>`, `<=`, `>=`) is always `Boolean`[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md). The same is true for logical operations (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) on `Boolean` operands.  
  
 The result data type of a bitwise logical operation depends on the data types of the operands. Note that `AndAlso` and `OrElse` are defined only for `Boolean`, and Visual Basic converts each operand as necessary to `Boolean` before performing the operation.  
  
### <a name="-----and--operators"></a>=, <>, \<, >, \<=, and >= Operators  
 If both operands are `Boolean`, Visual Basic considers `True` to be less than `False`. If a numeric type is compared with a `String`, Visual Basic attempts to convert the `String` to `Double` before the operation. A `Char` or `Date` operand can be compared only with another operand of the same data type. The result data type is always `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitwise Not Operator  
 The following table shows the result data types for the bitwise `Not` operator.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Booléen|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
  
 If the operand is `Decimal`, `Single`, `Double`, or `String`, Visual Basic attempts to convert it to `Long` before the operation, and the result data type is `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitwise And, Or, and Xor Operators  
 The following table shows the result data types for the bitwise `And`, `Or`, and `Xor` operators. Note that this table is symmetric; for a given combination of operand data types, the result data type is the same regardless of the order of the operands.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Booléen|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|Longue|Longue|Longue|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Longue|Longue|Longue|  
|`UInteger`|Longue|Longue|UInteger|Longue|UInteger|Longue|UInteger|Longue|ULong|  
|`Long`|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Longue|Longue|  
|`ULong`|Longue|Longue|ULong|Longue|ULong|Longue|ULong|Longue|ULong|  
  
 If an operand is `Decimal`, `Single`, `Double`, or `String`, Visual Basic attempts to convert it to `Long` before the operation, and the result data type is the same as if that operand had already been `Long`.  
  
## <a name="miscellaneous-operators"></a>Opérateurs divers  
 The `&` operator is defined only for concatenation of `String` operands. Visual Basic converts each operand as necessary to `String` before the operation, and the result data type is always `String`. For the purposes of the `&` operator, all conversions to `String` are considered to be widening, even if `Option Strict` is `On`.  
  
 The `Is` and `IsNot` operators require both operands to be of a reference type. The `TypeOf`...`Is` expression requires the first operand to be of a reference type and the second operand to be the name of a data type. In all these cases the result data type is `Boolean`.  
  
 The `Like` operator is defined only for pattern matching of `String` operands. Visual Basic attempts to convert each operand as necessary to `String` before the operation. The result data type is always `Boolean`.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs](../../../visual-basic/language-reference/operators/index.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
