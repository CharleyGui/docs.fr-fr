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
# <a name="strings"></a><span data-ttu-id="83fe0-103">Chaînes</span><span class="sxs-lookup"><span data-stu-id="83fe0-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="83fe0-104">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="83fe0-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="83fe0-105">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="83fe0-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="83fe0-106">Le type de `string` représente du texte immuable sous la forme d’une séquence de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="83fe0-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="83fe0-107">`string` est un alias pour `System.String` dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83fe0-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="83fe0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="83fe0-108">Remarks</span></span>

<span data-ttu-id="83fe0-109">Les littéraux de chaîne sont délimités par le caractère guillemet (").</span><span class="sxs-lookup"><span data-stu-id="83fe0-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="83fe0-110">La barre oblique inverse (\\) est utilisée pour encoder certains caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="83fe0-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="83fe0-111">La barre oblique inverse et le caractère suivant se présentent sous la forme d’une *séquence d’échappement*.</span><span class="sxs-lookup"><span data-stu-id="83fe0-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="83fe0-112">Les séquences d’échappement F# prises en charge dans les littéraux de chaîne sont indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="83fe0-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="83fe0-113">Caractère</span><span class="sxs-lookup"><span data-stu-id="83fe0-113">Character</span></span>|<span data-ttu-id="83fe0-114">Séquence d'échappement</span><span class="sxs-lookup"><span data-stu-id="83fe0-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="83fe0-115">Alerte</span><span class="sxs-lookup"><span data-stu-id="83fe0-115">Alert</span></span>|`\a`|
|<span data-ttu-id="83fe0-116">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="83fe0-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="83fe0-117">Saut de page</span><span class="sxs-lookup"><span data-stu-id="83fe0-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="83fe0-118">Saut de ligne</span><span class="sxs-lookup"><span data-stu-id="83fe0-118">Newline</span></span>|`\n`|
|<span data-ttu-id="83fe0-119">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="83fe0-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="83fe0-120">Onglet</span><span class="sxs-lookup"><span data-stu-id="83fe0-120">Tab</span></span>|`\t`|
|<span data-ttu-id="83fe0-121">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="83fe0-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="83fe0-122">Barre oblique inverse</span><span class="sxs-lookup"><span data-stu-id="83fe0-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="83fe0-123">Guillemets</span><span class="sxs-lookup"><span data-stu-id="83fe0-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="83fe0-124">Caractère</span><span class="sxs-lookup"><span data-stu-id="83fe0-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="83fe0-125">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="83fe0-125">Unicode character</span></span>|<span data-ttu-id="83fe0-126">`\DDD` (où `D` indique un chiffre décimal ; la plage de 000-255 ; par exemple, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="83fe0-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="83fe0-127">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="83fe0-127">Unicode character</span></span>|<span data-ttu-id="83fe0-128">`\xHH` (où `H` indique un chiffre hexadécimal ; la plage de 00 à FF ; par exemple, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="83fe0-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="83fe0-129">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="83fe0-129">Unicode character</span></span>|<span data-ttu-id="83fe0-130">`\uHHHH` (UTF-16) (où `H` indique un chiffre hexadécimal ; plage de 0000-FFFF ;  par exemple, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="83fe0-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="83fe0-131">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="83fe0-131">Unicode character</span></span>|<span data-ttu-id="83fe0-132">`\U00HHHHHH` (UTF-32) (où `H` indique un chiffre hexadécimal ; plage de 000000-10FFFF ;  par exemple, `\U0001F47D` = «👽»)</span><span class="sxs-lookup"><span data-stu-id="83fe0-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="83fe0-133">La séquence d’échappement `\DDD` est une notation décimale, et non une notation octale comme dans la plupart des autres langages.</span><span class="sxs-lookup"><span data-stu-id="83fe0-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="83fe0-134">Par conséquent, les chiffres `8` et `9` sont valides, et une séquence de `\032` représente un espace (U + 0020), tandis que le même point de code en notation octale est `\040`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="83fe0-135">Étant contraints à une plage de 0-255 (0xFF), les séquences d’échappement `\DDD` et `\x` sont en fait le jeu de caractères [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , car cela correspond aux 256 premiers points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="83fe0-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="83fe0-136">Chaînes textuelles</span><span class="sxs-lookup"><span data-stu-id="83fe0-136">Verbatim Strings</span></span>

<span data-ttu-id="83fe0-137">S’il est précédé du symbole @, le littéral est une chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="83fe0-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="83fe0-138">Cela signifie que toutes les séquences d’échappement sont ignorées, sauf que deux caractères guillemets sont interprétés comme un caractère guillemet.</span><span class="sxs-lookup"><span data-stu-id="83fe0-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="83fe0-139">Chaînes entre guillemets triple</span><span class="sxs-lookup"><span data-stu-id="83fe0-139">Triple Quoted Strings</span></span>

<span data-ttu-id="83fe0-140">En outre, une chaîne peut être placée entre des guillemets triples.</span><span class="sxs-lookup"><span data-stu-id="83fe0-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="83fe0-141">Dans ce cas, toutes les séquences d’échappement sont ignorées, y compris les guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="83fe0-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="83fe0-142">Pour spécifier une chaîne qui contient une chaîne entre guillemets incorporée, vous pouvez utiliser une chaîne textuelle ou une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="83fe0-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="83fe0-143">Si vous utilisez une chaîne textuelle, vous devez spécifier deux guillemets pour indiquer un caractère guillemet simple.</span><span class="sxs-lookup"><span data-stu-id="83fe0-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="83fe0-144">Si vous utilisez une chaîne entre guillemets, vous pouvez utiliser les guillemets simples sans qu’ils soient analysés comme la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="83fe0-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="83fe0-145">Cette technique peut être utile lorsque vous travaillez avec du code XML ou d’autres structures qui incluent des guillemets incorporés.</span><span class="sxs-lookup"><span data-stu-id="83fe0-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="83fe0-146">Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des nouvelles lignes, sauf si une barre oblique inverse est le dernier caractère avant le saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="83fe0-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="83fe0-147">L’espace blanc de début sur la ligne suivante est ignoré lorsque la barre oblique inverse est utilisée.</span><span class="sxs-lookup"><span data-stu-id="83fe0-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="83fe0-148">Le code suivant produit une `str1` de chaîne qui a la valeur `"abc\ndef"` et une chaîne `str2` qui a une valeur `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="83fe0-149">Indexation et découpage de chaîne</span><span class="sxs-lookup"><span data-stu-id="83fe0-149">String Indexing and Slicing</span></span>

<span data-ttu-id="83fe0-150">Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide d’une syntaxe de type tableau, comme suit.</span><span class="sxs-lookup"><span data-stu-id="83fe0-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="83fe0-151">Le résultat est `b`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-151">The output is `b`.</span></span>

<span data-ttu-id="83fe0-152">Vous pouvez aussi extraire des sous-chaînes à l’aide de la syntaxe de découpage de tableau, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="83fe0-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="83fe0-153">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="83fe0-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="83fe0-154">Vous pouvez représenter des chaînes ASCII par des tableaux d’octets non signés, `byte[]`de type.</span><span class="sxs-lookup"><span data-stu-id="83fe0-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="83fe0-155">Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII.</span><span class="sxs-lookup"><span data-stu-id="83fe0-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="83fe0-156">Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’échappement Unicode.</span><span class="sxs-lookup"><span data-stu-id="83fe0-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="83fe0-157">Opérateurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="83fe0-157">String Operators</span></span>

<span data-ttu-id="83fe0-158">Il existe deux façons de concaténer des chaînes : à l’aide de l’opérateur `+` ou à l’aide de l’opérateur `^`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-158">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="83fe0-159">L’opérateur `+` maintient la compatibilité avec les fonctionnalités de gestion des chaînes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83fe0-159">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="83fe0-160">L’exemple suivant illustre la concaténation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="83fe0-160">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="83fe0-161">String (classe)</span><span class="sxs-lookup"><span data-stu-id="83fe0-161">String Class</span></span>

<span data-ttu-id="83fe0-162">Étant donné que le type F# de chaîne dans est en fait un type de `System.String` .NET Framework, tous les membres de `System.String` sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="83fe0-162">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="83fe0-163">Cela comprend l’opérateur `+`, qui est utilisé pour concaténer des chaînes, la propriété `Length` et la propriété `Chars`, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="83fe0-163">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="83fe0-164">Pour plus d’informations sur les chaînes, consultez `System.String`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-164">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="83fe0-165">À l’aide de la propriété `Chars` de `System.String`, vous pouvez accéder aux différents caractères d’une chaîne en spécifiant un index, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="83fe0-165">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="83fe0-166">Module de chaîne</span><span class="sxs-lookup"><span data-stu-id="83fe0-166">String Module</span></span>

<span data-ttu-id="83fe0-167">Des fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le module `String` de l’espace de noms `FSharp.Core`.</span><span class="sxs-lookup"><span data-stu-id="83fe0-167">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="83fe0-168">Pour plus d’informations, consultez [module Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="83fe0-168">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="83fe0-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83fe0-169">See also</span></span>

- [<span data-ttu-id="83fe0-170">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="83fe0-170">F# Language Reference</span></span>](index.md)
