---
title: Littéraux
description: 'En savoir plus sur les types de littéraux dans le langage de programmation F #.'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855021"
---
# <a name="literals"></a><span data-ttu-id="5cccf-103">Littéraux</span><span class="sxs-lookup"><span data-stu-id="5cccf-103">Literals</span></span>

<span data-ttu-id="5cccf-104">Cet article fournit un tableau qui montre comment spécifier le type d’un littéral en F #.</span><span class="sxs-lookup"><span data-stu-id="5cccf-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="5cccf-105">La référence de l’API docs.microsoft.com pour F # n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="5cccf-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="5cccf-106">Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="5cccf-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="5cccf-107">Types de littéral</span><span class="sxs-lookup"><span data-stu-id="5cccf-107">Literal types</span></span>

<span data-ttu-id="5cccf-108">Le tableau suivant présente les types de littéraux en F #.</span><span class="sxs-lookup"><span data-stu-id="5cccf-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="5cccf-109">Les caractères qui représentent des chiffres en notation hexadécimale ne respectent pas la casse ; les caractères qui identifient le type respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="5cccf-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="5cccf-110">Type</span><span class="sxs-lookup"><span data-stu-id="5cccf-110">Type</span></span>|<span data-ttu-id="5cccf-111">Description</span><span class="sxs-lookup"><span data-stu-id="5cccf-111">Description</span></span>|<span data-ttu-id="5cccf-112">Suffixe ou préfixe</span><span class="sxs-lookup"><span data-stu-id="5cccf-112">Suffix or prefix</span></span>|<span data-ttu-id="5cccf-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="5cccf-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="5cccf-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="5cccf-114">sbyte</span></span>|<span data-ttu-id="5cccf-115">entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-115">signed 8-bit integer</span></span>|<span data-ttu-id="5cccf-116">y</span><span class="sxs-lookup"><span data-stu-id="5cccf-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="5cccf-117">byte</span><span class="sxs-lookup"><span data-stu-id="5cccf-117">byte</span></span>|<span data-ttu-id="5cccf-118">nombre naturel 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="5cccf-119">uy</span><span class="sxs-lookup"><span data-stu-id="5cccf-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="5cccf-120">int16</span><span class="sxs-lookup"><span data-stu-id="5cccf-120">int16</span></span>|<span data-ttu-id="5cccf-121">entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-121">signed 16-bit integer</span></span>|<span data-ttu-id="5cccf-122">s</span><span class="sxs-lookup"><span data-stu-id="5cccf-122">s</span></span>|`86s`|
|<span data-ttu-id="5cccf-123">uint16</span><span class="sxs-lookup"><span data-stu-id="5cccf-123">uint16</span></span>|<span data-ttu-id="5cccf-124">nombre naturel 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="5cccf-125">us</span><span class="sxs-lookup"><span data-stu-id="5cccf-125">us</span></span>|`86us`|
|<span data-ttu-id="5cccf-126">int</span><span class="sxs-lookup"><span data-stu-id="5cccf-126">int</span></span><br /><br /><span data-ttu-id="5cccf-127">int32</span><span class="sxs-lookup"><span data-stu-id="5cccf-127">int32</span></span>|<span data-ttu-id="5cccf-128">entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-128">signed 32-bit integer</span></span>|<span data-ttu-id="5cccf-129">l ou aucun</span><span class="sxs-lookup"><span data-stu-id="5cccf-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="5cccf-130">uint</span><span class="sxs-lookup"><span data-stu-id="5cccf-130">uint</span></span><br /><br /><span data-ttu-id="5cccf-131">uint32</span><span class="sxs-lookup"><span data-stu-id="5cccf-131">uint32</span></span>|<span data-ttu-id="5cccf-132">nombre naturel non signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="5cccf-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="5cccf-133">u ou UL</span><span class="sxs-lookup"><span data-stu-id="5cccf-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="5cccf-134">nativeint</span><span class="sxs-lookup"><span data-stu-id="5cccf-134">nativeint</span></span>|<span data-ttu-id="5cccf-135">pointeur natif vers un nombre naturel signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="5cccf-136">n</span><span class="sxs-lookup"><span data-stu-id="5cccf-136">n</span></span>|`123n`|
|<span data-ttu-id="5cccf-137">unativeint</span><span class="sxs-lookup"><span data-stu-id="5cccf-137">unativeint</span></span>|<span data-ttu-id="5cccf-138">pointeur natif en tant que nombre naturel non signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="5cccf-139">ÉCHAPP</span><span class="sxs-lookup"><span data-stu-id="5cccf-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="5cccf-140">int64</span><span class="sxs-lookup"><span data-stu-id="5cccf-140">int64</span></span>|<span data-ttu-id="5cccf-141">entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="5cccf-141">signed 64-bit integer</span></span>|<span data-ttu-id="5cccf-142">L</span><span class="sxs-lookup"><span data-stu-id="5cccf-142">L</span></span>|`86L`|
|<span data-ttu-id="5cccf-143">uint64</span><span class="sxs-lookup"><span data-stu-id="5cccf-143">uint64</span></span>|<span data-ttu-id="5cccf-144">nombre naturel non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="5cccf-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="5cccf-145">UL</span><span class="sxs-lookup"><span data-stu-id="5cccf-145">UL</span></span>|`86UL`|
|<span data-ttu-id="5cccf-146">unique, float32</span><span class="sxs-lookup"><span data-stu-id="5cccf-146">single, float32</span></span>|<span data-ttu-id="5cccf-147">nombre à virgule flottante 32 bits</span><span class="sxs-lookup"><span data-stu-id="5cccf-147">32-bit floating point number</span></span>|<span data-ttu-id="5cccf-148">F ou f</span><span class="sxs-lookup"><span data-stu-id="5cccf-148">F or f</span></span>|<span data-ttu-id="5cccf-149">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="5cccf-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="5cccf-150">chariot</span><span class="sxs-lookup"><span data-stu-id="5cccf-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="5cccf-151">dissocié Cliquer</span><span class="sxs-lookup"><span data-stu-id="5cccf-151">float; double</span></span>|<span data-ttu-id="5cccf-152">nombre à virgule flottante 64 bits</span><span class="sxs-lookup"><span data-stu-id="5cccf-152">64-bit floating point number</span></span>|<span data-ttu-id="5cccf-153">Aucun</span><span class="sxs-lookup"><span data-stu-id="5cccf-153">none</span></span>|<span data-ttu-id="5cccf-154">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="5cccf-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="5cccf-155">CHARIOT</span><span class="sxs-lookup"><span data-stu-id="5cccf-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="5cccf-156">bigint</span><span class="sxs-lookup"><span data-stu-id="5cccf-156">bigint</span></span>|<span data-ttu-id="5cccf-157">entier non limité à la représentation 64 bits</span><span class="sxs-lookup"><span data-stu-id="5cccf-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="5cccf-158">I</span><span class="sxs-lookup"><span data-stu-id="5cccf-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="5cccf-159">Décimal</span><span class="sxs-lookup"><span data-stu-id="5cccf-159">decimal</span></span>|<span data-ttu-id="5cccf-160">nombre fractionnaire représenté sous la forme d’un nombre à virgule fixe ou rationnel</span><span class="sxs-lookup"><span data-stu-id="5cccf-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="5cccf-161">M ou m</span><span class="sxs-lookup"><span data-stu-id="5cccf-161">M or m</span></span>|<span data-ttu-id="5cccf-162">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="5cccf-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="5cccf-163">Char</span><span class="sxs-lookup"><span data-stu-id="5cccf-163">Char</span></span>|<span data-ttu-id="5cccf-164">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="5cccf-164">Unicode character</span></span>|<span data-ttu-id="5cccf-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="5cccf-165">none</span></span>|<span data-ttu-id="5cccf-166">`'a'` ou `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="5cccf-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="5cccf-167">String</span><span class="sxs-lookup"><span data-stu-id="5cccf-167">String</span></span>|<span data-ttu-id="5cccf-168">chaîne Unicode</span><span class="sxs-lookup"><span data-stu-id="5cccf-168">Unicode string</span></span>|<span data-ttu-id="5cccf-169">Aucun</span><span class="sxs-lookup"><span data-stu-id="5cccf-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="5cccf-170">or</span><span class="sxs-lookup"><span data-stu-id="5cccf-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="5cccf-171">or</span><span class="sxs-lookup"><span data-stu-id="5cccf-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="5cccf-172">or</span><span class="sxs-lookup"><span data-stu-id="5cccf-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="5cccf-173">Voir aussi [chaînes](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="5cccf-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="5cccf-174">byte</span><span class="sxs-lookup"><span data-stu-id="5cccf-174">byte</span></span>|<span data-ttu-id="5cccf-175">Caractère ASCII</span><span class="sxs-lookup"><span data-stu-id="5cccf-175">ASCII character</span></span>|<span data-ttu-id="5cccf-176">B</span><span class="sxs-lookup"><span data-stu-id="5cccf-176">B</span></span>|`'a'B`|
|<span data-ttu-id="5cccf-177">byte[]</span><span class="sxs-lookup"><span data-stu-id="5cccf-177">byte[]</span></span>|<span data-ttu-id="5cccf-178">Chaîne ASCII</span><span class="sxs-lookup"><span data-stu-id="5cccf-178">ASCII string</span></span>|<span data-ttu-id="5cccf-179">B</span><span class="sxs-lookup"><span data-stu-id="5cccf-179">B</span></span>|`"text"B`|
|<span data-ttu-id="5cccf-180">String ou Byte []</span><span class="sxs-lookup"><span data-stu-id="5cccf-180">String or byte[]</span></span>|<span data-ttu-id="5cccf-181">chaîne textuelle</span><span class="sxs-lookup"><span data-stu-id="5cccf-181">verbatim string</span></span>|<span data-ttu-id="5cccf-182">@ préfixe</span><span class="sxs-lookup"><span data-stu-id="5cccf-182">@ prefix</span></span>|<span data-ttu-id="5cccf-183">`@"\\server\share"`Unicode</span><span class="sxs-lookup"><span data-stu-id="5cccf-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="5cccf-184">`@"\\server\share"B`R</span><span class="sxs-lookup"><span data-stu-id="5cccf-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="5cccf-185">Littéraux nommés</span><span class="sxs-lookup"><span data-stu-id="5cccf-185">Named literals</span></span>

<span data-ttu-id="5cccf-186">Les valeurs qui sont destinées à être des constantes peuvent être marquées avec l’attribut [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="5cccf-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="5cccf-187">Cet attribut a pour effet de provoquer la compilation d’une valeur en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="5cccf-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="5cccf-188">Dans les expressions de critères spéciaux, les identificateurs qui commencent par des caractères minuscules sont toujours traités comme des variables à lier, plutôt que comme des littéraux. vous devez donc généralement utiliser des majuscules lorsque vous définissez des littéraux.</span><span class="sxs-lookup"><span data-stu-id="5cccf-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="5cccf-189">Notes</span><span class="sxs-lookup"><span data-stu-id="5cccf-189">Remarks</span></span>

<span data-ttu-id="5cccf-190">Les chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivis d’un code hexadécimal 16 bits (0000-ffff) ou d’encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivis d’un code hexadécimal 32 bits qui représente un point de code Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="5cccf-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="5cccf-191">L’utilisation d’autres opérateurs de bits autres que `|||` n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="5cccf-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="5cccf-192">Entiers dans d’autres bases</span><span class="sxs-lookup"><span data-stu-id="5cccf-192">Integers in other bases</span></span>

<span data-ttu-id="5cccf-193">Les entiers 32 bits signés peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide d’un `0x` `0o` préfixe, ou, `0b` respectivement.</span><span class="sxs-lookup"><span data-stu-id="5cccf-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="5cccf-194">Traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="5cccf-194">Underscores in numeric literals</span></span>

<span data-ttu-id="5cccf-195">Vous pouvez séparer les chiffres par le caractère de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="5cccf-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="5cccf-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cccf-196">See also</span></span>

- [<span data-ttu-id="5cccf-197">Core. LiteralAttribute (, classe</span><span class="sxs-lookup"><span data-stu-id="5cccf-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
