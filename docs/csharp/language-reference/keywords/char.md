---
title: Char, mot C# clé-référence
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771797"
---
# <a name="char-c-reference"></a>Char (C# référence)

Le mot clé `char` type est un alias pour le type de structure .NET <xref:System.Char?displayProperty=nameWithType> qui représente un caractère Unicode UTF-16 :

|Tapez|Range|Size|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Littéraux

Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode. Vous pouvez également convertir un code de caractère intégral en valeur `char` correspondante. Dans l’exemple suivant, les quatre éléments d’un tableau de `char` sont initialisés avec le même `X` de caractères :

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Conversions

Le type de `char` est implicitement convertible en types [intégraux](../builtin-types/integral-numeric-types.md) suivants : `ushort`, `int`, `uint`, `long` et `ulong`. Il est également implicitement convertible en types numériques à [virgule flottante](../builtin-types/floating-point-numeric-types.md) intégrés : `float`, `double` et `decimal`. Elle est explicitement convertible en `sbyte`, `byte` et `short` types intégraux.

Il n’existe pas de conversion implicite d’autres types en type `char`. Toutefois, tout type numérique [intégral](../builtin-types/integral-numeric-types.md) ou à [virgule flottante](../builtin-types/floating-point-numeric-types.md) est explicitement convertible en `char`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Mots clés C#](./index.md)
- [Tableaux des types intégrés](./built-in-types-table.md)
- [Chaînes](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
