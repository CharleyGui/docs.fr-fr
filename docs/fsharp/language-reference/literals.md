---
title: Littéraux
description: 'En savoir plus sur les types de littéraux dans le langage de programmation F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559152"
---
# <a name="literals"></a>Littéraux

Cet article fournit un tableau qui montre comment spécifier le type d’un littéral en F #.

## <a name="literal-types"></a>Types de littéral

Le tableau suivant présente les types de littéraux en F #. Les caractères qui représentent des chiffres en notation hexadécimale ne respectent pas la casse ; les caractères qui identifient le type respectent la casse.

|Type|Description|Suffixe ou préfixe|Exemples|
|----|-----------|----------------|--------|
|sbyte|entier 8 bits signé|y|`86y`<br /><br />`0b00000101y`|
|byte|nombre naturel 8 bits non signé|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|entier 16 bits signé|s|`86s`|
|uint16|nombre naturel 16 bits non signé|us|`86us`|
|int<br /><br />int32|entier 32 bits signé|l ou aucun|`86`<br /><br />`86l`|
|uint<br /><br />uint32|nombre naturel non signé 32 bits|u ou UL|`86u`<br /><br />`86ul`|
|nativeint|pointeur natif vers un nombre naturel signé|n|`123n`|
|unativeint|pointeur natif en tant que nombre naturel non signé|ÉCHAPP|`0x00002D3Fun`|
|int64|entier 64 bits signé|L|`86L`|
|uint64|nombre naturel non signé 64 bits|UL|`86UL`|
|unique, float32|nombre à virgule flottante 32 bits|F ou f|`4.14F` ou `4.14f`|
|||chariot|`0x00000000lf`|
|dissocié Cliquer|nombre à virgule flottante 64 bits|aucun|`4.14` ou `2.3E+32` ou `2.3e+32`|
|||CHARIOT|`0x0000000000000000LF`|
|bigint|entier non limité à la représentation 64 bits|I|`9999999999999999999999999999I`|
|Décimal|nombre fractionnaire représenté sous la forme d’un nombre à virgule fixe ou rationnel|M ou m|`0.7833M` ou `0.7833m`|
|Char|Caractère Unicode|aucun|`'a'` ou `'\u0061'`|
|String|chaîne Unicode|aucun|`"text\n"`<br /><br />or<br /><br />`@"c:\filename"`<br /><br />or<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />or<br /><br />`"string1" + "string2"`<br /><br />Voir aussi [chaînes](Strings.md).|
|byte|Caractère ASCII|B|`'a'B`|
|byte[]|Chaîne ASCII|B|`"text"B`|
|String ou Byte []|chaîne textuelle|@ préfixe|`@"\\server\share"` Unicode<br /><br />`@"\\server\share"B` R|

## <a name="named-literals"></a>Littéraux nommés

Les valeurs qui sont destinées à être des constantes peuvent être marquées avec l’attribut [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) . Cet attribut a pour effet de provoquer la compilation d’une valeur en tant que constante.

Dans les expressions de critères spéciaux, les identificateurs qui commencent par des caractères minuscules sont toujours traités comme des variables à lier, plutôt que comme des littéraux. vous devez donc généralement utiliser des majuscules lorsque vous définissez des littéraux.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Notes

Les chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivis d’un code hexadécimal 16 bits (0000-ffff) ou d’encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivis d’un code hexadécimal 32 bits qui représente un point de code Unicode (00000000-0010FFFF).

L’utilisation d’autres opérateurs de bits autres que `|||` n’est pas autorisée.

## <a name="integers-in-other-bases"></a>Entiers dans d’autres bases

Les entiers 32 bits signés peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide d’un `0x` `0o` préfixe, ou, `0b` respectivement.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Traits de soulignement dans les littéraux numériques

Vous pouvez séparer les chiffres par le caractère de soulignement ( `_` ).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
