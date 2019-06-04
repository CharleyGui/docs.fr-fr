---
title: Littéraux
description: En savoir plus sur les types de littéraux dans le F# langage de programmation.
ms.date: 02/08/2019
ms.openlocfilehash: 032bc82d222cd34e7ac62e42ee4394c97d975b2e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490974"
---
# <a name="literals"></a>Littéraux

> [!NOTE]
> Les liens de référence des API dans cet article vous dirigera vers MSDN (pour l’instant).

Cette rubrique fournit une table qui montre comment spécifier le type d’un littéral dans F#.

## <a name="literal-types"></a>Types de littéral

Le tableau suivant présente les types de littéraux dans F#. Les caractères qui représentent des chiffres en notation hexadécimale ne sont pas la casse ; les caractères qui identifient le type respectent la casse.

|Type|Description|Suffixe ou préfixe|Exemples|
|----|-----------|----------------|--------|
|sbyte|entier signé 8 bits|o|`86y`<br /><br />`0b00000101y`|
|byte|nombre de naturel 8 bits non signé|UY|`86uy`<br /><br />`0b00000101uy`|
|int16|entier signé 16 bits|s|`86s`|
|uint16|nombre de naturel non signé 16 bits|us|`86us`|
|int<br /><br />int32|entier signé 32 bits|« l » ou none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|nombre de naturel non signé 32 bits|u ou ul|`86u`<br /><br />`86ul`|
|nativeint|pointeur natif à un nombre naturel signé|n|`123n`|
|unativeint|pointeur natif sous forme de nombre naturel non signé|Annuler|`0x00002D3Fun`|
|int64|entier signé 64 bits|L|`86L`|
|uint64|nombre de naturel non signé 64 bits|UL|`86UL`|
|single, float32|nombre à virgule flottante 32 bits|F ou f|`4.14F` ou `4.14f`|
|||LF|`0x00000000lf`|
|type float ; Double|nombre à virgule flottante 64 bits|none|`4.14` ou `2.3E+32` ou `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|entier non limité à la représentation 64 bits|I|`9999999999999999999999999999I`|
|decimal|nombre fractionnaire représenté sous la forme à virgule fixe ou un nombre rationnel|M ou m|`0.7833M` ou `0.7833m`|
|Char|caractère Unicode|none|`'a'`|
|Chaîne|chaîne Unicode|none|`"text\n"`<br /><br />ou<br /><br />`@"c:\filename"`<br /><br />ou<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />ou<br /><br />`"string1" + "string2"`<br /><br />Voir aussi [chaînes](Strings.md).|
|byte|Caractère ASCII|B|`'a'B`|
|byte[]|Chaîne ASCII|B|`"text"B`|
|String ou byte]|chaîne textuelle|@ prefix|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Notes

Chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivi d’un code hexadécimal 16 bits ou les encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivie d’un code hexadécimal 32 bits qui représente un Unicode paire de substitution.

En tant que de F# 3.1, vous pouvez utiliser la `+` vous connecter pour combiner des littéraux de chaîne. Vous pouvez également utiliser l’opérateur de bits ou (`|||`) opérateur pour combiner les indicateurs d’énumération. Par exemple, le code suivant est autorisé dans F# 3.1 :

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

L’utilisation d’autres opérateurs au niveau du bit n’est pas autorisée.

## <a name="named-literals"></a>Littéraux nommés

Les valeurs qui sont destinées à être des constantes peuvent être marquées avec le [littéral](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribut. Cet attribut a pour effet de provoquer une valeur doit être compilé en tant que constante.

Dans les expressions de critères spéciaux, les identificateurs qui commencent par les caractères minuscules sont toujours traités en tant que variables à lier, plutôt que comme des littéraux, par conséquent, vous devez généralement utiliser majuscules lorsque vous définissez des littéraux.

## <a name="integers-in-other-bases"></a>Nombres entiers dans d’autres Bases

Entiers signés de 32 bits peuvent également être spécifiés dans hexadécimal, octal ou binaire à l’aide un `0x`, `0o` ou `0b` respectivement de préfixe.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Traits de soulignement dans les littéraux numériques

En commençant par F# 4.1, vous pouvez séparer les chiffres par le caractère de soulignement (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Voir aussi

- [Core.LiteralAttribute, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
