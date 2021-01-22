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
# <a name="character-encoding-in-net"></a><span data-ttu-id="c1ea6-103">Encodage de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="c1ea6-103">Character encoding in .NET</span></span>

<span data-ttu-id="c1ea6-104">Cet article fournit une introduction aux char systèmes d’encodage acter utilisés par .net.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="c1ea6-105">L’article explique comment les <xref:System.String> <xref:System.Char> types,, <xref:System.Text.Rune> et <xref:System.Globalization.StringInfo> fonctionnent avec Unicode, UTF-16 et UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="c1ea6-106">Le terme *char acter* est utilisé ici dans le sens général de *ce qu’un lecteur perçoit comme un seul élément d’affichage*.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="c1ea6-107">Les exemples les plus courants sont la lettre « a », le symbole « @ » et l’Emoji « 🐂 ».</span><span class="sxs-lookup"><span data-stu-id="c1ea6-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="c1ea6-108">Parfois, l’aspect char d’un acter est composé de plusieurs éléments d’affichage indépendants, comme l’explique la section sur les [clusters graphèmes](#grapheme-clusters) .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="c1ea6-109">stringTypes et char</span><span class="sxs-lookup"><span data-stu-id="c1ea6-109">The string and char types</span></span>

<span data-ttu-id="c1ea6-110">Une instance de la [string](xref:System.String) classe représente du texte.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="c1ea6-111">Un `string` est logiquement une séquence de valeurs 16 bits, chacune d’elles étant une instance de la [char](xref:System.Char) structure.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="c1ea6-112">[ string . ](xref:System.String.Length)La propriété Length retourne le nombre d' `char` instances dans l' `string` instance.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="c1ea6-113">L’exemple de fonction suivant imprime les valeurs en notation hexadécimale de toutes les `char` instances dans un `string` :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

<span data-ttu-id="c1ea6-114">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/PrintStringChars. cs" ID = "SnippetPrintChars" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="c1ea6-115">Transmettez le string « Hello » à cette fonction et vous recevez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-115">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="c1ea6-116">Chaque char acter est représenté par une `char` valeur unique.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-116">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="c1ea6-117">Ce modèle est valable pour la plupart des langues du monde.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="c1ea6-118">Par exemple, voici la sortie de deux acters chinois char qui ressemble à *Nǐ hǎo* et signifiant *Hello*:</span><span class="sxs-lookup"><span data-stu-id="c1ea6-118">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="c1ea6-119">Toutefois, pour certains langages et pour certains symboles et emoji, il faut deux `char` instances pour représenter un seul char acter.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-119">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="c1ea6-120">Par exemple, comparez les char acters et les `char` instances du mot « *Osage* » dans le langage Osage :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-120">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="c1ea6-121">Dans l’exemple précédent, chaque char acter, à l’exception de l’espace, est représenté par deux `char` instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-121">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="c1ea6-122">Un seul Emoji Unicode est également représenté par deux `char` , comme illustré dans l’exemple suivant, qui montre un Emoji Ox :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-122">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="c1ea6-123">Ces exemples montrent que la valeur de `string.Length` , qui indique le nombre d' `char` instances, n’indique pas nécessairement le nombre de char acters affichés.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-123">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="c1ea6-124">Une seule `char` instance de elle-même ne représente pas nécessairement un char acter.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-124">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="c1ea6-125">Les `char` paires qui mappent à un seul char acter sont appelées *paires de substitution*.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-125">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="c1ea6-126">Pour comprendre comment elles fonctionnent, vous devez comprendre l’encodage Unicode et UTF-16.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="c1ea6-127">Points de code Unicode</span><span class="sxs-lookup"><span data-stu-id="c1ea6-127">Unicode code points</span></span>

<span data-ttu-id="c1ea6-128">Unicode est une norme internationale d’encodage à utiliser sur différentes plateformes et avec différents langages et scripts.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="c1ea6-129">La norme Unicode définit plus de 1,1 million [points de code](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="c1ea6-130">Un point de code est une valeur entière qui peut être comprise entre 0 et `U+10FFFF` (décimal 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="c1ea6-131">Certains points de code sont assignés à des lettres, des symboles ou des Emoji.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="c1ea6-132">D’autres sont affectés aux actions qui contrôlent le mode d’affichage du texte ou char des acters, par exemple avancer sur une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-132">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="c1ea6-133">De nombreux points de code ne sont pas encore assignés.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="c1ea6-134">Voici quelques exemples d’attributions de point de code, avec des liens vers Unicode char TS dans lequel ils apparaissent :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-134">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="c1ea6-135">Decimal</span><span class="sxs-lookup"><span data-stu-id="c1ea6-135">Decimal</span></span>|<span data-ttu-id="c1ea6-136">Hex</span><span class="sxs-lookup"><span data-stu-id="c1ea6-136">Hex</span></span>       |<span data-ttu-id="c1ea6-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1ea6-137">Example</span></span>|<span data-ttu-id="c1ea6-138">Description</span><span class="sxs-lookup"><span data-stu-id="c1ea6-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="c1ea6-139">10</span><span class="sxs-lookup"><span data-stu-id="c1ea6-139">10</span></span>     | `U+000A` |<span data-ttu-id="c1ea6-140">N/A</span><span class="sxs-lookup"><span data-stu-id="c1ea6-140">N/A</span></span>| <span data-ttu-id="c1ea6-141">[SAUT DE LIGNE](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-141">[LINE FEED](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="c1ea6-142">97</span><span class="sxs-lookup"><span data-stu-id="c1ea6-142">97</span></span>     | `U+0061` | <span data-ttu-id="c1ea6-143">a</span><span class="sxs-lookup"><span data-stu-id="c1ea6-143">a</span></span> | <span data-ttu-id="c1ea6-144">[LETTRE MINUSCULE LATINE A](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-144">[LATIN SMALL LETTER A](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="c1ea6-145">562</span><span class="sxs-lookup"><span data-stu-id="c1ea6-145">562</span></span>    | `U+0232` | <span data-ttu-id="c1ea6-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="c1ea6-146">Ȳ</span></span> | <span data-ttu-id="c1ea6-147">[LETTRE MAJUSCULE LATINE Y AVEC MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="c1ea6-148">68 675</span><span class="sxs-lookup"><span data-stu-id="c1ea6-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="c1ea6-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="c1ea6-149">𐱃</span></span> | <span data-ttu-id="c1ea6-150">[ANCIENNE LETTRE TURQUE ORKHON À](https://www.unicode.org/charts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="c1ea6-151">127 801</span><span class="sxs-lookup"><span data-stu-id="c1ea6-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="c1ea6-152">🌹</span><span class="sxs-lookup"><span data-stu-id="c1ea6-152">🌹</span></span> | <span data-ttu-id="c1ea6-153">[ROSE-Emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-153">[ROSE emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="c1ea6-154">Les points de code sont habituellement référencés à l’aide de la syntaxe `U+xxxx` , où `xxxx` est la valeur entière encodée en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="c1ea6-155">Au sein de la plage complète de points de code, il existe deux sous-plages :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="c1ea6-156">Le **plan multilingue de base (BMP)** de la plage `U+0000..U+FFFF` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="c1ea6-157">Cette plage de 16 bits fournit 65 536 points de code, suffisants pour couvrir la majorité des systèmes d’écriture au monde.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="c1ea6-158">**Points de code supplémentaires** dans la plage `U+10000..U+10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="c1ea6-159">Cette plage de 21 bits fournit plus d’un million de points de code supplémentaires qui peuvent être utilisés pour des langages moins connus et d’autres fins, telles que des Emoji.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="c1ea6-160">Le diagramme suivant illustre la relation entre le BMP et les points de code supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/BMP-and-Supplementary. svg "alt-text =" BMP et les points de code supplémentaires " :::

## <a name="utf-16-code-units"></a><span data-ttu-id="c1ea6-162">Unités de code UTF-16</span><span class="sxs-lookup"><span data-stu-id="c1ea6-162">UTF-16 code units</span></span>

<span data-ttu-id="c1ea6-163">le format [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)(Unicode Transformation Format) 16 bits est un char système de codage acter qui utilise des *unités de code* 16 bits pour représenter les points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-163">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="c1ea6-164">.NET utilise UTF-16 pour encoder le texte dans un `string` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-164">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="c1ea6-165">Une `char` instance représente une unité de code 16 bits.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-165">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="c1ea6-166">Une seule unité de code 16 bits peut représenter n’importe quel point de code dans la plage de 16 bits du plan multilingue de base.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="c1ea6-167">Toutefois, pour un point de code dans la plage supplémentaire, deux `char` instances sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-167">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="c1ea6-168">Paires de substitution</span><span class="sxs-lookup"><span data-stu-id="c1ea6-168">Surrogate pairs</span></span>

<span data-ttu-id="c1ea6-169">La conversion de valeurs 2 16 bits en valeur 21 bits unique est facilitée par une plage spéciale appelée points de code de *substitution*, de `U+D800` à `U+DFFF` (décimal 55 296 à 57 343), incluse.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="c1ea6-170">Le diagramme suivant illustre la relation entre le BMP et les points de code de substitution.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/BMP-and-Surrogate. svg "alt-text =" BMP et les points de code de substitution " :::

<span data-ttu-id="c1ea6-172">Quand un point de code de *substitution étendu* ( `U+D800..U+DBFF` ) est immédiatement suivi d’un point de code de *substitution faible* ( `U+DC00..U+DFFF` ), la paire est interprétée comme un point de code supplémentaire à l’aide de la formule suivante :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="c1ea6-173">Voici la même formule utilisant la notation décimale :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="c1ea6-174">Un point de code de substitution *étendu* n’a pas une valeur numérique supérieure à un point de code de substitution *faible* .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="c1ea6-175">Le point de code de substitution étendu est appelé « High », car il est utilisé pour calculer les 11 bits d’ordre supérieur de la plage de points de code 21 bits complète.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="c1ea6-176">Le point de code de substitution faible est utilisé pour calculer les 10 bits de poids faible.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="c1ea6-177">Par exemple, le point de code réel qui correspond à la paire de substitution `0xD83C` et `0xDF39`  est calculé comme suit :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="c1ea6-178">Voici le même calcul à l’aide de la notation décimale :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="c1ea6-179">L’exemple précédent montre que `"\ud83c\udf39"` est l’encodage UTF-16 du `U+1F339 ROSE ('🌹')` point de code mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="c1ea6-180">Valeurs scalaires Unicode</span><span class="sxs-lookup"><span data-stu-id="c1ea6-180">Unicode scalar values</span></span>

<span data-ttu-id="c1ea6-181">Le terme [valeur scalaire Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) fait référence à tous les points de code autres que les points de code de substitution.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="c1ea6-182">En d’autres termes, une valeur scalaire correspond à n’importe quel point de code affecté char à un acter ou char à un acter à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-182">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="c1ea6-183">« Caractère » fait référence à tout ce qui peut être assigné à un point de code, qui comprend des actions qui contrôlent l’affichage du texte ou char des acters.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="c1ea6-184">Le diagramme suivant illustre les points de code de la valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char) ::: acter-Encoding-Introduction/Scalar-values. svg "alt-text =" valeurs scalaires " :::

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="c1ea6-186">RuneType en tant que valeur scalaire</span><span class="sxs-lookup"><span data-stu-id="c1ea6-186">The Rune type as a scalar value</span></span>

<span data-ttu-id="c1ea6-187">À compter de .NET Core 3,0, le <xref:System.Text.Rune?displayProperty=fullName> type représente une valeur scalaire Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-187">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="c1ea6-188">**`Rune` n’est pas disponible dans .NET Core 2. x ou .NET Framework 4. x.**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-188">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="c1ea6-189">Les `Rune` constructeurs vérifient que l’instance résultante est une valeur scalaire Unicode valide, sinon elles lèvent une exception.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-189">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="c1ea6-190">L’exemple suivant montre le code qui instancie correctement `Rune` des instances, car l’entrée représente des valeurs scalaires valides :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-190">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="c1ea6-191">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetValid" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="c1ea6-192">L’exemple suivant lève une exception, car le point de code se trouve dans la plage de substitution et ne fait pas partie d’une paire de substitution :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="c1ea6-193">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetInvalidSurrogate" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="c1ea6-194">L’exemple suivant lève une exception, car le point de code est au-delà de la plage supplémentaire :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="c1ea6-195">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/instanciation Rune s.cs" ID = "SnippetInvalidHigh" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="c1ea6-196">Rune exemple d’utilisation : modification de la casse des lettres</span><span class="sxs-lookup"><span data-stu-id="c1ea6-196">Rune usage example: changing letter case</span></span>

<span data-ttu-id="c1ea6-197">Une API qui prend un `char` et suppose qu’elle utilise un point de code qui est une valeur scalaire ne fonctionne pas correctement si le `char` est issu d’une paire de substitution.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-197">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="c1ea6-198">Par exemple, considérez la méthode suivante qui appelle <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> sur chaque char dans un string :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

<span data-ttu-id="c1ea6-199">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/ConvertToUpper. cs" ID = "SnippetBadExample" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="c1ea6-200">Si `input` string contient la lettre de Deseret minuscules `er` ( `𐑉` ), ce code ne le convertit pas en majuscules ( `𐐡` ).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-200">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="c1ea6-201">Le code appelle `char.ToUpperInvariant` séparément sur chaque point de code de substitution, `U+D801` et `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-201">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="c1ea6-202">Mais `U+D801` ne dispose pas d’informations suffisantes pour l’identifier comme une lettre minuscule `char.ToUpperInvariant` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="c1ea6-203">Et il gère `U+DC49` de la même façon.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="c1ea6-204">Le résultat est que les minuscules « 𐑉 » dans le `input` string ne sont pas converties en majuscules « 𐑉 ».</span><span class="sxs-lookup"><span data-stu-id="c1ea6-204">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="c1ea6-205">Voici deux options pour convertir correctement un string en majuscules :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-205">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="c1ea6-206">Appelez <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> sur l’entrée string plutôt que d’effectuer `char` une itération par `char` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="c1ea6-207">La `string.ToUpperInvariant` méthode a accès aux deux parties de chaque paire de substitution. elle peut donc gérer correctement tous les points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-207">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="c1ea6-208">Itérez au sein des valeurs scalaires Unicode en tant qu’instances plutôt qu’en tant `Rune` `char` qu’instances, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-208">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="c1ea6-209">Comme une `Rune` instance est une valeur scalaire Unicode valide, elle peut être passée à des API qui s’attendent à fonctionner sur une valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-209">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="c1ea6-210">Par exemple, l’appel de <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant donne des résultats corrects :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-210">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="c1ea6-211">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/ConvertToUpper. cs" ID = "SnippetGoodExample" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="c1ea6-212">Autres Rune API</span><span class="sxs-lookup"><span data-stu-id="c1ea6-212">Other Rune APIs</span></span>

<span data-ttu-id="c1ea6-213">Le `Rune` type expose des analogies de nombreuses `char` API.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-213">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="c1ea6-214">Par exemple, les méthodes suivantes reflètent les API statiques sur le `char` type :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-214">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="c1ea6-215">Pour obtenir la valeur scalaire brute d’une `Rune` instance, utilisez la <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-215">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="c1ea6-216">Pour reconvertir une `Rune` instance en une séquence de `char` , utilisez <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> ou la <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-216">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c1ea6-217">Étant donné que toute valeur scalaire Unicode `char` peut être représentée par un unique ou par une paire de substitution, toute `Rune` instance peut être représentée par au plus 2 `char` instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-217">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="c1ea6-218">Utilisez <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> pour voir le nombre d' `char` instances nécessaires pour représenter une `Rune` instance.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="c1ea6-219">Pour plus d’informations sur le `Rune` type .net, consultez la référence de l' [ `Rune` API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-219">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="c1ea6-220">Clusters graphèmes</span><span class="sxs-lookup"><span data-stu-id="c1ea6-220">Grapheme clusters</span></span>

<span data-ttu-id="c1ea6-221">Comme un char acter peut résulter d’une combinaison de plusieurs points de code, un terme plus descriptif, souvent utilisé à la place de « char acter », est le [cluster graphèmes](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-221">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="c1ea6-222">Le terme équivalent dans .NET est l' [élément de texte](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="c1ea6-223">Examinez les `string` instances « a », « á », « á » et « `👩🏽‍🚒` ».</span><span class="sxs-lookup"><span data-stu-id="c1ea6-223">Consider the `string` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="c1ea6-224">Si votre système d’exploitation les gère comme spécifié par la norme Unicode, chacune de ces `string` instances apparaît sous la forme d’un seul élément de texte ou d’un seul cluster graphèmes.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-224">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="c1ea6-225">Toutefois, les deux derniers sont représentés par plusieurs points de code de valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="c1ea6-226">Le string « a » est représenté par une valeur scalaire et contient une `char` instance.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-226">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="c1ea6-227">Le string « á » est représenté par une valeur scalaire et contient une `char` instance.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-227">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="c1ea6-228">Le string « á » ressemble à « á », mais il est représenté par deux valeurs scalaires et contient `char` deux instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-228">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="c1ea6-229">Enfin, le string « `👩🏽‍🚒` » est représenté par quatre valeurs scalaires et contient sept `char` instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-229">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="c1ea6-230">`U+1F469 WOMAN` (plage supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="c1ea6-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (plage supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="c1ea6-232">`U+1F692 FIRE ENGINE` (plage supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="c1ea6-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="c1ea6-233">Dans certains des exemples précédents, tels que le modificateur d’accent ou le modificateur de tonalité de la peau, le point de code ne s’affiche pas en tant qu’élément autonome à l’écran.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="c1ea6-234">Au lieu de cela, elle permet de modifier l’apparence d’un élément de texte qui précède.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="c1ea6-235">Ces exemples montrent qu’il peut prendre plusieurs valeurs scalaires pour créer ce que nous considérons comme un seul char cluster « acter » ou « graphèmes ».</span><span class="sxs-lookup"><span data-stu-id="c1ea6-235">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="c1ea6-236">Pour énumérer les clusters graphèmes d’un `string` , utilisez la <xref:System.Globalization.StringInfo> classe comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-236">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="c1ea6-237">Si vous êtes familiarisé avec SWIFT, le `StringInfo` type .net est conceptuellement similaire au [ `character` type SWIFT](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="c1ea6-238">Exemple : char instances d' Rune éléments de texte Count, et</span><span class="sxs-lookup"><span data-stu-id="c1ea6-238">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="c1ea6-239">Dans les API .NET, un cluster graphèmes est appelé un *élément de texte*.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="c1ea6-240">La méthode suivante montre les différences entre `char` les `Rune` instances d’élément de texte, et dans un `string` :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-240">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

<span data-ttu-id="c1ea6-241">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/CountTextElements. cs" ID = "SnippetCountMethod" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="c1ea6-242">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/CountTextElements. cs" ID = "SnippetCallCountMethod" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="c1ea6-243">Si vous exécutez ce code dans .NET Framework ou .NET Core 3,1 ou une version antérieure, le nombre d’éléments de texte pour l’Emoji s’affiche `4` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="c1ea6-244">Cela est dû à un bogue dans la `StringInfo` classe qui est résolu dans .net 5.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="c1ea6-245">Exemple : fractionnement d' string instances</span><span class="sxs-lookup"><span data-stu-id="c1ea6-245">Example: splitting string instances</span></span>

<span data-ttu-id="c1ea6-246">Lors du fractionnement `string` des instances, évitez de fractionner les paires de substitution et les clusters graphèmes.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-246">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="c1ea6-247">Prenons l’exemple suivant de code incorrect, qui envisage d’insérer des sauts de ligne tous les 10 char acters dans un string :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

<span data-ttu-id="c1ea6-248">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/InsertNewlines. cs" ID = "SnippetBadExample" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="c1ea6-249">Étant donné que ce code énumère `char` les instances, une paire de substitution qui se trouve sur un chevauchement de 10 `char` limites est fractionnée et un saut de ligne est injecté entre eux.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-249">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="c1ea6-250">Cette insertion introduit une altération des données, car les points de code de substitution sont significatifs uniquement en tant que paires.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="c1ea6-251">Le risque d’altération des données n’est pas éliminé si vous énumérez `Rune` des instances (valeurs scalaires) au lieu d' `char` instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-251">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="c1ea6-252">Un ensemble d' `Rune` instances peut créer un cluster graphèmes qui chevauche 10 `char` limites.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-252">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="c1ea6-253">Si le jeu de clusters graphèmes est fractionné, il ne peut pas être interprété correctement.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="c1ea6-254">Une meilleure approche consiste à rompre le string en comptant les clusters graphèmes ou les éléments de texte, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-254">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="c1ea6-255">::: code Language = "CSharp" source = "extraits/ char acter-Encoding-Introduction/CSharp/InsertNewlines. cs" ID = "SnippetGoodExample" :::</span><span class="sxs-lookup"><span data-stu-id="c1ea6-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="c1ea6-256">Comme indiqué précédemment, toutefois, dans les implémentations de .NET autres que .NET 5, la `StringInfo` classe peut gérer des clusters graphèmes de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="c1ea6-257">UTF-8 et UTF-32</span><span class="sxs-lookup"><span data-stu-id="c1ea6-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="c1ea6-258">Les sections précédentes sont axées sur UTF-16, car c’est ce que .NET utilise pour encoder des `string` instances.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="c1ea6-259">Il existe d’autres systèmes d’encodage pour Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) et [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="c1ea6-260">Ces encodages utilisent des unités de code 8 bits et des unités de code 32 bits, respectivement.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="c1ea6-261">Comme UTF-16, UTF-8 requiert que plusieurs unités de code représentent des valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="c1ea6-262">UTF-32 peut représenter n’importe quelle valeur scalaire dans une seule unité de code 32 bits.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="c1ea6-263">Voici quelques exemples montrant comment le même point de code Unicode est représenté dans chacun de ces trois systèmes d’encodage Unicode :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="c1ea6-264">Comme indiqué précédemment, une seule unité de code UTF-16 d’une [paire de substitution](#surrogate-pairs) n’est pas significative.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="c1ea6-265">De la même façon, une seule unité de code UTF-8 n’a pas de sens pour elle-même si elle se trouve dans une séquence de deux, trois ou quatre utilisées pour calculer une valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="c1ea6-266">Endianness</span><span class="sxs-lookup"><span data-stu-id="c1ea6-266">Endianness</span></span>

<span data-ttu-id="c1ea6-267">Dans .NET, les unités de code UTF-16 d’un string sont stockées dans une mémoire contiguë sous la forme d’une séquence d’entiers 16 bits ( `char` instances).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-267">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="c1ea6-268">Les bits des unités de code individuelles sont disposés selon le [endianness](https://en.wikipedia.org/wiki/Endianness) de l’architecture actuelle.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="c1ea6-269">Sur une architecture avec primauté des octets de poids faible, les string points de code UTF-16 `[ D801 DCCC ]` sont disposés en mémoire comme octets `[ 0x01, 0xD8, 0xCC, 0xDC ]` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-269">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="c1ea6-270">Sur une architecture avec primauté des octets de poids fort (Big-endian), string elle serait présentée en mémoire comme octets `[ 0xD8, 0x01, 0xDC, 0xCC ]` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-270">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="c1ea6-271">Les systèmes informatiques qui communiquent entre eux doivent s’accorder sur la représentation des données qui transitent par le réseau.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="c1ea6-272">La plupart des protocoles réseau utilisent UTF-8 comme norme lors de la transmission de texte, en partie afin d’éviter les problèmes qui peuvent résulter d’une machine à Big-endian communiquant avec un ordinateur Little-endian.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="c1ea6-273">Le string composé des points de code UTF-8 `[ F0 90 93 8C ]` est toujours représenté sous la forme d’octets `[ 0xF0, 0x90, 0x93, 0x8C ]` , quel que soit le endianness.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-273">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="c1ea6-274">Pour utiliser UTF-8 pour transmettre du texte, les applications .NET utilisent souvent du code similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="c1ea6-275">Dans l’exemple précédent, la méthode [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) décode le UTF-16 `string` en une série de valeurs scalaires Unicode, puis Recode ces valeurs scalaires en UTF-8 et place la séquence résultante dans un `byte` tableau.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="c1ea6-276">L' [encodage de méthode. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) effectue la transformation inverse, en convertissant un tableau UTF-8 `byte` en UTF-16 `string` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="c1ea6-277">Étant donné qu’UTF-8 est courant sur Internet, il peut être tentant de lire des octets bruts à partir du câble et de traiter les données comme s’il s’agissait d’UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="c1ea6-278">Toutefois, vous devez vérifier qu’il est bien formé.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="c1ea6-279">Un client malveillant peut soumettre un UTF-8 incorrect à votre service.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="c1ea6-280">Si vous opérez sur ces données comme si elles étaient correctement formées, cela peut entraîner des erreurs ou des failles de sécurité dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="c1ea6-281">Pour valider des données UTF-8, vous pouvez utiliser une méthode comme `Encoding.UTF8.GetString` , qui effectuera la validation lors de la conversion des données entrantes en `string` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="c1ea6-282">Encodage bien formé</span><span class="sxs-lookup"><span data-stu-id="c1ea6-282">Well-formed encoding</span></span>

<span data-ttu-id="c1ea6-283">Un encodage Unicode bien formé est un string d’unités de code qui peuvent être décodées sans ambiguïté et sans erreur dans une séquence de valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-283">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="c1ea6-284">Les données correctement formées peuvent être transcodées librement entre UTF-8, UTF-16 et UTF-32.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="c1ea6-285">La question de savoir si une séquence d’encodage est correctement formée ou non n’est pas liée à l’endianness de l’architecture d’une machine.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="c1ea6-286">Une séquence UTF-8 incorrecte est incorrecte de la même façon sur les ordinateurs Big-endian et Little-endian.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="c1ea6-287">Voici quelques exemples de codages incorrects :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="c1ea6-288">En UTF-8, la séquence `[ 6C C2 61 ]` est incorrecte car `C2` ne peut pas être suivi de `61` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="c1ea6-289">En UTF-16, la séquence `[ DC00 DD00 ]` (ou, en C#,) est incorrecte string `"\udc00\udd00"` , car le substitut faible `DC00` ne peut pas être suivi d’un autre substitut faible `DD00` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="c1ea6-290">En UTF-32, la séquence `[ 0011ABCD ]` est incorrecte car `0011ABCD` est en dehors de la plage de valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="c1ea6-291">Dans .NET, les `string` instances contiennent presque toujours des données UTF-16 bien formées, mais cela n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-291">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="c1ea6-292">Les exemples suivants illustrent du code C# valide qui crée des données UTF-16 incorrectes dans des `string` instances de.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="c1ea6-293">Littéral incorrect :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-293">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="c1ea6-294">Un Sub string qui divise une paire de substitution :</span><span class="sxs-lookup"><span data-stu-id="c1ea6-294">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="c1ea6-295">Les API telles que [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) ne retournent jamais des instances mal formées `string` .</span><span class="sxs-lookup"><span data-stu-id="c1ea6-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="c1ea6-296">`Encoding.GetString``Encoding.GetBytes`les méthodes et détectent les séquences incorrectes dans l’entrée et effectuent une char substitution acter lors de la génération de la sortie.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="c1ea6-297">Par exemple, si [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) détecte un octet non-ASCII dans l’entrée (en dehors de la plage u + 0000.. U + 007F), il insère un «  ? » dans l' `string` instance retournée.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="c1ea6-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) remplace les séquences UTF-8 incorrectes par `U+FFFD REPLACEMENT CHARACTER ('�')` dans l' `string` instance retournée.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="c1ea6-299">Pour plus d’informations, consultez [la norme Unicode](https://www.unicode.org/versions/latest/), sections 5,22 et 3,9.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="c1ea6-300">Les `Encoding` classes intégrées peuvent également être configurées pour lever une exception au lieu d’effectuer une char substitution acter quand des séquences incorrectes sont affichées.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="c1ea6-301">Cette approche est souvent utilisée dans les applications sensibles à la sécurité où la char substitution de acter peut ne pas être acceptable.</span><span class="sxs-lookup"><span data-stu-id="c1ea6-301">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="c1ea6-302">Pour plus d’informations sur l’utilisation des classes intégrées `Encoding` , consultez Guide pratique [pour utiliser char des classes d’encodage acter dans .net](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="c1ea6-302">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ea6-303">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1ea6-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="c1ea6-304">Globalisation et localisation</span><span class="sxs-lookup"><span data-stu-id="c1ea6-304">Globalization and Localization</span></span>](../globalization-localization/index.md)
