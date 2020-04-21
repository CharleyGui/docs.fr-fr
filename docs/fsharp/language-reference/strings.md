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
# <a name="strings"></a><span data-ttu-id="d6f18-103">Chaînes</span><span class="sxs-lookup"><span data-stu-id="d6f18-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="d6f18-104">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="d6f18-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="d6f18-105">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="d6f18-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="d6f18-106">Le `string` type représente le texte immuable comme une séquence de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6f18-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="d6f18-107">`string` est un alias pour `System.String` dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6f18-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6f18-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d6f18-108">Remarks</span></span>

<span data-ttu-id="d6f18-109">Les littérals de cordes sont délimités par le caractère de la marque de citation («)</span><span class="sxs-lookup"><span data-stu-id="d6f18-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="d6f18-110">Le personnage de \\ barre oblique inverse ( ) est utilisé pour coder certains caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="d6f18-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="d6f18-111">La barre oblique inverse et le personnage suivant ensemble sont connus comme une *séquence d’évasion*.</span><span class="sxs-lookup"><span data-stu-id="d6f18-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="d6f18-112">Les séquences d’évasion prises en charge dans les littérals de cordes F sont montrées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d6f18-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="d6f18-113">Caractère</span><span class="sxs-lookup"><span data-stu-id="d6f18-113">Character</span></span>|<span data-ttu-id="d6f18-114">Séquence d'échappement</span><span class="sxs-lookup"><span data-stu-id="d6f18-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="d6f18-115">Alerte</span><span class="sxs-lookup"><span data-stu-id="d6f18-115">Alert</span></span>|`\a`|
|<span data-ttu-id="d6f18-116">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="d6f18-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="d6f18-117">Saut de page</span><span class="sxs-lookup"><span data-stu-id="d6f18-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="d6f18-118">Saut de ligne</span><span class="sxs-lookup"><span data-stu-id="d6f18-118">Newline</span></span>|`\n`|
|<span data-ttu-id="d6f18-119">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="d6f18-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="d6f18-120">Onglet</span><span class="sxs-lookup"><span data-stu-id="d6f18-120">Tab</span></span>|`\t`|
|<span data-ttu-id="d6f18-121">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="d6f18-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="d6f18-122">Barre oblique inverse</span><span class="sxs-lookup"><span data-stu-id="d6f18-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="d6f18-123">Guillemets</span><span class="sxs-lookup"><span data-stu-id="d6f18-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="d6f18-124">Apostrophe</span><span class="sxs-lookup"><span data-stu-id="d6f18-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="d6f18-125">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="d6f18-125">Unicode character</span></span>|<span data-ttu-id="d6f18-126">`\DDD`(où `D` indique un chiffre décimal; gamme de 000 `\231` - 255; par exemple, "ç")</span><span class="sxs-lookup"><span data-stu-id="d6f18-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="d6f18-127">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="d6f18-127">Unicode character</span></span>|<span data-ttu-id="d6f18-128">`\xHH`(où `H` indique un chiffre hexadecimal; gamme de 00 - FF; par exemple, `\xE7` "ç")</span><span class="sxs-lookup"><span data-stu-id="d6f18-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="d6f18-129">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="d6f18-129">Unicode character</span></span>|<span data-ttu-id="d6f18-130">`\uHHHH`(UTF-16) (où `H` indique un chiffre hexadecimal; gamme de 0000 - FFFF;  par exemple, `\u00E7` "ç")</span><span class="sxs-lookup"><span data-stu-id="d6f18-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="d6f18-131">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="d6f18-131">Unicode character</span></span>|<span data-ttu-id="d6f18-132">`\U00HHHHHH`(UTF-32) (où `H` indique un chiffre hexadecimal; gamme de 0000000 - 10FFFF;  par exemple, `\U0001F47D` 👽" ")</span><span class="sxs-lookup"><span data-stu-id="d6f18-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="d6f18-133">La `\DDD` séquence d’évasion est une notation décimale, et non une notation octotale comme dans la plupart des autres langues.</span><span class="sxs-lookup"><span data-stu-id="d6f18-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="d6f18-134">Par conséquent, `8` `9` les chiffres et sont `\032` valides, et une séquence de représente un espace (U-0020), tandis que ce même point de code dans la notation octale serait `\040`.</span><span class="sxs-lookup"><span data-stu-id="d6f18-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f18-135">Étant limité à une gamme de 0 - 255 `\DDD` `\x` (0xFF), les séquences et d’évasion sont effectivement l’ENSEMBLE de caractères [ISO-8859-1,](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) puisque cela correspond aux 256 premiers points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6f18-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="d6f18-136">Cordes Verbatim</span><span class="sxs-lookup"><span data-stu-id="d6f18-136">Verbatim Strings</span></span>

<span data-ttu-id="d6f18-137">Si précédé par le symbole, le littéral est une chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="d6f18-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="d6f18-138">Cela signifie que toutes les séquences d’évasion sont ignorées, sauf que deux personnages de guillemets sont interprétés comme un personnage de marque de citation.</span><span class="sxs-lookup"><span data-stu-id="d6f18-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="d6f18-139">Triples cordes citées</span><span class="sxs-lookup"><span data-stu-id="d6f18-139">Triple Quoted Strings</span></span>

<span data-ttu-id="d6f18-140">En outre, une chaîne peut être entourée de citations triples.</span><span class="sxs-lookup"><span data-stu-id="d6f18-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="d6f18-141">Dans ce cas, toutes les séquences d’évasion sont ignorées, y compris les caractères de double guillemets.</span><span class="sxs-lookup"><span data-stu-id="d6f18-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="d6f18-142">Pour spécifier une chaîne qui contient une chaîne citée intégrée, vous pouvez soit utiliser une chaîne textuelle ou une chaîne à trois points.</span><span class="sxs-lookup"><span data-stu-id="d6f18-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="d6f18-143">Si vous utilisez une chaîne textuelle, vous devez spécifier deux caractères de guillemets pour indiquer un seul caractère de marque de citation.</span><span class="sxs-lookup"><span data-stu-id="d6f18-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="d6f18-144">Si vous utilisez une chaîne à trois citations, vous pouvez utiliser les caractères de la marque de citation unique sans qu’ils soient analysés comme la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d6f18-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="d6f18-145">Cette technique peut être utile lorsque vous travaillez avec XML ou d’autres structures qui incluent des guillemets intégrés.</span><span class="sxs-lookup"><span data-stu-id="d6f18-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="d6f18-146">Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des lignes neuves, à moins qu’un personnage de barre oblique inverse soit le dernier personnage avant la rupture de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d6f18-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="d6f18-147">L’espace blanc de tête sur la ligne suivante est ignoré lorsque le caractère de barre oblique inverse est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6f18-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="d6f18-148">Le code suivant `str1` produit une `"abc\ndef"` chaîne `str2` qui a `"abcdef"`de la valeur et une chaîne qui a de la valeur .</span><span class="sxs-lookup"><span data-stu-id="d6f18-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="d6f18-149">Indexation et découpe des cordes</span><span class="sxs-lookup"><span data-stu-id="d6f18-149">String Indexing and Slicing</span></span>

<span data-ttu-id="d6f18-150">Vous pouvez accéder à des caractères individuels dans une chaîne en utilisant la syntaxe en forme de tableau, comme suit.</span><span class="sxs-lookup"><span data-stu-id="d6f18-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="d6f18-151">Le résultat est `b`.</span><span class="sxs-lookup"><span data-stu-id="d6f18-151">The output is `b`.</span></span>

<span data-ttu-id="d6f18-152">Ou vous pouvez extraire des sous-cordes en utilisant la syntaxe de tranche de tableau, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d6f18-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="d6f18-153">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="d6f18-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="d6f18-154">Vous pouvez représenter les chaînes ASCII par des tableaux `byte[]`d’octets non signés, type .</span><span class="sxs-lookup"><span data-stu-id="d6f18-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="d6f18-155">Vous ajoutez le `B` suffixe à une chaîne littérale pour indiquer qu’il s’agit d’une chaîne ASCII.</span><span class="sxs-lookup"><span data-stu-id="d6f18-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="d6f18-156">Les littérals de cordes ASCII utilisés avec les tableaux byte prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’évasion Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6f18-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="d6f18-157">Opérateurs de cordes</span><span class="sxs-lookup"><span data-stu-id="d6f18-157">String Operators</span></span>

<span data-ttu-id="d6f18-158">L’opérateur `+` peut être utilisé pour concatenate des chaînes, en maintenant la compatibilité avec les caractéristiques de manipulation de chaîne .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6f18-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="d6f18-159">L’exemple suivant illustre la concatenation des cordes.</span><span class="sxs-lookup"><span data-stu-id="d6f18-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="d6f18-160">Classe de cordes</span><span class="sxs-lookup"><span data-stu-id="d6f18-160">String Class</span></span>

<span data-ttu-id="d6f18-161">Étant donné que le type de chaîne `System.String` en F `System.String` est en fait un type cadre .NET, tous les membres sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="d6f18-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="d6f18-162">Cela comprend `+` l’opérateur, qui est utilisé pour `Length` concatenate `Chars` cordes, la propriété, et la propriété, qui retourne la chaîne comme un tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6f18-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="d6f18-163">Pour plus d’informations `System.String`sur les chaînes, voir .</span><span class="sxs-lookup"><span data-stu-id="d6f18-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="d6f18-164">En utilisant `Chars` la `System.String`propriété de , vous pouvez accéder aux caractères individuels dans une chaîne en spécifiant un index, comme il est indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d6f18-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="d6f18-165">Module de chaîne</span><span class="sxs-lookup"><span data-stu-id="d6f18-165">String Module</span></span>

<span data-ttu-id="d6f18-166">D’autres fonctionnalités pour la `String` manipulation `FSharp.Core` des chaînes sont incluses dans le module dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="d6f18-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="d6f18-167">Pour plus d’informations, voir [Module Core.String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="d6f18-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6f18-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6f18-168">See also</span></span>

- [<span data-ttu-id="d6f18-169">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="d6f18-169">F# Language Reference</span></span>](index.md)
