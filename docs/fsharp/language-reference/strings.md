---
title: Chaînes
description: Découvrez comment le F# type’String’représente du texte immuable comme une séquence de caractères Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452816"
---
# <a name="strings"></a>Chaînes

> [!NOTE]
> Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Le type de `string` représente du texte immuable sous la forme d’une séquence de caractères Unicode. `string` est un alias pour `System.String` dans le .NET Framework.

## <a name="remarks"></a>Notes

Les littéraux de chaîne sont délimités par le caractère guillemet ("). La barre oblique inverse (\\) est utilisée pour encoder certains caractères spéciaux. La barre oblique inverse et le caractère suivant se présentent sous la forme d’une *séquence d’échappement*. Les séquences d’échappement F# prises en charge dans les littéraux de chaîne sont indiquées dans le tableau suivant.

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
|Caractère|`\'`|
|Caractère Unicode|`\DDD` (où `D` indique un chiffre décimal ; la plage de 000-255 ; par exemple, `\231` = "ç")|
|Caractère Unicode|`\xHH` (où `H` indique un chiffre hexadécimal ; la plage de 00 à FF ; par exemple, `\xE7` = "ç")|
|Caractère Unicode|`\uHHHH` (UTF-16) (où `H` indique un chiffre hexadécimal ; plage de 0000-FFFF ;  par exemple, `\u00E7` = "ç")|
|Caractère Unicode|`\U00HHHHHH` (UTF-32) (où `H` indique un chiffre hexadécimal ; plage de 000000-10FFFF ;  par exemple, `\U0001F47D` = «👽»)|

> [!IMPORTANT]
> La séquence d’échappement `\DDD` est une notation décimale, et non une notation octale comme dans la plupart des autres langages. Par conséquent, les chiffres `8` et `9` sont valides, et une séquence de `\032` représente un espace (U + 0020), tandis que le même point de code en notation octale est `\040`.

> [!NOTE]
> Étant contraints à une plage de 0-255 (0xFF), les séquences d’échappement `\DDD` et `\x` sont en fait le jeu de caractères [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , car cela correspond aux 256 premiers points de code Unicode.

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

Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des nouvelles lignes, sauf si une barre oblique inverse est le dernier caractère avant le saut de ligne. L’espace blanc de début sur la ligne suivante est ignoré lorsque la barre oblique inverse est utilisée. Le code suivant produit une `str1` de chaîne qui a la valeur `"abc\ndef"` et une chaîne `str2` qui a une valeur `"abcdef"`.

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

Vous pouvez représenter des chaînes ASCII par des tableaux d’octets non signés, `byte[]`de type. Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII. Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’échappement Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Opérateurs de chaîne

Il existe deux façons de concaténer des chaînes : à l’aide de l’opérateur `+` ou à l’aide de l’opérateur `^`. L’opérateur `+` maintient la compatibilité avec les fonctionnalités de gestion des chaînes .NET Framework.

L’exemple suivant illustre la concaténation de chaînes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String (classe)

Étant donné que le type F# de chaîne dans est en fait un type de `System.String` .NET Framework, tous les membres de `System.String` sont disponibles. Cela comprend l’opérateur `+`, qui est utilisé pour concaténer des chaînes, la propriété `Length` et la propriété `Chars`, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode. Pour plus d’informations sur les chaînes, consultez `System.String`.

À l’aide de la propriété `Chars` de `System.String`, vous pouvez accéder aux différents caractères d’une chaîne en spécifiant un index, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Module de chaîne

Des fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le module `String` de l’espace de noms `FSharp.Core`. Pour plus d’informations, consultez [module Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
