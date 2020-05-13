---
title: type char-référence C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205777"
---
# <a name="char-c-reference"></a>Char (référence C#)

Le `char` mot clé type est un alias pour le <xref:System.Char?displayProperty=nameWithType> type de structure .net qui représente un caractère Unicode UTF-16.

|Type|Plage|Taille|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

La valeur par défaut du `char` type est `\0` , c’est-à-dire U + 0000.

Le `char` type prend en charge les opérateurs de [comparaison](../operators/comparison-operators.md), d' [égalité](../operators/equality-operators.md), d' [incrémentation](../operators/arithmetic-operators.md#increment-operator-)et de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) . En outre, pour les `char` opérandes, les opérateurs [logiques](../operators/bitwise-and-shift-operators.md) [arithmétiques](../operators/arithmetic-operators.md) et au niveau du bit effectuent une opération sur les codes de caractères correspondants et produisent le résultat du `int` type.

Le type [String](reference-types.md#the-string-type) représente du texte sous la forme d’une séquence de `char` valeurs.

## <a name="literals"></a>Littéraux

Vous pouvez spécifier une `char` valeur avec :

- littéral de caractère.
- séquence d’échappement Unicode, suivie de `\u` la représentation hexadécimale à quatre symboles d’un code de caractère.
- séquence d’échappement hexadécimale, `\x` suivie de la représentation hexadécimale d’un code de caractère.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Comme le montre l’exemple précédent, vous pouvez également effectuer un cast de la valeur d’un code de caractère dans la `char` valeur correspondante.

> [!NOTE]
> Dans le cas d’une séquence d’échappement Unicode, vous devez spécifier les quatre chiffres hexadécimaux. Autrement dit, `\u006A` est une séquence d’échappement valide, tandis que `\u06A` et `\u6A` ne sont pas valides.
>
> Dans le cas d’une séquence d’échappement hexadécimale, vous pouvez omettre les zéros non significatifs. Autrement dit, les `\x006A` `\x06A` `\x6A` séquences d’échappement, et sont valides et correspondent au même caractère.

## <a name="conversions"></a>Conversions

Le `char` type est implicitement convertible en types [intégraux](integral-numeric-types.md) suivants : `ushort` , `int` , `uint` , `long` et `ulong` . Il est également implicitement convertible en types numériques à [virgule flottante](floating-point-numeric-types.md) intégrés : `float` , `double` et `decimal` . Il est explicitement convertible en `sbyte` `byte` types, et en `short` types intégraux.

Il n’existe pas de conversion implicite d’autres types vers le `char` type. Toutefois, tous les types numériques [intégraux](integral-numeric-types.md) ou à [virgule flottante](floating-point-numeric-types.md) sont explicitement convertibles en `char` .

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de valeur](value-types.md)
- [Chaînes](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [Encodage de caractères dans .NET](../../../standard/base-types/character-encoding-introduction.md)
