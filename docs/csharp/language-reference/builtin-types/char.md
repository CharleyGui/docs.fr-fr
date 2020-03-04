---
title: type de caractère C# -référence
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a5aca12e4037d517c3bcfb403c990605a052d48f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239844"
---
# <a name="char-c-reference"></a>Char (C# référence)

Le mot clé `char` type est un alias pour le type de structure .NET <xref:System.Char?displayProperty=nameWithType> qui représente un caractère Unicode UTF-16.

|Type|Plage|Taille|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

La valeur par défaut du type de `char` est `\0`, c’est-à-dire U + 0000.

Le type [String](reference-types.md#the-string-type) représente du texte sous la forme d’une séquence de valeurs `char`.

## <a name="literals"></a>Littéraux

Vous pouvez spécifier une valeur de `char` avec :

- littéral de caractère.
- séquence d’échappement Unicode, `\u` suivie de la représentation hexadécimale à quatre symboles d’un code de caractère.
- séquence d’échappement hexadécimale, `\x` suivie de la représentation hexadécimale d’un code de caractère.

[!code-csharp-interactive[char literals](~/samples/snippets/csharp/language-reference/builtin-types/CharType.cs#Literals)]

Comme le montre l’exemple précédent, vous pouvez également effectuer un cast de la valeur d’un code de caractère dans la valeur `char` correspondante.

> [!NOTE]
> Dans le cas d’une séquence d’échappement Unicode, vous devez spécifier les quatre chiffres hexadécimaux. Autrement dit, `\u006A` est une séquence d’échappement valide, tandis que `\u06A` et `\u6A` ne sont pas valides.
>
> Dans le cas d’une séquence d’échappement hexadécimale, vous pouvez omettre les zéros non significatifs. Autrement dit, les séquences d’échappement `\x006A`, `\x06A`et `\x6A` sont valides et correspondent au même caractère.

## <a name="conversions"></a>Conversions

Le type de `char` est implicitement convertible en types [intégraux](integral-numeric-types.md) suivants : `ushort`, `int`, `uint`, `long`et `ulong`. Il est également implicitement convertible en types numériques à [virgule flottante](floating-point-numeric-types.md) intégrés : `float`, `double`et `decimal`. Elle est explicitement convertible en `sbyte`, `byte`et `short` types intégraux.

Il n’existe pas de conversion implicite d’autres types en type `char`. Toutefois, tout type numérique [intégral](integral-numeric-types.md) ou à [virgule flottante](floating-point-numeric-types.md) est explicitement convertible en `char`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [Chaînes](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
