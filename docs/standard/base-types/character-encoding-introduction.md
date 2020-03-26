---
title: Introduction à l’encodage de caractère dans .NET
description: Découvrez plus en détail l’encodage et le décodage de caractères dans .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134442"
---
# <a name="character-encoding-in-net"></a>Encodage de caractères dans .NET

Cet article fournit une introduction aux systèmes d’encodage de caractère qui sont utilisés par .NET. L’article explique <xref:System.String> <xref:System.Char>comment <xref:System.Text.Rune>le <xref:System.Globalization.StringInfo> , , et les types de travail avec Unicode, UTF-16, et UTF-8.

Le *terme caractère* est utilisé ici dans le sens général de *ce qu’un lecteur perçoit comme un seul élément d’affichage*. Les exemples courants sont la lettre " a🐂", le symbole " et l’emoji " " Parfois, ce qui ressemble à un personnage est en fait composé de plusieurs éléments d’affichage indépendants, comme l’explique la section sur [les clusters de grapheme.](#grapheme-clusters)

## <a name="the-string-and-char-types"></a>Les types de cordes et d’ombles

Une instance de la classe [de cordes](xref:System.String) représente un texte. A `string` est logiquement une séquence de valeurs 16 bits, dont chacune est un exemple de la struction de [l’omble chevalier.](xref:System.Char) La [ficelle. La](xref:System.String.Length) propriété de `char` longueur renvoie le nombre de cas dans l’exemple. `string`

La fonction d’échantillon suivante imprime les valeurs dans `char` la `string`notation hexadecimale de tous les cas dans un :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Passez la chaîne "Bonjour" à cette fonction, et vous obtenez la sortie suivante:

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

Chaque personnage est représenté `char` par une seule valeur. Ce modèle est vrai pour la plupart des langues du monde. Par exemple, voici la sortie de deux personnages chinois qui sonnent comme *nô hôo* et *signifie*bonjour:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Cependant, pour certaines langues et pour certains `char` symboles et emoji, il faut deux instances pour représenter un seul personnage. Par exemple, comparez `char` les caractères et les instances dans le mot qui signifie *Osage* dans la langue Osage :

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

Dans l’exemple précédent, chaque personnage, à `char` l’exception de l’espace, est représenté par deux instances.

Un seul emoji Unicode est `char`également représenté par deux s, comme on le voit dans l’exemple suivant montrant un emoji de bœuf:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Ces exemples montrent `string.Length`que la valeur `char` de , qui indique le nombre de cas, n’indique pas nécessairement le nombre de caractères affichés. Une `char` seule instance en soi ne représente pas nécessairement un personnage.

Les `char` paires qui cartographient à un seul caractère sont appelés *paires de substitution*. Pour comprendre comment ils fonctionnent, vous devez comprendre Unicode et UTF-16 codage.

## <a name="unicode-code-points"></a>Points de code Unicode

Unicode est une norme internationale d’encodage pour une utilisation sur diverses plates-formes et avec différentes langues et scripts.

L’Unicode Standard définit plus de 1,1 million de [points de code](https://www.unicode.org/glossary/#code_point). Un point de code est une valeur d’intégrant qui peut varier de 0 à `U+10FFFF` (décimale 1 114 111). Certains points de code sont attribués à des lettres, des symboles ou des emoji. D’autres sont affectés à des actions qui contrôlent la façon dont le texte ou les caractères sont affichés, comme l’avance à une nouvelle ligne. De nombreux points de code ne sont pas encore attribués.

Voici quelques exemples d’affectations de points de code, avec des liens vers des graphiques Unicode dans lesquels ils apparaissent:

|Decimal|Hex       |Exemple|Description|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [LIGNE FEED](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [PETITE LETTRE LATINE A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | 1er | [LETTRE DE LA CAPITALE LATINE Y AVEC MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [VIEILLE LETTRE TURQUE ORKHON À](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [EMOJI ROSE](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Les points de code sont habituellement mentionnés `U+xxxx`en `xxxx` utilisant la syntaxe , où est la valeur integer encodé hex.

Dans toute la gamme des points de code il y a deux sous-gammes :

* Le **plan multilingue de base (BMP)** dans la gamme `U+0000..U+FFFF`. Cette gamme 16 bits fournit 65 536 points de code, assez pour couvrir la majorité des systèmes d’écriture du monde.
* **Points de code** `U+10000..U+10FFFF`supplémentaires dans la plage . Cette gamme 21 bits fournit plus d’un million de points de code supplémentaires qui peuvent être utilisés pour des langues moins connues et d’autres fins telles que les emojis.

Le diagramme suivant illustre la relation entre le BMP et les points de code supplémentaires.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP et points de code supplémentaires":::

## <a name="utf-16-code-units"></a>Unités de code UTF-16

16 bits Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) est un système de codage de caractère qui utilise des unités de code 16 *bits* pour représenter les points de code Unicode. .NET utilise UTF-16 pour coder `string`le texte dans un . Une `char` instance représente une unité de code 16 bits.

Une seule unité de code 16 bits peut représenter n’importe quel point de code dans la gamme 16 bits de l’avion multilingue de base. Mais pour un point de code `char` dans la plage supplémentaire, deux instances sont nécessaires.

## <a name="surrogate-pairs"></a>Paires de substitution

La traduction de deux valeurs 16 bits à une seule valeur 21 bits est `U+D800` `U+DFFF` facilitée par une gamme spéciale appelée les points de code de *substitution*, de (décimale 55 296 à 57 343), inclusivement.

Le diagramme suivant illustre la relation entre le BMP et les points de code de substitution.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="Points de code BMP et de substitution":::

Lorsqu’un point de`U+D800..U+DBFF`code de substitution *élevé* (`U+DC00..U+DFFF`) est immédiatement suivi d’un faible point de code de *substitution* (), la paire est interprétée comme un point de code supplémentaire en utilisant la formule suivante:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Voici la même formule à l’aide de la notation décimale :

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

Un point de code de substitution *élevé* n’a pas une valeur de nombre plus élevée qu’un point de code de substitution *faible.* Le point de code de substitution élevé est appelé «élevé» parce qu’il est utilisé pour calculer l’ordre supérieur 11 bits de la gamme complète de points de code 21 bits. Le point de code de substitution faible est utilisé pour calculer l’ordre inférieur 10 bits.

Par exemple, le point de code réel `0xD83C` `0xDF39` qui correspond à la paire de substitution et est calculé comme suit:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Voici le même calcul à l’aide de la notation décimale :

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

L’exemple précédent `"\ud83c\udf39"` démontre qu’il s’agit de `U+1F339 ROSE ('🌹')` l’encodage UTF-16 du point de code mentionné précédemment.

## <a name="unicode-scalar-values"></a>Valeurs scalaires Unicode

Le terme [valeur scalaire Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) se réfère à tous les points de code autres que les points de code de substitution. En d’autres termes, une valeur scalaire est n’importe quel point de code qui est attribué à un personnage ou peut être attribué un personnage à l’avenir. "Caractère" se réfère ici à tout ce qui peut être attribué à un point de code, qui comprend des choses telles que les actions qui contrôlent la façon dont le texte ou les caractères sont affichés.

Le diagramme suivant illustre les points de code de valeur scalaires.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Valeurs scalaires":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Le Rune type comme valeur scalaire

Commençant par .NET Core 3.0, le <xref:System.Text.Rune?displayProperty=fullName> type représente une valeur scalaire Unicode. **`Rune`n’est pas disponible en .NET Core 2.x ou .NET Framework 4.x.**

Les `Rune` constructeurs valident que l’instance résultante est une valeur scalaire Unicode valide, sinon ils jettent une exception. L’exemple suivant montre le `Rune` code qui instantané les instances avec succès parce que l’entrée représente des valeurs scalaires valides :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

L’exemple suivant jette une exception parce que le point de code est dans la plage de substitution et ne fait pas partie d’une paire de substitution:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

L’exemple suivant jette une exception parce que le point de code est au-delà de la plage supplémentaire:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Runeexemple d’utilisation : cas de lettre changeant

Une API qui `char` prend un et suppose qu’il travaille avec un point de code `char` qui est une valeur scalaire ne fonctionne pas correctement si le est d’une paire de substitution. Par exemple, considérez la <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> méthode char suivante stringqui fait appel à chacune d’une

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

Si `input` string le contient la lettre `er` de`𐑉`Deseret minuscule ( ), ce code`𐐡`ne la convertira pas en uppercase (). Le code `char.ToUpperInvariant` appelle séparément sur `U+D801` chaque `U+DC49`point de code de substitution, et . Mais `U+D801` n’a pas assez d’informations par lui-même `char.ToUpperInvariant` pour l’identifier comme une lettre minuscule, laisse donc seul. Et il `U+DC49` gère de la même façon. Le résultat est que lowercase ''dans le `input` string ne se convertit pas en uppercase ''.

Voici deux options pour convertir string correctement un uppercase :

* Faites <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> appel string à l’entrée `char`plutôt`char`qu’à itérer - par- . La `string.ToUpperInvariant` méthode a accès aux deux parties de chaque paire de substitution, de sorte qu’il peut gérer tous les points de code Unicode correctement.
* Itérer à travers les valeurs scalaires Unicode comme `Rune` instances au lieu d’instances, `char` comme le montre l’exemple suivant. Étant `Rune` donné qu’une instance est une valeur scalaire Unicode valide, elle peut être transmise aux API qui s’attendent à fonctionner sur une valeur scalaire. Par exemple, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> l’appel tel qu’il est indiqué dans l’exemple suivant donne des résultats corrects :

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Autres Rune API

Le `Rune` type expose les analogues `char` de la plupart des API. Par exemple, les méthodes suivantes reflètent `char` les API statiques sur le type :

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Pour obtenir la valeur scalaire brute `Rune` <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> d’une instance, utilisez la propriété.

Pour convertir `Rune` une instance en `char`une <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> séquence <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> de s, utilisez ou la méthode.

Étant donné que toute valeur scalaire `char` Unicode est représentée `Rune` par une seule ou par `char` une paire de substitution, n’importe quelle instance peut être représentée par au plus deux cas. Utilisez <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> pour voir `char` combien d’instances `Rune` sont nécessaires pour représenter une instance.

Pour plus d’informations `Rune` sur le type .NET, voir la [ `Rune` référence API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Clusters Grapheme

Ce qui ressemble à un personnage pourrait résulter d’une combinaison de plusieurs points de code, de sorte qu’un terme plus descriptif qui est souvent utilisé à la place de "caractère" est [cluster grapheme](https://www.unicode.org/glossary/#grapheme_cluster). Le terme équivalent en .NET est [élément texte](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Considérez `string` les instances comme « a », « ô ». "ô", et`👩🏽‍🚒`". Si votre système d’exploitation les gère comme le `string` précise la norme Unicode, chacun de ces instances apparaît sous forme d’un seul élément de texte ou d’un cluster graphique. Mais les deux derniers sont représentés par plus d’un point de code de valeur scalaire.

* Le string "a" est représenté par une valeur `char` scalaire et contient une instance.

  * `U+0061 LATIN SMALL LETTER A`

* Le string « ô » est représenté par une `char` valeur scalaire et contient un cas.

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* Le string « » ressemble à « ô » mais est représenté par deux `char` valeurs scalaires et contient deux instances.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Enfin, string le`👩🏽‍🚒`" " est représenté par quatre `char` valeurs scalaires et contient sept instances.

  * `U+1F469 WOMAN`(gamme supplémentaire, nécessite une paire de substitution)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(gamme supplémentaire, nécessite une paire de substitution)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(gamme supplémentaire, nécessite une paire de substitution)

Dans certains des exemples précédents - comme le modificateur d’accent combinant ou le modificateur de teint - le point de code ne s’affiche pas comme élément autonome sur l’écran. Il sert plutôt à modifier l’apparence d’un élément texte qui lui a été soumis. Ces exemples montrent qu’il pourrait prendre plusieurs valeurs scalaires pour compenser ce que nous considérons comme un seul « caractère » ou « cluster de grapheme ».

Pour énumérer les grappes de `string`grapheme <xref:System.Globalization.StringInfo> d’un , utilisez la classe comme indiqué dans l’exemple suivant. Si vous êtes familier avec Swift, le type .NET `StringInfo` est conceptuellement similaire au type de [ `character` Swift](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Exemple : char Runecompter , , et les instances d’élément de texte

Dans les API .NET, un cluster de grapheme est appelé *un élément de texte*. La méthode suivante démontre les `char` `Rune`différences entre les instances `string`d’élément texte et les exemples d’élément texte dans un :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Si vous exécutez ce code dans .NET Framework ou .NET Core 3.1 ou plus tôt, le nombre d’éléments texte pour l’emoji montre `4`. Cela est dû à `StringInfo` un bug dans la classe qui est fixé en .NET 5.

### <a name="example-splitting-opno-locstring-instances"></a>Exemple : string fractionnement des instances

Lors `string` du fractionnement des instances, évitez de diviser les paires de substitution et les grappes de grapheme. Prenons l’exemple suivant d’un code incorrect, qui a stringl’intention d’insérer des sauts de ligne tous les 10 caractères dans un :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Parce que ce code `char` énumère les instances, une paire de substitution`char` qui se trouve à chevaucher une limite de 10 sera divisée et une nouvelle ligne injectée entre eux. Cette insertion introduit la corruption de données, parce que les points de code de substitution ne sont significatifs que comme paires.

Le risque de corruption des données n’est pas éliminé si vous énumérez `Rune` les instances (valeurs scalaires) au lieu d’instances. `char` Un ensemble `Rune` d’instances peut constituer un cluster de grapheme`char` qui chevauche une limite de 10. Si l’ensemble de cluster grapheme est divisé, il ne peut pas être interprété correctement.

Une meilleure approche consiste string à briser les clusters en comptant des clusters de grapheme, ou des éléments de texte, comme dans l’exemple suivant :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Comme indiqué précédemment, cependant, dans les implémentations `StringInfo` de .NET autre que .NET 5, la classe pourrait gérer certains clusters de grapheme incorrectement.

## <a name="utf-8-and-utf-32"></a>UTF-8 et UTF-32

Les sections précédentes se sont concentrées sur UTF-16 `string` parce que c’est ce que .NET utilise pour coder les instances. Il existe d’autres systèmes d’encodage pour Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) et [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Ces codages utilisent des unités de code 8 bits et des unités de code 32 bits, respectivement.

Comme UTF-16, UTF-8 nécessite plusieurs unités de code pour représenter certaines valeurs scalaires Unicode. UTF-32 peut représenter n’importe quelle valeur scalaire dans une seule unité de code 32 bits.

Voici quelques exemples montrant comment le même point de code Unicode est représenté dans chacun de ces trois systèmes d’encodage Unicode :

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

Comme indiqué précédemment, une seule unité de code UTF-16 d’une paire de [substitution](#surrogate-pairs) n’a aucun sens par lui-même. De la même manière, une seule unité de code UTF-8 n’a pas de sens en soi si elle est dans une séquence de deux, trois ou quatre utilisés pour calculer une valeur scalaire.

### <a name="endianness"></a>Endianness

Dans .NET, les unités de code UTF-16 d’un string sont stockées dans la mémoire`char` contigu comme une séquence d’intégrateurs 16 bits (instances). Les bits des unités de code individuelles sont disposés en fonction de [l’endianness](https://en.wikipedia.org/wiki/Endianness) de l’architecture actuelle.

Sur une architecture peu-endienne, le string composé des points `[ D801 DCCC ]` de code UTF-16 `[ 0x01, 0xD8, 0xCC, 0xDC ]`serait exposé en mémoire comme les octets . Sur une architecture big-endian que la même string chose `[ 0xD8, 0x01, 0xDC, 0xCC ]`serait énoncée dans la mémoire que les octets .

Les systèmes informatiques qui communiquent entre eux doivent s’entendre sur la représentation des données traversant le fil. La plupart des protocoles réseau utilisent UTF-8 comme norme lors de la transmission du texte, en partie pour éviter les problèmes qui pourraient résulter d’une machine big-endian communiquer avec une machine peu-endienne. Les string points `[ F0 90 93 8C ]` de code UTF-8 seront toujours représentés `[ 0xF0, 0x90, 0x93, 0x8C ]` comme les octets indépendamment de l’endianness.

Pour utiliser UTF-8 pour la transmission de texte, les applications .NET utilisent souvent le code comme l’exemple suivant :

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

Dans l’exemple précédent, la méthode [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) décode `string` l’UTF-16 en une série de valeurs scalaires Unicode, puis il réencode ces `byte` valeurs scalaires en UTF-8 et place la séquence résultante dans un tableau. La méthode [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) effectue la transformation opposée, convertissant `byte` un tableau UTF-8 en utF-16 `string`.

> [!WARNING]
> Étant donné QUE l’UTF-8 est monnaie courante sur Internet, il peut être tentant de lire les octets bruts du fil et de traiter les données comme si c’était UTF-8. Cependant, vous devez valider qu’il est en effet bien formé. Un client malveillant peut soumettre UTF-8 mal formé à votre service. Si vous utilisez ces données comme si elles étaient bien formées, elles pourraient causer des erreurs ou des failles de sécurité dans votre application. Pour valider les données UTF-8, `Encoding.UTF8.GetString`vous pouvez utiliser une méthode comme `string`, qui effectuera la validation tout en convertissant les données entrantes en un .

### <a name="well-formed-encoding"></a>Codage bien formé

Un codage Unicode bien string formé est une des unités de code qui peuvent être décodés sans ambiguïté et sans erreur dans une séquence de valeurs scalaires Unicode. Les données bien formées peuvent être transcodées librement entre UTF-8, UTF-16 et UTF-32.

La question de savoir si une séquence d’encodage est bien formée ou non n’est pas liée à l’endianness de l’architecture d’une machine. Une séquence UTF-8 mal formée est mal formée de la même manière sur les machines big-endian et little-endian.

Voici quelques exemples d’encodages mal formés :

* Dans UTF-8, `[ 6C C2 61 ]` la séquence est `C2` mal formée `61`parce qu’elle ne peut pas être suivie par .

* Dans UTF-16, `[ DC00 DD00 ]` la séquence (ou, string `"\udc00\udd00"`en C, le ) `DC00` est mal formée parce `DD00`que la mère porteuse faible ne peut pas être suivie par une autre faible mère porteuse .

* Dans UTF-32, `[ 0011ABCD ]` la séquence est `0011ABCD` mal formée parce qu’elle est en dehors de la gamme des valeurs scalaires Unicode.

Dans .NET, `string` les instances contiennent presque toujours des données UTF-16 bien formées, mais ce n’est pas garanti. Les exemples suivants montrent un code Cmd valide qui crée `string` des données UTF-16 mal formées dans les cas.

* Un littéral mal formé:

  ```csharp
  const string s = "\ud800";
  ```

* Un sous-cordon qui divise une paire de substitution:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Les API comme [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) ne `string` reviennent jamais à des cas mal formés. `Encoding.GetString`et `Encoding.GetBytes` les méthodes détectent les séquences mal formées dans l’entrée et effectuent la substitution de caractère lors de la génération de la sortie. Par exemple, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) si l’on voit un byte non-ASCII dans l’entrée (en dehors de la plage U-0000..U-007F), il insère un «?» dans l’instance retournée. `string` [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)remplace les séquences UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` mal formées par dans l’instance retournée. `string` Pour plus d’informations, consultez [la norme Unicode](https://www.unicode.org/versions/latest/), sections 5.22 et 3.9.

Les `Encoding` classes intégrées peuvent également être configurées pour lancer une exception plutôt que d’effectuer la substitution de caractères lorsque des séquences mal formées sont vues. Cette approche est souvent utilisée dans des applications sensibles à la sécurité où la substitution de caractères peut ne pas être acceptable.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Pour plus d’informations sur `Encoding` la façon d’utiliser les classes intégrées, voir [Comment utiliser les classes d’encodage des personnages en .NET](character-encoding.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Mondialisation et localisation](../../../docs/standard/globalization-localization/index.md)
