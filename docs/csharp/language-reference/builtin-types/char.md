---
title: type d’omble - Référence C
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a07cae6e607bb6cda965240c669c655207632298
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739065"
---
# <a name="char-c-reference"></a>char (référence C)

Le `char` mot clé de type <xref:System.Char?displayProperty=nameWithType> est un alias pour le type de structure .NET qui représente un caractère Unicode UTF-16.

|Type|Plage|Taille|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

La valeur par `char` défaut `\0`du type est, c’est-à-dire, U-0000.

Le type [de chaîne](reference-types.md#the-string-type) représente `char` le texte comme une séquence de valeurs.

## <a name="literals"></a>Littéraux

Vous pouvez `char` spécifier une valeur avec :

- un personnage littéral.
- une séquence d’évasion `\u` Unicode, qui est suivie par la représentation héxadecimale à quatre symboles d’un code de caractère.
- une séquence d’évasion hexadecimal, qui est `\x` suivie par la représentation héxadecimale d’un code de caractère.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Comme l’exemple précédent l’indique, vous pouvez également `char` jeter la valeur d’un code de caractère dans la valeur correspondante.

> [!NOTE]
> Dans le cas d’une séquence d’évasion Unicode, vous devez spécifier les quatre chiffres hexadecimal. C’est-à-dire, `\u006A` est `\u06A` `\u6A` une séquence d’évasion valide, tandis que et ne sont pas valides.
>
> Dans le cas d’une séquence d’évasion hexadecimal, vous pouvez omettre les zéros de premier plan. C’est-à-dire, le `\x006A`, `\x06A`, et `\x6A` les séquences d’évasion sont valides et correspondent au même caractère.

## <a name="conversions"></a>Conversions

Le `char` type est implicitement convertible aux `int`types `uint` `long` [intégrals](integral-numeric-types.md) suivants: `ushort`, , , et `ulong`. Il est également implicitement convertible pour les types numériques `double` [flottants](floating-point-numeric-types.md) intégrés: `float`, , et `decimal`. Il est explicitement `sbyte`convertible `byte`à `short` , , et les types intégrales.

Il n’y a pas de `char` conversions implicites d’autres types à ce type. Cependant, tout type numérique [intégral](integral-numeric-types.md) ou à `char`point [flottant](floating-point-numeric-types.md) est explicitement convertible à .

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [des types intégrales](~/_csharplang/spec/types.md#integral-types) de la [spécification linguistique C.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de valeur](value-types.md)
- [Chaînes](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [Encodage de caractères dans .NET](../../../standard/base-types/character-encoding-introduction.md)
