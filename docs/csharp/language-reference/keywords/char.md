---
title: char, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698774"
---
# <a name="char-c-reference"></a>char (référence C#)

Le mot clé `char` permet de déclarer une instance de la structure <xref:System.Char?displayProperty=nameWithType> utilisée par le .NET Framework pour représenter un caractère Unicode. La valeur d’un objet `Char` est une valeur numérique 16 bits (ordinale).

 Les caractères Unicode sont utilisés pour représenter la plupart des langues écrites dans le monde.

|Type|Plage|Size|Type .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 à U+FFFF|Caractère Unicode 16 bits|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Littéraux

Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode. Vous pouvez également effectuer un cast des codes de caractères de type intégral. Dans l’exemple suivant, les quatre éléments d’un tableau de `char` sont initialisés avec le même caractère `X` :

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Conversions

Vous pouvez convertir implicitement un `char` en [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md) ou [decimal](../builtin-types/floating-point-numeric-types.md). Par contre, vous ne pouvez pas convertir implicitement d’autres types en type `char`.

Le type <xref:System.Char?displayProperty=nameWithType> fournit plusieurs méthodes statiques à utiliser avec des valeurs `char`.

## <a name="c-language-specification"></a>spécification du langage C#  

Pour plus d’informations, consultez [Types intégraux](~/_csharplang/spec/types.md#integral-types) dans la [spécification du langage C#](../language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- <xref:System.Char>
- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Types intégraux](../builtin-types/integral-numeric-types.md)
- [Tableau des types intégrés](./built-in-types-table.md)
- [Tableau des conversions numériques implicites](./implicit-numeric-conversions-table.md)
- [Tableau des conversions numériques explicites](./explicit-numeric-conversions-table.md)
- [Chaînes](../../programming-guide/strings/index.md)
