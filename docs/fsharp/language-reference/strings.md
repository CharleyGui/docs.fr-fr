---
title: Chaînes
description: Découvrez comment la F# type 'string' représente le texte immuable sous la forme d’une séquence de caractères Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610165"
---
# <a name="strings"></a>Chaînes

> [!NOTE]
> Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Le `string` type représente le texte immuable sous la forme d’une séquence de caractères Unicode. `string` est un alias pour `System.String` dans le .NET Framework.

## <a name="remarks"></a>Notes

Littéraux de chaîne sont délimitées par le caractère guillemet ("). Le caractère barre oblique inverse ( \\ ) est utilisé pour encoder certains caractères spéciaux. La barre oblique inverse et le caractère suivant forment sont appelés une *séquence d’échappement*. Prise en charge dans des séquences d’échappement F# littéraux de chaîne sont affichées dans le tableau suivant.

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
|Guillemet|`\"`|
|Apostrophe|`\'`|
|caractère Unicode|`\DDD` (où `D` indique un nombre décimal à chiffres ; la plage de 000 - 255 ; par exemple, `\231` = « ç »)|
|caractère Unicode|`\xHH` (où `H` indique un chiffre hexadécimal ; la plage 00 - FF ; par exemple, `\xE7` = « ç »)|
|caractère Unicode|`\uHHHH` (UTF-16) (où `H` indique un chiffre hexadécimal ; plage 0000 - FFFF ;  par exemple, `\u00E7` = « ç »)|
|caractère Unicode|`\U00HHHHHH` (UTF-32) (où `H` indique un chiffre hexadécimal ; plage 000000 - 10FFFF ;  par exemple, `\U0001F47D` = «👽»)|

> [!IMPORTANT]
> Le `\DDD` séquence d’échappement est la notation décimale, notation octale pas comme dans la plupart des autres langages. Par conséquent, les chiffres `8` et `9` sont valides et une séquence de `\032` représente un espace (U + 0020), alors que ce même point de code en notation octale serait `\040`.

> [!NOTE]
> Limitée à une plage de 0 - 255 (0xFF), le `\DDD` et `\x` sont effectivement des séquences d’échappement le [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) jeu, de caractères dans la mesure où les 256 premiers points de code Unicode correspondant.

Si précédé par le symbole @, le littéral est une chaîne textuelle. Cela signifie que les séquences d’échappement sont ignorés, sauf que deux caractères de guillemet sont interprétés comme un seul guillemet.

En outre, une chaîne peut être placé entre guillemets triples. Dans ce cas, toutes les séquences d’échappement sont ignorés, y compris les caractères de guillemet double. Pour spécifier une chaîne qui contient un élément incorporé chaîne entre guillemets, vous pouvez utiliser une chaîne textuelle ou une chaîne entre guillemets de triple. Si vous utilisez une chaîne textuelle, vous devez spécifier deux caractères de guillemet pour indiquer un caractère de guillemet. Si vous utilisez une chaîne entre guillemets de triple, vous pouvez utiliser les caractères guillemet-apostrophe sans eux analysé en tant que la fin de la chaîne. Cette technique peut être utile lorsque vous travaillez avec XML ou d’autres structures qui incluent les guillemets incorporés.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des sauts de ligne, sauf si un caractère de barre oblique inverse est le dernier caractère avant le saut de ligne. Espace blanc de début sur la ligne suivante est ignoré lorsque le caractère barre oblique inverse est utilisé. Le code suivant produit une chaîne `str1` qui a la valeur `"abc\ndef"` et une chaîne `str2` qui a la valeur `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide de syntaxe de type tableau, comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Le résultat est `b`.

Ou vous pouvez extraire des sous-chaînes à l’aide de syntaxe de découpage de tableau, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

La sortie est la suivante.

```
abc
def
```

Vous pouvez représenter les chaînes ASCII par des tableaux d’octets non signés, type `byte[]`. Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII. Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prend en charge les mêmes séquences d’échappement sous forme de chaînes Unicode à l’exception des séquences d’échappement Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Opérateurs de chaîne

Il existe deux façons de concaténer des chaînes : à l’aide de la `+` opérateur ou à l’aide de la `^` opérateur. Le `+` opérateur assure la compatibilité avec la chaîne de .NET Framework gère les fonctionnalités.

L’exemple suivant illustre la concaténation de chaînes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe de chaîne

Parce que la chaîne de type dans F# est en fait un .NET Framework `System.String` taper, tout le `System.String` membres sont disponibles. Cela inclut la `+` opérateur, qui est utilisé pour concaténer des chaînes, la `Length` propriété et le `Chars` propriété, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode. Pour plus d’informations sur les chaînes, consultez `System.String`.

À l’aide de la `Chars` propriété du `System.String`, vous pouvez accéder à différents caractères dans une chaîne en spécifiant un index, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Module de chaîne

Des fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le `String` module dans le `FSharp.Core` espace de noms. Pour plus d’informations, consultez [Core.String, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
