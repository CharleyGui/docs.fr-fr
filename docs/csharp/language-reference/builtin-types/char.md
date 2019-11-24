---
title: char type - C# reference
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451163"
---
# <a name="char-c-reference"></a>char (C# reference)

The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.

|Tapez|Range|Size|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.

## <a name="literals"></a>Littéraux

You can specify a `char` value with:

- a character literal.
- a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.
- a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.

> [!NOTE]
> In the case of a Unicode escape sequence, you must specify all four hexadecimal digits. That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.
>
> In the case of a hexadecimal escape sequence, you can omit the leading zeros. That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.

## <a name="conversions"></a>Conversions

The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`. It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`. It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.

There are no implicit conversions from other types to the `char` type. However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.

## <a name="c-language-specification"></a>spécification du langage C#

For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Tableaux des types intégrés](../keywords/built-in-types-table.md)
- [Chaînes](../../programming-guide/strings/index.md)
