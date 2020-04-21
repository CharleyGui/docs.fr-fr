---
title: Chaînes
description: Découvrez comment le type de « corde » Fmd représente le texte immuable comme une séquence de caractères Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739570"
---
# <a name="strings"></a>Chaînes

> [!NOTE]
> Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Le `string` type représente le texte immuable comme une séquence de caractères Unicode. `string` est un alias pour `System.String` dans le .NET Framework.

## <a name="remarks"></a>Notes

Les littérals de cordes sont délimités par le caractère de la marque de citation («) Le personnage de \\ barre oblique inverse ( ) est utilisé pour coder certains caractères spéciaux. La barre oblique inverse et le personnage suivant ensemble sont connus comme une *séquence d’évasion*. Les séquences d’évasion prises en charge dans les littérals de cordes F sont montrées dans le tableau suivant.

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
|Caractère Unicode|`\DDD`(où `D` indique un chiffre décimal; gamme de 000 `\231` - 255; par exemple, "ç")|
|Caractère Unicode|`\xHH`(où `H` indique un chiffre hexadecimal; gamme de 00 - FF; par exemple, `\xE7` "ç")|
|Caractère Unicode|`\uHHHH`(UTF-16) (où `H` indique un chiffre hexadecimal; gamme de 0000 - FFFF;  par exemple, `\u00E7` "ç")|
|Caractère Unicode|`\U00HHHHHH`(UTF-32) (où `H` indique un chiffre hexadecimal; gamme de 0000000 - 10FFFF;  par exemple, `\U0001F47D` 👽" ")|

> [!IMPORTANT]
> La `\DDD` séquence d’évasion est une notation décimale, et non une notation octotale comme dans la plupart des autres langues. Par conséquent, `8` `9` les chiffres et sont `\032` valides, et une séquence de représente un espace (U-0020), tandis que ce même point de code dans la notation octale serait `\040`.

> [!NOTE]
> Étant limité à une gamme de 0 - 255 `\DDD` `\x` (0xFF), les séquences et d’évasion sont effectivement l’ENSEMBLE de caractères [ISO-8859-1,](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) puisque cela correspond aux 256 premiers points de code Unicode.

## <a name="verbatim-strings"></a>Cordes Verbatim

Si précédé par le symbole, le littéral est une chaîne textuelle. Cela signifie que toutes les séquences d’évasion sont ignorées, sauf que deux personnages de guillemets sont interprétés comme un personnage de marque de citation.

## <a name="triple-quoted-strings"></a>Triples cordes citées

En outre, une chaîne peut être entourée de citations triples. Dans ce cas, toutes les séquences d’évasion sont ignorées, y compris les caractères de double guillemets. Pour spécifier une chaîne qui contient une chaîne citée intégrée, vous pouvez soit utiliser une chaîne textuelle ou une chaîne à trois points. Si vous utilisez une chaîne textuelle, vous devez spécifier deux caractères de guillemets pour indiquer un seul caractère de marque de citation. Si vous utilisez une chaîne à trois citations, vous pouvez utiliser les caractères de la marque de citation unique sans qu’ils soient analysés comme la fin de la chaîne. Cette technique peut être utile lorsque vous travaillez avec XML ou d’autres structures qui incluent des guillemets intégrés.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des lignes neuves, à moins qu’un personnage de barre oblique inverse soit le dernier personnage avant la rupture de la ligne. L’espace blanc de tête sur la ligne suivante est ignoré lorsque le caractère de barre oblique inverse est utilisé. Le code suivant `str1` produit une `"abc\ndef"` chaîne `str2` qui a `"abcdef"`de la valeur et une chaîne qui a de la valeur .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexation et découpe des cordes

Vous pouvez accéder à des caractères individuels dans une chaîne en utilisant la syntaxe en forme de tableau, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Le résultat est `b`.

Ou vous pouvez extraire des sous-cordes en utilisant la syntaxe de tranche de tableau, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

La sortie est la suivante.

```console
abc
def
```

Vous pouvez représenter les chaînes ASCII par des tableaux `byte[]`d’octets non signés, type . Vous ajoutez le `B` suffixe à une chaîne littérale pour indiquer qu’il s’agit d’une chaîne ASCII. Les littérals de cordes ASCII utilisés avec les tableaux byte prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’évasion Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Opérateurs de cordes

L’opérateur `+` peut être utilisé pour concatenate des chaînes, en maintenant la compatibilité avec les caractéristiques de manipulation de chaîne .NET Framework. L’exemple suivant illustre la concatenation des cordes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe de cordes

Étant donné que le type de chaîne `System.String` en F `System.String` est en fait un type cadre .NET, tous les membres sont disponibles. Cela comprend `+` l’opérateur, qui est utilisé pour `Length` concatenate `Chars` cordes, la propriété, et la propriété, qui retourne la chaîne comme un tableau de caractères Unicode. Pour plus d’informations `System.String`sur les chaînes, voir .

En utilisant `Chars` la `System.String`propriété de , vous pouvez accéder aux caractères individuels dans une chaîne en spécifiant un index, comme il est indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Module de chaîne

D’autres fonctionnalités pour la `String` manipulation `FSharp.Core` des chaînes sont incluses dans le module dans l’espace nom. Pour plus d’informations, voir [Module Core.String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
