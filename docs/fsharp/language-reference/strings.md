---
title: Chaînes
description: "Découvrez comment le type F # 'String’représente du texte immuable comme une séquence de caractères Unicode."
ms.date: 07/05/2019
ms.openlocfilehash: 67a6506b4b8c479da1022c069a7f53402f904b4d
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855411"
---
# <a name="strings"></a>Chaînes

Le `string` type représente du texte immuable sous la forme d’une séquence de caractères Unicode. `string` est un alias de `System.String` dans .NET.

> [!NOTE]
> La référence de l’API docs.microsoft.com pour F # n’est pas terminée. Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="remarks"></a>Notes

Les littéraux de chaîne sont délimités par le caractère guillemet ("). La barre oblique inverse ( \\ ) est utilisée pour encoder certains caractères spéciaux. La barre oblique inverse et le caractère suivant se présentent sous la forme d’une *séquence d’échappement*. Les séquences d’échappement prises en charge dans les littéraux de chaîne F # sont indiquées dans le tableau suivant.

|Caractère|Séquence d'échappement|
|---------|---------------|
|Alerte|`\a`|
|Retour arrière|`\b`|
|Saut de page|`\f`|
|Saut de ligne|`\n`|
|Retour chariot|`\r`|
|Onglet|`\t`|
|Tabulation verticale|`\v`|
|Barre oblique inverse|`\\`|
|Guillemets|`\"`|
|Apostrophe|`\'`|
|Caractère Unicode|`\DDD`(où `D` indique un chiffre décimal ; la plage de 000-255 ; par exemple, `\231` = « ç »)|
|Caractère Unicode|`\xHH`(où `H` indique un chiffre hexadécimal ; la plage de 00 à FF ; par exemple `\xE7` , = "ç")|
|Caractère Unicode|`\uHHHH`(UTF-16) (où `H` indique un chiffre hexadécimal ; plage de 0000-FFFF ;  par exemple, `\u00E7` = "ç")|
|Caractère Unicode|`\U00HHHHHH`(UTF-32) (où `H` indique un chiffre hexadécimal ; plage de 000000-10FFFF ;  par exemple, `\U0001F47D` = " 👽 ")|

> [!IMPORTANT]
> La `\DDD` séquence d’échappement est une notation décimale, et non une notation octale comme dans la plupart des autres langages. Par conséquent, les chiffres `8` et `9` sont valides, et une séquence de `\032` représente un espace (U + 0020), alors que ce même point de code en notation octale serait `\040` .

> [!NOTE]
> Étant donné qu’il est imposé à une plage de 0-255 (0xFF), les `\DDD` `\x` séquences d’échappement et sont en fait le jeu de caractères [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , car cela correspond aux 256 premiers points de code Unicode.

## <a name="verbatim-strings"></a>Chaînes textuelles

S’il est précédé du symbole @, le littéral est une chaîne textuelle. Cela signifie que toutes les séquences d’échappement sont ignorées, sauf que deux caractères guillemets sont interprétés comme un caractère guillemet.

## <a name="triple-quoted-strings"></a>Chaînes entre guillemets triple

En outre, une chaîne peut être placée entre des guillemets triples. Dans ce cas, toutes les séquences d’échappement sont ignorées, y compris les guillemets doubles. Pour spécifier une chaîne qui contient une chaîne entre guillemets incorporée, vous pouvez utiliser une chaîne textuelle ou une chaîne entre guillemets. Si vous utilisez une chaîne textuelle, vous devez spécifier deux guillemets pour indiquer un caractère guillemet simple. Si vous utilisez une chaîne entre guillemets, vous pouvez utiliser les guillemets simples sans qu’ils soient analysés comme la fin de la chaîne. Cette technique peut être utile lorsque vous travaillez avec du code XML ou d’autres structures qui incluent des guillemets incorporés.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des nouvelles lignes, sauf si une barre oblique inverse est le dernier caractère avant le saut de ligne. L’espace blanc de début sur la ligne suivante est ignoré lorsque la barre oblique inverse est utilisée. Le code suivant génère une chaîne `str1` qui a une valeur `"abc\ndef"` et une chaîne `str2` qui a la valeur `"abcdef"` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexation et découpage de chaîne

Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide d’une syntaxe de type tableau, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Le résultat est `b`.

Vous pouvez aussi extraire des sous-chaînes à l’aide de la syntaxe de découpage de tableau, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

La sortie est la suivante.

```console
abc
def
```

Vous pouvez représenter des chaînes ASCII par des tableaux d’octets non signés, de type `byte[]` . Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII. Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’échappement Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Opérateurs de chaîne

L' `+` opérateur peut être utilisé pour concaténer des chaînes, en conservant la compatibilité avec les fonctionnalités de gestion des chaînes de .NET Framework. L’exemple suivant illustre la concaténation de chaînes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String (classe)

Étant donné que le type de chaîne en F # est en fait un type de .NET Framework `System.String` , tous les `System.String` membres sont disponibles. Cela comprend l' `+` opérateur, qui est utilisé pour concaténer des chaînes, la `Length` propriété et la `Chars` propriété, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode. Pour plus d’informations sur les chaînes, consultez `System.String` .

À l’aide `Chars` de la propriété de `System.String` , vous pouvez accéder aux différents caractères d’une chaîne en spécifiant un index, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Module de chaîne

Des fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le `String` module de l' `FSharp.Core` espace de noms. Pour plus d’informations, consultez [module Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
