---
title: Chaînes
description: "Découvrez comment le type F # 'String’représente du texte immuable comme une séquence de caractères Unicode."
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812209"
---
# <a name="strings"></a><span data-ttu-id="71dac-103">Chaînes</span><span class="sxs-lookup"><span data-stu-id="71dac-103">Strings</span></span>

<span data-ttu-id="71dac-104">Le `string` type représente du texte immuable sous la forme d’une séquence de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="71dac-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="71dac-105">`string` est un alias de `System.String` dans .NET.</span><span class="sxs-lookup"><span data-stu-id="71dac-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="71dac-106">Notes</span><span class="sxs-lookup"><span data-stu-id="71dac-106">Remarks</span></span>

<span data-ttu-id="71dac-107">Les littéraux de chaîne sont délimités par le caractère guillemet (").</span><span class="sxs-lookup"><span data-stu-id="71dac-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="71dac-108">La barre oblique inverse ( \\ ) est utilisée pour encoder certains caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="71dac-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="71dac-109">La barre oblique inverse et le caractère suivant se présentent sous la forme d’une *séquence d’échappement*.</span><span class="sxs-lookup"><span data-stu-id="71dac-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="71dac-110">Les séquences d’échappement prises en charge dans les littéraux de chaîne F # sont indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="71dac-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="71dac-111">Caractère</span><span class="sxs-lookup"><span data-stu-id="71dac-111">Character</span></span>|<span data-ttu-id="71dac-112">Séquence d'échappement</span><span class="sxs-lookup"><span data-stu-id="71dac-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="71dac-113">Alerte</span><span class="sxs-lookup"><span data-stu-id="71dac-113">Alert</span></span>|`\a`|
|<span data-ttu-id="71dac-114">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="71dac-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="71dac-115">Saut de page</span><span class="sxs-lookup"><span data-stu-id="71dac-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="71dac-116">Saut de ligne</span><span class="sxs-lookup"><span data-stu-id="71dac-116">Newline</span></span>|`\n`|
|<span data-ttu-id="71dac-117">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="71dac-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="71dac-118">Onglet</span><span class="sxs-lookup"><span data-stu-id="71dac-118">Tab</span></span>|`\t`|
|<span data-ttu-id="71dac-119">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="71dac-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="71dac-120">Barre oblique inverse</span><span class="sxs-lookup"><span data-stu-id="71dac-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="71dac-121">Guillemets</span><span class="sxs-lookup"><span data-stu-id="71dac-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="71dac-122">Apostrophe</span><span class="sxs-lookup"><span data-stu-id="71dac-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="71dac-123">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="71dac-123">Unicode character</span></span>|<span data-ttu-id="71dac-124">`\DDD` (où `D` indique un chiffre décimal ; la plage de 000-255 ; par exemple, `\231` = « ç »)</span><span class="sxs-lookup"><span data-stu-id="71dac-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="71dac-125">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="71dac-125">Unicode character</span></span>|<span data-ttu-id="71dac-126">`\xHH` (où `H` indique un chiffre hexadécimal ; la plage de 00 à FF ; par exemple `\xE7` , = "ç")</span><span class="sxs-lookup"><span data-stu-id="71dac-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="71dac-127">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="71dac-127">Unicode character</span></span>|<span data-ttu-id="71dac-128">`\uHHHH` (UTF-16) (où `H` indique un chiffre hexadécimal ; plage de 0000-FFFF ;  par exemple, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="71dac-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="71dac-129">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="71dac-129">Unicode character</span></span>|<span data-ttu-id="71dac-130">`\U00HHHHHH` (UTF-32) (où `H` indique un chiffre hexadécimal ; plage de 000000-10FFFF ;  par exemple, `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="71dac-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="71dac-131">La `\DDD` séquence d’échappement est une notation décimale, et non une notation octale comme dans la plupart des autres langages.</span><span class="sxs-lookup"><span data-stu-id="71dac-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="71dac-132">Par conséquent, les chiffres `8` et `9` sont valides, et une séquence de `\032` représente un espace (U + 0020), alors que ce même point de code en notation octale serait `\040` .</span><span class="sxs-lookup"><span data-stu-id="71dac-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="71dac-133">Étant donné qu’il est imposé à une plage de 0-255 (0xFF), les `\DDD` `\x` séquences d’échappement et sont en fait le jeu de caractères [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , car cela correspond aux 256 premiers points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="71dac-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="71dac-134">Chaînes textuelles</span><span class="sxs-lookup"><span data-stu-id="71dac-134">Verbatim Strings</span></span>

<span data-ttu-id="71dac-135">S’il est précédé du symbole @, le littéral est une chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="71dac-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="71dac-136">Cela signifie que toutes les séquences d’échappement sont ignorées, sauf que deux caractères guillemets sont interprétés comme un caractère guillemet.</span><span class="sxs-lookup"><span data-stu-id="71dac-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="71dac-137">Chaînes entre guillemets triple</span><span class="sxs-lookup"><span data-stu-id="71dac-137">Triple Quoted Strings</span></span>

<span data-ttu-id="71dac-138">En outre, une chaîne peut être placée entre des guillemets triples.</span><span class="sxs-lookup"><span data-stu-id="71dac-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="71dac-139">Dans ce cas, toutes les séquences d’échappement sont ignorées, y compris les guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="71dac-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="71dac-140">Pour spécifier une chaîne qui contient une chaîne entre guillemets incorporée, vous pouvez utiliser une chaîne textuelle ou une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="71dac-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="71dac-141">Si vous utilisez une chaîne textuelle, vous devez spécifier deux guillemets pour indiquer un caractère guillemet simple.</span><span class="sxs-lookup"><span data-stu-id="71dac-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="71dac-142">Si vous utilisez une chaîne entre guillemets, vous pouvez utiliser les guillemets simples sans qu’ils soient analysés comme la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="71dac-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="71dac-143">Cette technique peut être utile lorsque vous travaillez avec du code XML ou d’autres structures qui incluent des guillemets incorporés.</span><span class="sxs-lookup"><span data-stu-id="71dac-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="71dac-144">Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétés littéralement comme des nouvelles lignes, sauf si une barre oblique inverse est le dernier caractère avant le saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="71dac-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="71dac-145">L’espace blanc de début sur la ligne suivante est ignoré lorsque la barre oblique inverse est utilisée.</span><span class="sxs-lookup"><span data-stu-id="71dac-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="71dac-146">Le code suivant génère une chaîne `str1` qui a une valeur `"abc\ndef"` et une chaîne `str2` qui a la valeur `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="71dac-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="71dac-147">Indexation et découpage de chaîne</span><span class="sxs-lookup"><span data-stu-id="71dac-147">String Indexing and Slicing</span></span>

<span data-ttu-id="71dac-148">Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide d’une syntaxe de type tableau, comme suit.</span><span class="sxs-lookup"><span data-stu-id="71dac-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="71dac-149">La sortie est `b`.</span><span class="sxs-lookup"><span data-stu-id="71dac-149">The output is `b`.</span></span>

<span data-ttu-id="71dac-150">Vous pouvez aussi extraire des sous-chaînes à l’aide de la syntaxe de découpage de tableau, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="71dac-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="71dac-151">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="71dac-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="71dac-152">Vous pouvez représenter des chaînes ASCII par des tableaux d’octets non signés, de type `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="71dac-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="71dac-153">Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII.</span><span class="sxs-lookup"><span data-stu-id="71dac-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="71dac-154">Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prennent en charge les mêmes séquences d’échappement que les chaînes Unicode, à l’exception des séquences d’échappement Unicode.</span><span class="sxs-lookup"><span data-stu-id="71dac-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="71dac-155">Opérateurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="71dac-155">String Operators</span></span>

<span data-ttu-id="71dac-156">L' `+` opérateur peut être utilisé pour concaténer des chaînes, en conservant la compatibilité avec les fonctionnalités de gestion des chaînes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71dac-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="71dac-157">L’exemple suivant illustre la concaténation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="71dac-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="71dac-158">String (classe)</span><span class="sxs-lookup"><span data-stu-id="71dac-158">String Class</span></span>

<span data-ttu-id="71dac-159">Étant donné que le type de chaîne en F # est en fait un type de .NET Framework `System.String` , tous les `System.String` membres sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="71dac-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="71dac-160">Cela comprend l' `+` opérateur, qui est utilisé pour concaténer des chaînes, la `Length` propriété et la `Chars` propriété, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="71dac-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="71dac-161">Pour plus d’informations sur les chaînes, consultez `System.String` .</span><span class="sxs-lookup"><span data-stu-id="71dac-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="71dac-162">À l’aide `Chars` de la propriété de `System.String` , vous pouvez accéder aux différents caractères d’une chaîne en spécifiant un index, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="71dac-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="71dac-163">Module de chaîne</span><span class="sxs-lookup"><span data-stu-id="71dac-163">String Module</span></span>

<span data-ttu-id="71dac-164">Des fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le `String` module de l' `FSharp.Core` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="71dac-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="71dac-165">Pour plus d’informations, consultez [module de chaîne](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span><span class="sxs-lookup"><span data-stu-id="71dac-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="71dac-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71dac-166">See also</span></span>

- [<span data-ttu-id="71dac-167">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="71dac-167">F# Language Reference</span></span>](index.md)
