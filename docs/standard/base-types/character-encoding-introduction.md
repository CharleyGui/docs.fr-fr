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
# <a name="character-encoding-in-net"></a><span data-ttu-id="9e85a-103">Encodage de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="9e85a-103">Character encoding in .NET</span></span>

<span data-ttu-id="9e85a-104">Cet article fournit une introduction aux systèmes d’encodage de caractère qui sont utilisés par .NET.</span><span class="sxs-lookup"><span data-stu-id="9e85a-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="9e85a-105">L’article explique <xref:System.String> <xref:System.Char>comment <xref:System.Text.Rune>le <xref:System.Globalization.StringInfo> , , et les types de travail avec Unicode, UTF-16, et UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9e85a-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="9e85a-106">Le *terme caractère* est utilisé ici dans le sens général de *ce qu’un lecteur perçoit comme un seul élément d’affichage*.</span><span class="sxs-lookup"><span data-stu-id="9e85a-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="9e85a-107">Les exemples courants sont la lettre " a🐂", le symbole " et l’emoji " "</span><span class="sxs-lookup"><span data-stu-id="9e85a-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="9e85a-108">Parfois, ce qui ressemble à un personnage est en fait composé de plusieurs éléments d’affichage indépendants, comme l’explique la section sur [les clusters de grapheme.](#grapheme-clusters)</span><span class="sxs-lookup"><span data-stu-id="9e85a-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="9e85a-109">Les types de cordes et d’ombles</span><span class="sxs-lookup"><span data-stu-id="9e85a-109">The string and char types</span></span>

<span data-ttu-id="9e85a-110">Une instance de la classe [de cordes](xref:System.String) représente un texte.</span><span class="sxs-lookup"><span data-stu-id="9e85a-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="9e85a-111">A `string` est logiquement une séquence de valeurs 16 bits, dont chacune est un exemple de la struction de [l’omble chevalier.](xref:System.Char)</span><span class="sxs-lookup"><span data-stu-id="9e85a-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="9e85a-112">La [ficelle. La](xref:System.String.Length) propriété de `char` longueur renvoie le nombre de cas dans l’exemple. `string`</span><span class="sxs-lookup"><span data-stu-id="9e85a-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="9e85a-113">La fonction d’échantillon suivante imprime les valeurs dans `char` la `string`notation hexadecimale de tous les cas dans un :</span><span class="sxs-lookup"><span data-stu-id="9e85a-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="9e85a-114">Passez la chaîne "Bonjour" à cette fonction, et vous obtenez la sortie suivante:</span><span class="sxs-lookup"><span data-stu-id="9e85a-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="9e85a-115">Chaque personnage est représenté `char` par une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="9e85a-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="9e85a-116">Ce modèle est vrai pour la plupart des langues du monde.</span><span class="sxs-lookup"><span data-stu-id="9e85a-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="9e85a-117">Par exemple, voici la sortie de deux personnages chinois qui sonnent comme *nô hôo* et *signifie*bonjour:</span><span class="sxs-lookup"><span data-stu-id="9e85a-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="9e85a-118">Cependant, pour certaines langues et pour certains `char` symboles et emoji, il faut deux instances pour représenter un seul personnage.</span><span class="sxs-lookup"><span data-stu-id="9e85a-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="9e85a-119">Par exemple, comparez `char` les caractères et les instances dans le mot qui signifie *Osage* dans la langue Osage :</span><span class="sxs-lookup"><span data-stu-id="9e85a-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="9e85a-120">Dans l’exemple précédent, chaque personnage, à `char` l’exception de l’espace, est représenté par deux instances.</span><span class="sxs-lookup"><span data-stu-id="9e85a-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="9e85a-121">Un seul emoji Unicode est `char`également représenté par deux s, comme on le voit dans l’exemple suivant montrant un emoji de bœuf:</span><span class="sxs-lookup"><span data-stu-id="9e85a-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="9e85a-122">Ces exemples montrent `string.Length`que la valeur `char` de , qui indique le nombre de cas, n’indique pas nécessairement le nombre de caractères affichés.</span><span class="sxs-lookup"><span data-stu-id="9e85a-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="9e85a-123">Une `char` seule instance en soi ne représente pas nécessairement un personnage.</span><span class="sxs-lookup"><span data-stu-id="9e85a-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="9e85a-124">Les `char` paires qui cartographient à un seul caractère sont appelés *paires de substitution*.</span><span class="sxs-lookup"><span data-stu-id="9e85a-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="9e85a-125">Pour comprendre comment ils fonctionnent, vous devez comprendre Unicode et UTF-16 codage.</span><span class="sxs-lookup"><span data-stu-id="9e85a-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="9e85a-126">Points de code Unicode</span><span class="sxs-lookup"><span data-stu-id="9e85a-126">Unicode code points</span></span>

<span data-ttu-id="9e85a-127">Unicode est une norme internationale d’encodage pour une utilisation sur diverses plates-formes et avec différentes langues et scripts.</span><span class="sxs-lookup"><span data-stu-id="9e85a-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="9e85a-128">L’Unicode Standard définit plus de 1,1 million de [points de code](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="9e85a-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="9e85a-129">Un point de code est une valeur d’intégrant qui peut varier de 0 à `U+10FFFF` (décimale 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="9e85a-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="9e85a-130">Certains points de code sont attribués à des lettres, des symboles ou des emoji.</span><span class="sxs-lookup"><span data-stu-id="9e85a-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="9e85a-131">D’autres sont affectés à des actions qui contrôlent la façon dont le texte ou les caractères sont affichés, comme l’avance à une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="9e85a-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="9e85a-132">De nombreux points de code ne sont pas encore attribués.</span><span class="sxs-lookup"><span data-stu-id="9e85a-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="9e85a-133">Voici quelques exemples d’affectations de points de code, avec des liens vers des graphiques Unicode dans lesquels ils apparaissent:</span><span class="sxs-lookup"><span data-stu-id="9e85a-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="9e85a-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="9e85a-134">Decimal</span></span>|<span data-ttu-id="9e85a-135">Hex</span><span class="sxs-lookup"><span data-stu-id="9e85a-135">Hex</span></span>       |<span data-ttu-id="9e85a-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e85a-136">Example</span></span>|<span data-ttu-id="9e85a-137">Description</span><span class="sxs-lookup"><span data-stu-id="9e85a-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="9e85a-138">10</span><span class="sxs-lookup"><span data-stu-id="9e85a-138">10</span></span>     | `U+000A` |<span data-ttu-id="9e85a-139">N/A</span><span class="sxs-lookup"><span data-stu-id="9e85a-139">N/A</span></span>| [<span data-ttu-id="9e85a-140">LIGNE FEED</span><span class="sxs-lookup"><span data-stu-id="9e85a-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="9e85a-141">65</span><span class="sxs-lookup"><span data-stu-id="9e85a-141">65</span></span>     | `U+0061` | <span data-ttu-id="9e85a-142">a</span><span class="sxs-lookup"><span data-stu-id="9e85a-142">a</span></span> | [<span data-ttu-id="9e85a-143">PETITE LETTRE LATINE A</span><span class="sxs-lookup"><span data-stu-id="9e85a-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="9e85a-144">562</span><span class="sxs-lookup"><span data-stu-id="9e85a-144">562</span></span>    | `U+0232` | <span data-ttu-id="9e85a-145">1er</span><span class="sxs-lookup"><span data-stu-id="9e85a-145">Ȳ</span></span> | [<span data-ttu-id="9e85a-146">LETTRE DE LA CAPITALE LATINE Y AVEC MACRON</span><span class="sxs-lookup"><span data-stu-id="9e85a-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="9e85a-147">68,675</span><span class="sxs-lookup"><span data-stu-id="9e85a-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="9e85a-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="9e85a-148">𐱃</span></span> | [<span data-ttu-id="9e85a-149">VIEILLE LETTRE TURQUE ORKHON À</span><span class="sxs-lookup"><span data-stu-id="9e85a-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="9e85a-150">127,801</span><span class="sxs-lookup"><span data-stu-id="9e85a-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="9e85a-151">🌹</span><span class="sxs-lookup"><span data-stu-id="9e85a-151">🌹</span></span> | [<span data-ttu-id="9e85a-152">EMOJI ROSE</span><span class="sxs-lookup"><span data-stu-id="9e85a-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="9e85a-153">Les points de code sont habituellement mentionnés `U+xxxx`en `xxxx` utilisant la syntaxe , où est la valeur integer encodé hex.</span><span class="sxs-lookup"><span data-stu-id="9e85a-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="9e85a-154">Dans toute la gamme des points de code il y a deux sous-gammes :</span><span class="sxs-lookup"><span data-stu-id="9e85a-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="9e85a-155">Le **plan multilingue de base (BMP)** dans la gamme `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="9e85a-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="9e85a-156">Cette gamme 16 bits fournit 65 536 points de code, assez pour couvrir la majorité des systèmes d’écriture du monde.</span><span class="sxs-lookup"><span data-stu-id="9e85a-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="9e85a-157">**Points de code** `U+10000..U+10FFFF`supplémentaires dans la plage .</span><span class="sxs-lookup"><span data-stu-id="9e85a-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="9e85a-158">Cette gamme 21 bits fournit plus d’un million de points de code supplémentaires qui peuvent être utilisés pour des langues moins connues et d’autres fins telles que les emojis.</span><span class="sxs-lookup"><span data-stu-id="9e85a-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="9e85a-159">Le diagramme suivant illustre la relation entre le BMP et les points de code supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9e85a-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP et points de code supplémentaires":::

## <a name="utf-16-code-units"></a><span data-ttu-id="9e85a-161">Unités de code UTF-16</span><span class="sxs-lookup"><span data-stu-id="9e85a-161">UTF-16 code units</span></span>

<span data-ttu-id="9e85a-162">16 bits Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) est un système de codage de caractère qui utilise des unités de code 16 *bits* pour représenter les points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="9e85a-163">.NET utilise UTF-16 pour coder `string`le texte dans un .</span><span class="sxs-lookup"><span data-stu-id="9e85a-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="9e85a-164">Une `char` instance représente une unité de code 16 bits.</span><span class="sxs-lookup"><span data-stu-id="9e85a-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="9e85a-165">Une seule unité de code 16 bits peut représenter n’importe quel point de code dans la gamme 16 bits de l’avion multilingue de base.</span><span class="sxs-lookup"><span data-stu-id="9e85a-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="9e85a-166">Mais pour un point de code `char` dans la plage supplémentaire, deux instances sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="9e85a-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="9e85a-167">Paires de substitution</span><span class="sxs-lookup"><span data-stu-id="9e85a-167">Surrogate pairs</span></span>

<span data-ttu-id="9e85a-168">La traduction de deux valeurs 16 bits à une seule valeur 21 bits est `U+D800` `U+DFFF` facilitée par une gamme spéciale appelée les points de code de *substitution*, de (décimale 55 296 à 57 343), inclusivement.</span><span class="sxs-lookup"><span data-stu-id="9e85a-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="9e85a-169">Le diagramme suivant illustre la relation entre le BMP et les points de code de substitution.</span><span class="sxs-lookup"><span data-stu-id="9e85a-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="Points de code BMP et de substitution":::

<span data-ttu-id="9e85a-171">Lorsqu’un point de`U+D800..U+DBFF`code de substitution *élevé* (`U+DC00..U+DFFF`) est immédiatement suivi d’un faible point de code de *substitution* (), la paire est interprétée comme un point de code supplémentaire en utilisant la formule suivante:</span><span class="sxs-lookup"><span data-stu-id="9e85a-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="9e85a-172">Voici la même formule à l’aide de la notation décimale :</span><span class="sxs-lookup"><span data-stu-id="9e85a-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="9e85a-173">Un point de code de substitution *élevé* n’a pas une valeur de nombre plus élevée qu’un point de code de substitution *faible.*</span><span class="sxs-lookup"><span data-stu-id="9e85a-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="9e85a-174">Le point de code de substitution élevé est appelé «élevé» parce qu’il est utilisé pour calculer l’ordre supérieur 11 bits de la gamme complète de points de code 21 bits.</span><span class="sxs-lookup"><span data-stu-id="9e85a-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="9e85a-175">Le point de code de substitution faible est utilisé pour calculer l’ordre inférieur 10 bits.</span><span class="sxs-lookup"><span data-stu-id="9e85a-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="9e85a-176">Par exemple, le point de code réel `0xD83C` `0xDF39` qui correspond à la paire de substitution et est calculé comme suit:</span><span class="sxs-lookup"><span data-stu-id="9e85a-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="9e85a-177">Voici le même calcul à l’aide de la notation décimale :</span><span class="sxs-lookup"><span data-stu-id="9e85a-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="9e85a-178">L’exemple précédent `"\ud83c\udf39"` démontre qu’il s’agit de `U+1F339 ROSE ('🌹')` l’encodage UTF-16 du point de code mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="9e85a-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="9e85a-179">Valeurs scalaires Unicode</span><span class="sxs-lookup"><span data-stu-id="9e85a-179">Unicode scalar values</span></span>

<span data-ttu-id="9e85a-180">Le terme [valeur scalaire Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) se réfère à tous les points de code autres que les points de code de substitution.</span><span class="sxs-lookup"><span data-stu-id="9e85a-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="9e85a-181">En d’autres termes, une valeur scalaire est n’importe quel point de code qui est attribué à un personnage ou peut être attribué un personnage à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="9e85a-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="9e85a-182">"Caractère" se réfère ici à tout ce qui peut être attribué à un point de code, qui comprend des choses telles que les actions qui contrôlent la façon dont le texte ou les caractères sont affichés.</span><span class="sxs-lookup"><span data-stu-id="9e85a-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="9e85a-183">Le diagramme suivant illustre les points de code de valeur scalaires.</span><span class="sxs-lookup"><span data-stu-id="9e85a-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Valeurs scalaires":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="9e85a-185">Le Rune type comme valeur scalaire</span><span class="sxs-lookup"><span data-stu-id="9e85a-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="9e85a-186">Commençant par .NET Core 3.0, le <xref:System.Text.Rune?displayProperty=fullName> type représente une valeur scalaire Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="9e85a-187">**`Rune`n’est pas disponible en .NET Core 2.x ou .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="9e85a-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="9e85a-188">Les `Rune` constructeurs valident que l’instance résultante est une valeur scalaire Unicode valide, sinon ils jettent une exception.</span><span class="sxs-lookup"><span data-stu-id="9e85a-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="9e85a-189">L’exemple suivant montre le `Rune` code qui instantané les instances avec succès parce que l’entrée représente des valeurs scalaires valides :</span><span class="sxs-lookup"><span data-stu-id="9e85a-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="9e85a-190">L’exemple suivant jette une exception parce que le point de code est dans la plage de substitution et ne fait pas partie d’une paire de substitution:</span><span class="sxs-lookup"><span data-stu-id="9e85a-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="9e85a-191">L’exemple suivant jette une exception parce que le point de code est au-delà de la plage supplémentaire:</span><span class="sxs-lookup"><span data-stu-id="9e85a-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="9e85a-192">exemple d’utilisation : cas de lettre changeant</span><span class="sxs-lookup"><span data-stu-id="9e85a-192"> usage example: changing letter case</span></span>

<span data-ttu-id="9e85a-193">Une API qui `char` prend un et suppose qu’il travaille avec un point de code `char` qui est une valeur scalaire ne fonctionne pas correctement si le est d’une paire de substitution.</span><span class="sxs-lookup"><span data-stu-id="9e85a-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="9e85a-194">Par exemple, considérez la <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> méthode char suivante stringqui fait appel à chacune d’une</span><span class="sxs-lookup"><span data-stu-id="9e85a-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="9e85a-195">Si `input` string le contient la lettre `er` de`𐑉`Deseret minuscule ( ), ce code`𐐡`ne la convertira pas en uppercase ().</span><span class="sxs-lookup"><span data-stu-id="9e85a-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="9e85a-196">Le code `char.ToUpperInvariant` appelle séparément sur `U+D801` chaque `U+DC49`point de code de substitution, et .</span><span class="sxs-lookup"><span data-stu-id="9e85a-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="9e85a-197">Mais `U+D801` n’a pas assez d’informations par lui-même `char.ToUpperInvariant` pour l’identifier comme une lettre minuscule, laisse donc seul.</span><span class="sxs-lookup"><span data-stu-id="9e85a-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="9e85a-198">Et il `U+DC49` gère de la même façon.</span><span class="sxs-lookup"><span data-stu-id="9e85a-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="9e85a-199">Le résultat est que lowercase ''dans le `input` string ne se convertit pas en uppercase ''.</span><span class="sxs-lookup"><span data-stu-id="9e85a-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="9e85a-200">Voici deux options pour convertir string correctement un uppercase :</span><span class="sxs-lookup"><span data-stu-id="9e85a-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="9e85a-201">Faites <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> appel string à l’entrée `char`plutôt`char`qu’à itérer - par- .</span><span class="sxs-lookup"><span data-stu-id="9e85a-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="9e85a-202">La `string.ToUpperInvariant` méthode a accès aux deux parties de chaque paire de substitution, de sorte qu’il peut gérer tous les points de code Unicode correctement.</span><span class="sxs-lookup"><span data-stu-id="9e85a-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="9e85a-203">Itérer à travers les valeurs scalaires Unicode comme `Rune` instances au lieu d’instances, `char` comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9e85a-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="9e85a-204">Étant `Rune` donné qu’une instance est une valeur scalaire Unicode valide, elle peut être transmise aux API qui s’attendent à fonctionner sur une valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="9e85a-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="9e85a-205">Par exemple, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> l’appel tel qu’il est indiqué dans l’exemple suivant donne des résultats corrects :</span><span class="sxs-lookup"><span data-stu-id="9e85a-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="9e85a-206">Autres Rune API</span><span class="sxs-lookup"><span data-stu-id="9e85a-206">Other Rune APIs</span></span>

<span data-ttu-id="9e85a-207">Le `Rune` type expose les analogues `char` de la plupart des API.</span><span class="sxs-lookup"><span data-stu-id="9e85a-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="9e85a-208">Par exemple, les méthodes suivantes reflètent `char` les API statiques sur le type :</span><span class="sxs-lookup"><span data-stu-id="9e85a-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="9e85a-209">Pour obtenir la valeur scalaire brute `Rune` <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> d’une instance, utilisez la propriété.</span><span class="sxs-lookup"><span data-stu-id="9e85a-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="9e85a-210">Pour convertir `Rune` une instance en `char`une <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> séquence <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> de s, utilisez ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9e85a-211">Étant donné que toute valeur scalaire `char` Unicode est représentée `Rune` par une seule ou par `char` une paire de substitution, n’importe quelle instance peut être représentée par au plus deux cas.</span><span class="sxs-lookup"><span data-stu-id="9e85a-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="9e85a-212">Utilisez <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> pour voir `char` combien d’instances `Rune` sont nécessaires pour représenter une instance.</span><span class="sxs-lookup"><span data-stu-id="9e85a-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="9e85a-213">Pour plus d’informations `Rune` sur le type .NET, voir la [ `Rune` référence API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="9e85a-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="9e85a-214">Clusters Grapheme</span><span class="sxs-lookup"><span data-stu-id="9e85a-214">Grapheme clusters</span></span>

<span data-ttu-id="9e85a-215">Ce qui ressemble à un personnage pourrait résulter d’une combinaison de plusieurs points de code, de sorte qu’un terme plus descriptif qui est souvent utilisé à la place de "caractère" est [cluster grapheme](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="9e85a-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="9e85a-216">Le terme équivalent en .NET est [élément texte](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="9e85a-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="9e85a-217">Considérez `string` les instances comme « a », « ô ».</span><span class="sxs-lookup"><span data-stu-id="9e85a-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="9e85a-218">"ô", et`👩🏽‍🚒`".</span><span class="sxs-lookup"><span data-stu-id="9e85a-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="9e85a-219">Si votre système d’exploitation les gère comme le `string` précise la norme Unicode, chacun de ces instances apparaît sous forme d’un seul élément de texte ou d’un cluster graphique.</span><span class="sxs-lookup"><span data-stu-id="9e85a-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="9e85a-220">Mais les deux derniers sont représentés par plus d’un point de code de valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="9e85a-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="9e85a-221">Le string "a" est représenté par une valeur `char` scalaire et contient une instance.</span><span class="sxs-lookup"><span data-stu-id="9e85a-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="9e85a-222">Le string « ô » est représenté par une `char` valeur scalaire et contient un cas.</span><span class="sxs-lookup"><span data-stu-id="9e85a-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="9e85a-223">Le string « » ressemble à « ô » mais est représenté par deux `char` valeurs scalaires et contient deux instances.</span><span class="sxs-lookup"><span data-stu-id="9e85a-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="9e85a-224">Enfin, string le`👩🏽‍🚒`" " est représenté par quatre `char` valeurs scalaires et contient sept instances.</span><span class="sxs-lookup"><span data-stu-id="9e85a-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="9e85a-225">`U+1F469 WOMAN`(gamme supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="9e85a-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="9e85a-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(gamme supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="9e85a-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="9e85a-227">`U+1F692 FIRE ENGINE`(gamme supplémentaire, nécessite une paire de substitution)</span><span class="sxs-lookup"><span data-stu-id="9e85a-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="9e85a-228">Dans certains des exemples précédents - comme le modificateur d’accent combinant ou le modificateur de teint - le point de code ne s’affiche pas comme élément autonome sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="9e85a-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="9e85a-229">Il sert plutôt à modifier l’apparence d’un élément texte qui lui a été soumis.</span><span class="sxs-lookup"><span data-stu-id="9e85a-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="9e85a-230">Ces exemples montrent qu’il pourrait prendre plusieurs valeurs scalaires pour compenser ce que nous considérons comme un seul « caractère » ou « cluster de grapheme ».</span><span class="sxs-lookup"><span data-stu-id="9e85a-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="9e85a-231">Pour énumérer les grappes de `string`grapheme <xref:System.Globalization.StringInfo> d’un , utilisez la classe comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9e85a-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="9e85a-232">Si vous êtes familier avec Swift, le type .NET `StringInfo` est conceptuellement similaire au type de [ `character` Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="9e85a-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="9e85a-233">Exemple : char Runecompter , , et les instances d’élément de texte</span><span class="sxs-lookup"><span data-stu-id="9e85a-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="9e85a-234">Dans les API .NET, un cluster de grapheme est appelé *un élément de texte*.</span><span class="sxs-lookup"><span data-stu-id="9e85a-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="9e85a-235">La méthode suivante démontre les `char` `Rune`différences entre les instances `string`d’élément texte et les exemples d’élément texte dans un :</span><span class="sxs-lookup"><span data-stu-id="9e85a-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="9e85a-236">Si vous exécutez ce code dans .NET Framework ou .NET Core 3.1 ou plus tôt, le nombre d’éléments texte pour l’emoji montre `4`.</span><span class="sxs-lookup"><span data-stu-id="9e85a-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="9e85a-237">Cela est dû à `StringInfo` un bug dans la classe qui est fixé en .NET 5.</span><span class="sxs-lookup"><span data-stu-id="9e85a-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="9e85a-238">Exemple : string fractionnement des instances</span><span class="sxs-lookup"><span data-stu-id="9e85a-238">Example: splitting string instances</span></span>

<span data-ttu-id="9e85a-239">Lors `string` du fractionnement des instances, évitez de diviser les paires de substitution et les grappes de grapheme.</span><span class="sxs-lookup"><span data-stu-id="9e85a-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="9e85a-240">Prenons l’exemple suivant d’un code incorrect, qui a stringl’intention d’insérer des sauts de ligne tous les 10 caractères dans un :</span><span class="sxs-lookup"><span data-stu-id="9e85a-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="9e85a-241">Parce que ce code `char` énumère les instances, une paire de substitution`char` qui se trouve à chevaucher une limite de 10 sera divisée et une nouvelle ligne injectée entre eux.</span><span class="sxs-lookup"><span data-stu-id="9e85a-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="9e85a-242">Cette insertion introduit la corruption de données, parce que les points de code de substitution ne sont significatifs que comme paires.</span><span class="sxs-lookup"><span data-stu-id="9e85a-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="9e85a-243">Le risque de corruption des données n’est pas éliminé si vous énumérez `Rune` les instances (valeurs scalaires) au lieu d’instances. `char`</span><span class="sxs-lookup"><span data-stu-id="9e85a-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="9e85a-244">Un ensemble `Rune` d’instances peut constituer un cluster de grapheme`char` qui chevauche une limite de 10.</span><span class="sxs-lookup"><span data-stu-id="9e85a-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="9e85a-245">Si l’ensemble de cluster grapheme est divisé, il ne peut pas être interprété correctement.</span><span class="sxs-lookup"><span data-stu-id="9e85a-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="9e85a-246">Une meilleure approche consiste string à briser les clusters en comptant des clusters de grapheme, ou des éléments de texte, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9e85a-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="9e85a-247">Comme indiqué précédemment, cependant, dans les implémentations `StringInfo` de .NET autre que .NET 5, la classe pourrait gérer certains clusters de grapheme incorrectement.</span><span class="sxs-lookup"><span data-stu-id="9e85a-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="9e85a-248">UTF-8 et UTF-32</span><span class="sxs-lookup"><span data-stu-id="9e85a-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="9e85a-249">Les sections précédentes se sont concentrées sur UTF-16 `string` parce que c’est ce que .NET utilise pour coder les instances.</span><span class="sxs-lookup"><span data-stu-id="9e85a-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="9e85a-250">Il existe d’autres systèmes d’encodage pour Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) et [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="9e85a-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="9e85a-251">Ces codages utilisent des unités de code 8 bits et des unités de code 32 bits, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9e85a-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="9e85a-252">Comme UTF-16, UTF-8 nécessite plusieurs unités de code pour représenter certaines valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="9e85a-253">UTF-32 peut représenter n’importe quelle valeur scalaire dans une seule unité de code 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9e85a-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="9e85a-254">Voici quelques exemples montrant comment le même point de code Unicode est représenté dans chacun de ces trois systèmes d’encodage Unicode :</span><span class="sxs-lookup"><span data-stu-id="9e85a-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="9e85a-255">Comme indiqué précédemment, une seule unité de code UTF-16 d’une paire de [substitution](#surrogate-pairs) n’a aucun sens par lui-même.</span><span class="sxs-lookup"><span data-stu-id="9e85a-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="9e85a-256">De la même manière, une seule unité de code UTF-8 n’a pas de sens en soi si elle est dans une séquence de deux, trois ou quatre utilisés pour calculer une valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="9e85a-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="9e85a-257">Endianness</span><span class="sxs-lookup"><span data-stu-id="9e85a-257">Endianness</span></span>

<span data-ttu-id="9e85a-258">Dans .NET, les unités de code UTF-16 d’un string sont stockées dans la mémoire`char` contigu comme une séquence d’intégrateurs 16 bits (instances).</span><span class="sxs-lookup"><span data-stu-id="9e85a-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="9e85a-259">Les bits des unités de code individuelles sont disposés en fonction de [l’endianness](https://en.wikipedia.org/wiki/Endianness) de l’architecture actuelle.</span><span class="sxs-lookup"><span data-stu-id="9e85a-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="9e85a-260">Sur une architecture peu-endienne, le string composé des points `[ D801 DCCC ]` de code UTF-16 `[ 0x01, 0xD8, 0xCC, 0xDC ]`serait exposé en mémoire comme les octets .</span><span class="sxs-lookup"><span data-stu-id="9e85a-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="9e85a-261">Sur une architecture big-endian que la même string chose `[ 0xD8, 0x01, 0xDC, 0xCC ]`serait énoncée dans la mémoire que les octets .</span><span class="sxs-lookup"><span data-stu-id="9e85a-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="9e85a-262">Les systèmes informatiques qui communiquent entre eux doivent s’entendre sur la représentation des données traversant le fil.</span><span class="sxs-lookup"><span data-stu-id="9e85a-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="9e85a-263">La plupart des protocoles réseau utilisent UTF-8 comme norme lors de la transmission du texte, en partie pour éviter les problèmes qui pourraient résulter d’une machine big-endian communiquer avec une machine peu-endienne.</span><span class="sxs-lookup"><span data-stu-id="9e85a-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="9e85a-264">Les string points `[ F0 90 93 8C ]` de code UTF-8 seront toujours représentés `[ 0xF0, 0x90, 0x93, 0x8C ]` comme les octets indépendamment de l’endianness.</span><span class="sxs-lookup"><span data-stu-id="9e85a-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="9e85a-265">Pour utiliser UTF-8 pour la transmission de texte, les applications .NET utilisent souvent le code comme l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9e85a-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="9e85a-266">Dans l’exemple précédent, la méthode [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) décode `string` l’UTF-16 en une série de valeurs scalaires Unicode, puis il réencode ces `byte` valeurs scalaires en UTF-8 et place la séquence résultante dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="9e85a-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="9e85a-267">La méthode [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) effectue la transformation opposée, convertissant `byte` un tableau UTF-8 en utF-16 `string`.</span><span class="sxs-lookup"><span data-stu-id="9e85a-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="9e85a-268">Étant donné QUE l’UTF-8 est monnaie courante sur Internet, il peut être tentant de lire les octets bruts du fil et de traiter les données comme si c’était UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9e85a-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="9e85a-269">Cependant, vous devez valider qu’il est en effet bien formé.</span><span class="sxs-lookup"><span data-stu-id="9e85a-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="9e85a-270">Un client malveillant peut soumettre UTF-8 mal formé à votre service.</span><span class="sxs-lookup"><span data-stu-id="9e85a-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="9e85a-271">Si vous utilisez ces données comme si elles étaient bien formées, elles pourraient causer des erreurs ou des failles de sécurité dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9e85a-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="9e85a-272">Pour valider les données UTF-8, `Encoding.UTF8.GetString`vous pouvez utiliser une méthode comme `string`, qui effectuera la validation tout en convertissant les données entrantes en un .</span><span class="sxs-lookup"><span data-stu-id="9e85a-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="9e85a-273">Codage bien formé</span><span class="sxs-lookup"><span data-stu-id="9e85a-273">Well-formed encoding</span></span>

<span data-ttu-id="9e85a-274">Un codage Unicode bien string formé est une des unités de code qui peuvent être décodés sans ambiguïté et sans erreur dans une séquence de valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="9e85a-275">Les données bien formées peuvent être transcodées librement entre UTF-8, UTF-16 et UTF-32.</span><span class="sxs-lookup"><span data-stu-id="9e85a-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="9e85a-276">La question de savoir si une séquence d’encodage est bien formée ou non n’est pas liée à l’endianness de l’architecture d’une machine.</span><span class="sxs-lookup"><span data-stu-id="9e85a-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="9e85a-277">Une séquence UTF-8 mal formée est mal formée de la même manière sur les machines big-endian et little-endian.</span><span class="sxs-lookup"><span data-stu-id="9e85a-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="9e85a-278">Voici quelques exemples d’encodages mal formés :</span><span class="sxs-lookup"><span data-stu-id="9e85a-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="9e85a-279">Dans UTF-8, `[ 6C C2 61 ]` la séquence est `C2` mal formée `61`parce qu’elle ne peut pas être suivie par .</span><span class="sxs-lookup"><span data-stu-id="9e85a-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="9e85a-280">Dans UTF-16, `[ DC00 DD00 ]` la séquence (ou, string `"\udc00\udd00"`en C, le ) `DC00` est mal formée parce `DD00`que la mère porteuse faible ne peut pas être suivie par une autre faible mère porteuse .</span><span class="sxs-lookup"><span data-stu-id="9e85a-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="9e85a-281">Dans UTF-32, `[ 0011ABCD ]` la séquence est `0011ABCD` mal formée parce qu’elle est en dehors de la gamme des valeurs scalaires Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e85a-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="9e85a-282">Dans .NET, `string` les instances contiennent presque toujours des données UTF-16 bien formées, mais ce n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="9e85a-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="9e85a-283">Les exemples suivants montrent un code Cmd valide qui crée `string` des données UTF-16 mal formées dans les cas.</span><span class="sxs-lookup"><span data-stu-id="9e85a-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="9e85a-284">Un littéral mal formé:</span><span class="sxs-lookup"><span data-stu-id="9e85a-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="9e85a-285">Un sous-cordon qui divise une paire de substitution:</span><span class="sxs-lookup"><span data-stu-id="9e85a-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="9e85a-286">Les API comme [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) ne `string` reviennent jamais à des cas mal formés.</span><span class="sxs-lookup"><span data-stu-id="9e85a-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="9e85a-287">`Encoding.GetString`et `Encoding.GetBytes` les méthodes détectent les séquences mal formées dans l’entrée et effectuent la substitution de caractère lors de la génération de la sortie.</span><span class="sxs-lookup"><span data-stu-id="9e85a-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="9e85a-288">Par exemple, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) si l’on voit un byte non-ASCII dans l’entrée (en dehors de la plage U-0000..U-007F), il insère un «?» dans l’instance retournée. `string`</span><span class="sxs-lookup"><span data-stu-id="9e85a-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="9e85a-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)remplace les séquences UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` mal formées par dans l’instance retournée. `string`</span><span class="sxs-lookup"><span data-stu-id="9e85a-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="9e85a-290">Pour plus d’informations, consultez [la norme Unicode](https://www.unicode.org/versions/latest/), sections 5.22 et 3.9.</span><span class="sxs-lookup"><span data-stu-id="9e85a-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="9e85a-291">Les `Encoding` classes intégrées peuvent également être configurées pour lancer une exception plutôt que d’effectuer la substitution de caractères lorsque des séquences mal formées sont vues.</span><span class="sxs-lookup"><span data-stu-id="9e85a-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="9e85a-292">Cette approche est souvent utilisée dans des applications sensibles à la sécurité où la substitution de caractères peut ne pas être acceptable.</span><span class="sxs-lookup"><span data-stu-id="9e85a-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="9e85a-293">Pour plus d’informations sur `Encoding` la façon d’utiliser les classes intégrées, voir [Comment utiliser les classes d’encodage des personnages en .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="9e85a-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e85a-294">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e85a-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="9e85a-295">Mondialisation et localisation</span><span class="sxs-lookup"><span data-stu-id="9e85a-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
