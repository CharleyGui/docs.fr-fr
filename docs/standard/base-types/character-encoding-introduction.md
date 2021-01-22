---
title: Présentation de char l’encodage acter dans .net
description: En savoir plus sur char l’encodage et le décodage acter dans .net.
ms.date: 03/09/2020
ms.topic: conceptual
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 92710e2d223d1d765efc7e877cb16546ef372907
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693135"
---
# <a name="character-encoding-in-net"></a>Encodage de caractères dans .NET

Cet article fournit une introduction aux char systèmes d’encodage acter utilisés par .net. L’article explique comment les <xref:System.String> <xref:System.Char> types,, <xref:System.Text.Rune> et <xref:System.Globalization.StringInfo> fonctionnent avec Unicode, UTF-16 et UTF-8.

Le terme *char acter* est utilisé ici dans le sens général de *ce qu’un lecteur perçoit comme un seul élément d’affichage*. Les exemples les plus courants sont la lettre « a », le symbole « @ » et l’Emoji « 🐂 ». Parfois, l’aspect char d’un acter est composé de plusieurs éléments d’affichage indépendants, comme l’explique la section sur les [clusters graphèmes](#grapheme-clusters) .

## <a name="the-no-locstring-and-no-locchar-types"></a>stringTypes et char

Une instance de la [string](xref:System.String) classe représente du texte. Un `string` est logiquement une séquence de valeurs 16 bits, chacune d’elles étant une instance de la [char](xref:System.Char) structure. [ string . ](xref:System.String.Length)La propriété Length retourne le nombre d' `char` instances dans l' `string` instance.

L’exemple de fonction suivant imprime les valeurs en notation hexadécimale de toutes les `char` instances dans un `string` :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/PrintStringChars. cs" ID = "SnippetPrintChars" :::

Transmettez le string « Hello » à cette fonction et vous recevez la sortie suivante :

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

Chaque char acter est représenté par une `char` valeur unique. Ce modèle est valable pour la plupart des langues du monde. Par exemple, voici la sortie de deux acters chinois char qui ressemble à *Nǐ hǎo* et signifiant *Hello*:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Toutefois, pour certains langages et pour certains symboles et emoji, il faut deux `char` instances pour représenter un seul char acter. Par exemple, comparez les char acters et les `char` instances du mot « *Osage* » dans le langage Osage :

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

Dans l’exemple précédent, chaque char acter, à l’exception de l’espace, est représenté par deux `char` instances.

Un seul Emoji Unicode est également représenté par deux `char` , comme illustré dans l’exemple suivant, qui montre un Emoji Ox :

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Ces exemples montrent que la valeur de `string.Length` , qui indique le nombre d' `char` instances, n’indique pas nécessairement le nombre de char acters affichés. Une seule `char` instance de elle-même ne représente pas nécessairement un char acter.

Les `char` paires qui mappent à un seul char acter sont appelées *paires de substitution*. Pour comprendre comment elles fonctionnent, vous devez comprendre l’encodage Unicode et UTF-16.

## <a name="unicode-code-points"></a>Points de code Unicode

Unicode est une norme internationale d’encodage à utiliser sur différentes plateformes et avec différents langages et scripts.

La norme Unicode définit plus de 1,1 million [points de code](https://www.unicode.org/glossary/#code_point). Un point de code est une valeur entière qui peut être comprise entre 0 et `U+10FFFF` (décimal 1 114 111). Certains points de code sont assignés à des lettres, des symboles ou des Emoji. D’autres sont affectés aux actions qui contrôlent le mode d’affichage du texte ou char des acters, par exemple avancer sur une nouvelle ligne. De nombreux points de code ne sont pas encore assignés.

Voici quelques exemples d’attributions de point de code, avec des liens vers Unicode char TS dans lequel ils apparaissent :

|Decimal|Hex       |Exemple|Description|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [SAUT DE LIGNE](https://www.unicode.org/charts/PDF/U0000.pdf) |
|97     | `U+0061` | a | [LETTRE MINUSCULE LATINE A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [LETTRE MAJUSCULE LATINE Y AVEC MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68 675 | `U+10C43`| 𐱃 | [ANCIENNE LETTRE TURQUE ORKHON À](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127 801| `U+1F339`| 🌹 | [ROSE-Emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Les points de code sont habituellement référencés à l’aide de la syntaxe `U+xxxx` , où `xxxx` est la valeur entière encodée en hexadécimal.

Au sein de la plage complète de points de code, il existe deux sous-plages :

* Le **plan multilingue de base (BMP)** de la plage `U+0000..U+FFFF` . Cette plage de 16 bits fournit 65 536 points de code, suffisants pour couvrir la majorité des systèmes d’écriture au monde.
* **Points de code supplémentaires** dans la plage `U+10000..U+10FFFF` . Cette plage de 21 bits fournit plus d’un million de points de code supplémentaires qui peuvent être utilisés pour des langages moins connus et d’autres fins, telles que des Emoji.

Le diagramme suivant illustre la relation entre le BMP et les points de code supplémentaires.

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/BMP-and-Supplementary. svg "alt-text =" BMP et les points de code supplémentaires " :::

## <a name="utf-16-code-units"></a>Unités de code UTF-16

le format [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)(Unicode Transformation Format) 16 bits est un char système de codage acter qui utilise des *unités de code* 16 bits pour représenter les points de code Unicode. .NET utilise UTF-16 pour encoder le texte dans un `string` . Une `char` instance représente une unité de code 16 bits.

Une seule unité de code 16 bits peut représenter n’importe quel point de code dans la plage de 16 bits du plan multilingue de base. Toutefois, pour un point de code dans la plage supplémentaire, deux `char` instances sont nécessaires.

## <a name="surrogate-pairs"></a>Paires de substitution

La conversion de valeurs 2 16 bits en valeur 21 bits unique est facilitée par une plage spéciale appelée points de code de *substitution*, de `U+D800` à `U+DFFF` (décimal 55 296 à 57 343), incluse.

Le diagramme suivant illustre la relation entre le BMP et les points de code de substitution.

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/BMP-and-Surrogate. svg "alt-text =" BMP et les points de code de substitution " :::

Quand un point de code de *substitution étendu* ( `U+D800..U+DBFF` ) est immédiatement suivi d’un point de code de *substitution faible* ( `U+DC00..U+DFFF` ), la paire est interprétée comme un point de code supplémentaire à l’aide de la formule suivante :

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Voici la même formule utilisant la notation décimale :

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

Un point de code de substitution *étendu* n’a pas une valeur numérique supérieure à un point de code de substitution *faible* . Le point de code de substitution étendu est appelé « High », car il est utilisé pour calculer les 11 bits d’ordre supérieur de la plage de points de code 21 bits complète. Le point de code de substitution faible est utilisé pour calculer les 10 bits de poids faible.

Par exemple, le point de code réel qui correspond à la paire de substitution `0xD83C` et `0xDF39`  est calculé comme suit :

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Voici le même calcul à l’aide de la notation décimale :

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

L’exemple précédent montre que `"\ud83c\udf39"` est l’encodage UTF-16 du `U+1F339 ROSE ('🌹')` point de code mentionné précédemment.

## <a name="unicode-scalar-values"></a>Valeurs scalaires Unicode

Le terme [valeur scalaire Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) fait référence à tous les points de code autres que les points de code de substitution. En d’autres termes, une valeur scalaire correspond à n’importe quel point de code affecté char à un acter ou char à un acter à l’avenir. « Caractère » fait référence à tout ce qui peut être assigné à un point de code, qui comprend des actions qui contrôlent l’affichage du texte ou char des acters.

Le diagramme suivant illustre les points de code de la valeur scalaire.

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/Scalar-values. svg "alt-text =" valeurs scalaires " :::

### <a name="the-no-locrune-type-as-a-scalar-value"></a>RuneType en tant que valeur scalaire

À compter de .NET Core 3,0, le <xref:System.Text.Rune?displayProperty=fullName> type représente une valeur scalaire Unicode. **`Rune` n’est pas disponible dans .NET Core 2. x ou .NET Framework 4. x.**

Les `Rune` constructeurs vérifient que l’instance résultante est une valeur scalaire Unicode valide, sinon elles lèvent une exception. L’exemple suivant montre le code qui instancie correctement `Rune` des instances, car l’entrée représente des valeurs scalaires valides :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetValid" :::

L’exemple suivant lève une exception, car le point de code se trouve dans la plage de substitution et ne fait pas partie d’une paire de substitution :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetInvalidSurrogate" :::

L’exemple suivant lève une exception, car le point de code est au-delà de la plage supplémentaire :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetInvalidHigh" :::

### <a name="no-locrune-usage-example-changing-letter-case"></a>Rune exemple d’utilisation : modification de la casse des lettres

Une API qui prend un `char` et suppose qu’elle utilise un point de code qui est une valeur scalaire ne fonctionne pas correctement si le `char` est issu d’une paire de substitution. Par exemple, considérez la méthode suivante qui appelle <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> sur chaque char dans un string :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/ConvertToUpper. cs" ID = "SnippetBadExample" :::

Si `input` string contient la lettre de Deseret minuscules `er` ( `𐑉` ), ce code ne le convertit pas en majuscules ( `𐐡` ). Le code appelle `char.ToUpperInvariant` séparément sur chaque point de code de substitution, `U+D801` et `U+DC49` . Mais `U+D801` ne dispose pas d’informations suffisantes pour l’identifier comme une lettre minuscule `char.ToUpperInvariant` . Et il gère `U+DC49` de la même façon. Le résultat est que les minuscules « 𐑉 » dans le `input` string ne sont pas converties en majuscules « 𐑉 ».

Voici deux options pour convertir correctement un string en majuscules :

* Appelez <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> sur l’entrée string plutôt que d’effectuer `char` une itération par `char` . La `string.ToUpperInvariant` méthode a accès aux deux parties de chaque paire de substitution. elle peut donc gérer correctement tous les points de code Unicode.
* Itérez au sein des valeurs scalaires Unicode en tant qu’instances plutôt qu’en tant `Rune` `char` qu’instances, comme indiqué dans l’exemple suivant. Comme une `Rune` instance est une valeur scalaire Unicode valide, elle peut être passée à des API qui s’attendent à fonctionner sur une valeur scalaire. Par exemple, l’appel de <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant donne des résultats corrects :

  ::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/ConvertToUpper. cs" ID = "SnippetGoodExample" :::

### <a name="other-no-locrune-apis"></a>Autres Rune API

Le `Rune` type expose des analogies de nombreuses `char` API. Par exemple, les méthodes suivantes reflètent les API statiques sur le `char` type :

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Pour obtenir la valeur scalaire brute d’une `Rune` instance, utilisez la <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> propriété.

Pour reconvertir une `Rune` instance en une séquence de `char` , utilisez <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> ou la <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> méthode.

Étant donné que toute valeur scalaire Unicode `char` peut être représentée par un unique ou par une paire de substitution, toute `Rune` instance peut être représentée par au plus 2 `char` instances. Utilisez <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> pour voir le nombre d' `char` instances nécessaires pour représenter une `Rune` instance.

Pour plus d’informations sur le `Rune` type .net, consultez la référence de l' [ `Rune` API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Clusters graphèmes

Comme un char acter peut résulter d’une combinaison de plusieurs points de code, un terme plus descriptif, souvent utilisé à la place de « char acter », est le [cluster graphèmes](https://www.unicode.org/glossary/#grapheme_cluster). Le terme équivalent dans .NET est l' [élément de texte](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Examinez les `string` instances « a », « á », « á » et « `👩🏽‍🚒` ». Si votre système d’exploitation les gère comme spécifié par la norme Unicode, chacune de ces `string` instances apparaît sous la forme d’un seul élément de texte ou d’un seul cluster graphèmes. Toutefois, les deux derniers sont représentés par plusieurs points de code de valeur scalaire.

* Le string « a » est représenté par une valeur scalaire et contient une `char` instance.

  * `U+0061 LATIN SMALL LETTER A`

* Le string « á » est représenté par une valeur scalaire et contient une `char` instance.

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* Le string « á » ressemble à « á », mais il est représenté par deux valeurs scalaires et contient `char` deux instances.

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Enfin, le string « `👩🏽‍🚒` » est représenté par quatre valeurs scalaires et contient sept `char` instances.

  * `U+1F469 WOMAN` (plage supplémentaire, nécessite une paire de substitution)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (plage supplémentaire, nécessite une paire de substitution)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE` (plage supplémentaire, nécessite une paire de substitution)

Dans certains des exemples précédents, tels que le modificateur d’accent ou le modificateur de tonalité de la peau, le point de code ne s’affiche pas en tant qu’élément autonome à l’écran. Au lieu de cela, elle permet de modifier l’apparence d’un élément de texte qui précède. Ces exemples montrent qu’il peut prendre plusieurs valeurs scalaires pour créer ce que nous considérons comme un seul char cluster « acter » ou « graphèmes ».

Pour énumérer les clusters graphèmes d’un `string` , utilisez la <xref:System.Globalization.StringInfo> classe comme indiqué dans l’exemple suivant. Si vous êtes familiarisé avec SWIFT, le `StringInfo` type .net est conceptuellement similaire au [ `character` type SWIFT](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a>Exemple : char instances d' Rune éléments de texte Count, et

Dans les API .NET, un cluster graphèmes est appelé un *élément de texte*. La méthode suivante montre les différences entre `char` les `Rune` instances d’élément de texte, et dans un `string` :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/CountTextElements. cs" ID = "SnippetCountMethod" :::

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/CountTextElements. cs" ID = "SnippetCallCountMethod" :::

Si vous exécutez ce code dans .NET Framework ou .NET Core 3,1 ou une version antérieure, le nombre d’éléments de texte pour l’Emoji s’affiche `4` . Cela est dû à un bogue dans la `StringInfo` classe qui est résolu dans .net 5.

### <a name="example-splitting-no-locstring-instances"></a>Exemple : fractionnement d' string instances

Lors du fractionnement `string` des instances, évitez de fractionner les paires de substitution et les clusters graphèmes. Prenons l’exemple suivant de code incorrect, qui envisage d’insérer des sauts de ligne tous les 10 char acters dans un string :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/InsertNewlines. cs" ID = "SnippetBadExample" :::

Étant donné que ce code énumère `char` les instances, une paire de substitution qui se trouve sur un chevauchement de 10 `char` limites est fractionnée et un saut de ligne est injecté entre eux. Cette insertion introduit une altération des données, car les points de code de substitution sont significatifs uniquement en tant que paires.

Le risque d’altération des données n’est pas éliminé si vous énumérez `Rune` des instances (valeurs scalaires) au lieu d' `char` instances. Un ensemble d' `Rune` instances peut créer un cluster graphèmes qui chevauche 10 `char` limites. Si le jeu de clusters graphèmes est fractionné, il ne peut pas être interprété correctement.

Une meilleure approche consiste à rompre le string en comptant les clusters graphèmes ou les éléments de texte, comme dans l’exemple suivant :

::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/InsertNewlines. cs" ID = "SnippetGoodExample" :::

Comme indiqué précédemment, toutefois, dans les implémentations de .NET autres que .NET 5, la `StringInfo` classe peut gérer des clusters graphèmes de manière incorrecte.

## <a name="utf-8-and-utf-32"></a>UTF-8 et UTF-32

Les sections précédentes sont axées sur UTF-16, car c’est ce que .NET utilise pour encoder des `string` instances. Il existe d’autres systèmes d’encodage pour Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) et [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Ces encodages utilisent des unités de code 8 bits et des unités de code 32 bits, respectivement.

Comme UTF-16, UTF-8 requiert que plusieurs unités de code représentent des valeurs scalaires Unicode. UTF-32 peut représenter n’importe quelle valeur scalaire dans une seule unité de code 32 bits.

Voici quelques exemples montrant comment le même point de code Unicode est représenté dans chacun de ces trois systèmes d’encodage Unicode :

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

Comme indiqué précédemment, une seule unité de code UTF-16 d’une [paire de substitution](#surrogate-pairs) n’est pas significative. De la même façon, une seule unité de code UTF-8 n’a pas de sens pour elle-même si elle se trouve dans une séquence de deux, trois ou quatre utilisées pour calculer une valeur scalaire.

### <a name="endianness"></a>Endianness

Dans .NET, les unités de code UTF-16 d’un string sont stockées dans une mémoire contiguë sous la forme d’une séquence d’entiers 16 bits ( `char` instances). Les bits des unités de code individuelles sont disposés selon le [endianness](https://en.wikipedia.org/wiki/Endianness) de l’architecture actuelle.

Sur une architecture avec primauté des octets de poids faible, les string points de code UTF-16 `[ D801 DCCC ]` sont disposés en mémoire comme octets `[ 0x01, 0xD8, 0xCC, 0xDC ]` . Sur une architecture avec primauté des octets de poids fort (Big-endian), string elle serait présentée en mémoire comme octets `[ 0xD8, 0x01, 0xDC, 0xCC ]` .

Les systèmes informatiques qui communiquent entre eux doivent s’accorder sur la représentation des données qui transitent par le réseau. La plupart des protocoles réseau utilisent UTF-8 comme norme lors de la transmission de texte, en partie afin d’éviter les problèmes qui peuvent résulter d’une machine à Big-endian communiquant avec un ordinateur Little-endian. Le string composé des points de code UTF-8 `[ F0 90 93 8C ]` est toujours représenté sous la forme d’octets `[ 0xF0, 0x90, 0x93, 0x8C ]` , quel que soit le endianness.

Pour utiliser UTF-8 pour transmettre du texte, les applications .NET utilisent souvent du code similaire à l’exemple suivant :

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

Dans l’exemple précédent, la méthode [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) décode le UTF-16 `string` en une série de valeurs scalaires Unicode, puis Recode ces valeurs scalaires en UTF-8 et place la séquence résultante dans un `byte` tableau. L' [encodage de méthode. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) effectue la transformation inverse, en convertissant un tableau UTF-8 `byte` en UTF-16 `string` .

> [!WARNING]
> Étant donné qu’UTF-8 est courant sur Internet, il peut être tentant de lire des octets bruts à partir du câble et de traiter les données comme s’il s’agissait d’UTF-8. Toutefois, vous devez vérifier qu’il est bien formé. Un client malveillant peut soumettre un UTF-8 incorrect à votre service. Si vous opérez sur ces données comme si elles étaient correctement formées, cela peut entraîner des erreurs ou des failles de sécurité dans votre application. Pour valider des données UTF-8, vous pouvez utiliser une méthode comme `Encoding.UTF8.GetString` , qui effectuera la validation lors de la conversion des données entrantes en `string` .

### <a name="well-formed-encoding"></a>Encodage bien formé

Un encodage Unicode bien formé est un string d’unités de code qui peuvent être décodées sans ambiguïté et sans erreur dans une séquence de valeurs scalaires Unicode. Les données correctement formées peuvent être transcodées librement entre UTF-8, UTF-16 et UTF-32.

La question de savoir si une séquence d’encodage est correctement formée ou non n’est pas liée à l’endianness de l’architecture d’une machine. Une séquence UTF-8 incorrecte est incorrecte de la même façon sur les ordinateurs Big-endian et Little-endian.

Voici quelques exemples de codages incorrects :

* En UTF-8, la séquence `[ 6C C2 61 ]` est incorrecte car `C2` ne peut pas être suivi de `61` .

* En UTF-16, la séquence `[ DC00 DD00 ]` (ou, en C#,) est incorrecte string `"\udc00\udd00"` , car le substitut faible `DC00` ne peut pas être suivi d’un autre substitut faible `DD00` .

* En UTF-32, la séquence `[ 0011ABCD ]` est incorrecte car `0011ABCD` est en dehors de la plage de valeurs scalaires Unicode.

Dans .NET, les `string` instances contiennent presque toujours des données UTF-16 bien formées, mais cela n’est pas garanti. Les exemples suivants illustrent du code C# valide qui crée des données UTF-16 incorrectes dans des `string` instances de.

* Littéral incorrect :

  ```csharp
  const string s = "\ud800";
  ```

* Un Sub string qui divise une paire de substitution :

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Les API telles que [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) ne retournent jamais des instances mal formées `string` . `Encoding.GetString``Encoding.GetBytes`les méthodes et détectent les séquences incorrectes dans l’entrée et effectuent une char substitution acter lors de la génération de la sortie. Par exemple, si [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) détecte un octet non-ASCII dans l’entrée (en dehors de la plage u + 0000.. U + 007F), il insère un «  ? » dans l' `string` instance retournée. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) remplace les séquences UTF-8 incorrectes par `U+FFFD REPLACEMENT CHARACTER ('�')` dans l' `string` instance retournée. Pour plus d’informations, consultez [la norme Unicode](https://www.unicode.org/versions/latest/), sections 5,22 et 3,9.

Les `Encoding` classes intégrées peuvent également être configurées pour lever une exception au lieu d’effectuer une char substitution acter quand des séquences incorrectes sont affichées. Cette approche est souvent utilisée dans les applications sensibles à la sécurité où la char substitution de acter peut ne pas être acceptable.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Pour plus d’informations sur l’utilisation des classes intégrées `Encoding` , consultez Guide pratique [pour utiliser char des classes d’encodage acter dans .net](character-encoding.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalisation et localisation](../globalization-localization/index.md)
