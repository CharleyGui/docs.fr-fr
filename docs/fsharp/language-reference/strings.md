---
title: Chaînes
description: Découvrez comment le F# type’String’représente du texte immuable comme une séquence de caractères Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 25f5d7ce5059ba5ddb4e938313c511734c2d7320
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216737"
---
# <a name="strings"></a><span data-ttu-id="48f7b-103">Chaînes</span><span class="sxs-lookup"><span data-stu-id="48f7b-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="48f7b-104">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="48f7b-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="48f7b-105">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="48f7b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="48f7b-106">Le `string` type représente du texte immuable sous la forme d’une séquence de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="48f7b-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="48f7b-107">`string` est un alias pour `System.String` dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48f7b-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="48f7b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="48f7b-108">Remarks</span></span>

<span data-ttu-id="48f7b-109">Les littéraux de chaîne sont délimités par le caractère guillemet (").</span><span class="sxs-lookup"><span data-stu-id="48f7b-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="48f7b-110">La barre oblique inverse \\ () est utilisée pour encoder certains caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="48f7b-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="48f7b-111">La barre oblique inverse et le caractère suivant se présentent sous la forme d’une *séquence d’échappement*.</span><span class="sxs-lookup"><span data-stu-id="48f7b-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="48f7b-112">Les séquences d’échappement F# prises en charge dans les littéraux de chaîne sont indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="48f7b-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="48f7b-113">Caractère</span><span class="sxs-lookup"><span data-stu-id="48f7b-113">Character</span></span>|<span data-ttu-id="48f7b-114">Séquence d'échappement</span><span class="sxs-lookup"><span data-stu-id="48f7b-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="48f7b-115">Alerte</span><span class="sxs-lookup"><span data-stu-id="48f7b-115">Alert</span></span>|`\a`|
|<span data-ttu-id="48f7b-116">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="48f7b-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="48f7b-117">Saut de page</span><span class="sxs-lookup"><span data-stu-id="48f7b-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="48f7b-118">Saut de ligne</span><span class="sxs-lookup"><span data-stu-id="48f7b-118">Newline</span></span>|`\n`|
|<span data-ttu-id="48f7b-119">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="48f7b-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="48f7b-120">Onglet</span><span class="sxs-lookup"><span data-stu-id="48f7b-120">Tab</span></span>|`\t`|
|<span data-ttu-id="48f7b-121">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="48f7b-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="48f7b-122">Barre oblique inverse</span><span class="sxs-lookup"><span data-stu-id="48f7b-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="48f7b-123">Guillemet</span><span class="sxs-lookup"><span data-stu-id="48f7b-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="48f7b-124">Caractère</span><span class="sxs-lookup"><span data-stu-id="48f7b-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="48f7b-125">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="48f7b-125">Unicode character</span></span>|<span data-ttu-id="48f7b-126">`\DDD`(où `D` indique un chiffre décimal ; la plage de 000-255 ; par exemple `\231` , = « ç »)</span><span class="sxs-lookup"><span data-stu-id="48f7b-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="48f7b-127">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="48f7b-127">Unicode character</span></span>|<span data-ttu-id="48f7b-128">`\xHH`(où `H` indique un chiffre hexadécimal ; la plage de 00 à FF ; par exemple `\xE7` , = "ç")</span><span class="sxs-lookup"><span data-stu-id="48f7b-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="48f7b-129">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="48f7b-129">Unicode character</span></span>|<span data-ttu-id="48f7b-130">`\uHHHH`(UTF-16) (où `H` indique un chiffre hexadécimal ; plage de 0000-FFFF ;  par exemple, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="48f7b-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="48f7b-131">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="48f7b-131">Unicode character</span></span>|<span data-ttu-id="48f7b-132">`\U00HHHHHH`(UTF-32) (où `H` indique un chiffre hexadécimal ; plage de 000000-10FFFF ;  par exemple, `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="48f7b-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="48f7b-133">La `\DDD` séquence d’échappement est une notation décimale, et non une notation octale comme dans la plupart des autres langages.</span><span class="sxs-lookup"><span data-stu-id="48f7b-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="48f7b-134">Par conséquent, `8` les `9` chiffres et sont valides, et `\032` une séquence de représente un espace (U + 0020), alors que ce `\040`même point de code en notation octale serait.</span><span class="sxs-lookup"><span data-stu-id="48f7b-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="48f7b-135">Étant donné qu’il est imposé à une plage de 0-255 (0xFF) `\DDD` , `\x` les séquences d’échappement et sont en fait le jeu de caractères [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , car cela correspond aux 256 premiers points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="48f7b-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="48f7b-136">S’il est précédé du symbole @, le littéral est une chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="48f7b-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="48f7b-137">Cela signifie que toutes les séquences d’échappement sont ignorées, sauf que deux caractères guillemets sont interprétés comme un caractère guillemet.</span><span class="sxs-lookup"><span data-stu-id="48f7b-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="48f7b-138">En outre, une chaîne peut être placée entre des guillemets triples.</span><span class="sxs-lookup"><span data-stu-id="48f7b-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="48f7b-139">Dans ce cas, toutes les séquences d’échappement sont ignorées, y compris les guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="48f7b-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="48f7b-140">Pour spécifier une chaîne qui contient une chaîne entre guillemets incorporée, vous pouvez utiliser une chaîne textuelle ou une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="48f7b-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="48f7b-141">Si vous utilisez une chaîne textuelle, vous devez spécifier deux guillemets pour indiquer un caractère guillemet simple.</span><span class="sxs-lookup"><span data-stu-id="48f7b-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="48f7b-142">Si vous utilisez une chaîne entre guillemets, vous pouvez utiliser les guillemets simples sans qu’ils soient analysés comme la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="48f7b-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="48f7b-143">Cette technique peut être utile lorsque vous travaillez avec du code XML ou d’autres structures qui incluent des guillemets incorporés.</span><span class="sxs-lookup"><span data-stu-id="48f7b-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="48f7b-144">Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des nouvelles lignes, sauf si une barre oblique inverse est le dernier caractère avant le saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="48f7b-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="48f7b-145">L’espace blanc de début sur la ligne suivante est ignoré lorsque la barre oblique inverse est utilisée.</span><span class="sxs-lookup"><span data-stu-id="48f7b-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="48f7b-146">Le code suivant génère une chaîne `str1` qui a une `"abc\ndef"` valeur et une `str2` chaîne qui a `"abcdef"`la valeur.</span><span class="sxs-lookup"><span data-stu-id="48f7b-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="48f7b-147">Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide d’une syntaxe de type tableau, comme suit.</span><span class="sxs-lookup"><span data-stu-id="48f7b-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="48f7b-148">Le résultat est `b`.</span><span class="sxs-lookup"><span data-stu-id="48f7b-148">The output is `b`.</span></span>

<span data-ttu-id="48f7b-149">Vous pouvez aussi extraire des sous-chaînes à l’aide de la syntaxe de découpage de tableau, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="48f7b-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="48f7b-150">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="48f7b-150">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="48f7b-151">Vous pouvez représenter des chaînes ASCII par des tableaux d’octets non signés, `byte[]`de type.</span><span class="sxs-lookup"><span data-stu-id="48f7b-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="48f7b-152">Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII.</span><span class="sxs-lookup"><span data-stu-id="48f7b-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="48f7b-153">Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’échappement Unicode.</span><span class="sxs-lookup"><span data-stu-id="48f7b-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="48f7b-154">Opérateurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="48f7b-154">String Operators</span></span>

<span data-ttu-id="48f7b-155">Il existe deux façons de concaténer des chaînes : à l' `+` aide de l’opérateur ou `^` à l’aide de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="48f7b-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="48f7b-156">L' `+` opérateur gère la compatibilité avec les fonctionnalités de gestion de chaîne .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48f7b-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="48f7b-157">L’exemple suivant illustre la concaténation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="48f7b-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="48f7b-158">String (classe)</span><span class="sxs-lookup"><span data-stu-id="48f7b-158">String Class</span></span>

<span data-ttu-id="48f7b-159">Étant donné que le type F# de chaîne dans est `System.String` en fait un type `System.String` de .NET Framework, tous les membres sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="48f7b-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="48f7b-160">Cela comprend l' `+` opérateur, qui est utilisé pour concaténer des chaînes, `Length` la propriété et la `Chars` propriété, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="48f7b-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="48f7b-161">Pour plus d’informations sur les chaînes `System.String`, consultez.</span><span class="sxs-lookup"><span data-stu-id="48f7b-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="48f7b-162">À l’aide `Chars` de la `System.String`propriété de, vous pouvez accéder aux différents caractères d’une chaîne en spécifiant un index, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="48f7b-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="48f7b-163">Module de chaîne</span><span class="sxs-lookup"><span data-stu-id="48f7b-163">String Module</span></span>

<span data-ttu-id="48f7b-164">Des fonctionnalités supplémentaires pour la gestion des chaînes sont `String` incluses dans le `FSharp.Core` module de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="48f7b-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="48f7b-165">Pour plus d’informations, consultez [module Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="48f7b-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="48f7b-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48f7b-166">See also</span></span>

- [<span data-ttu-id="48f7b-167">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="48f7b-167">F# Language Reference</span></span>](index.md)
