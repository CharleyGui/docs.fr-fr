---
title: Littéraux
description: En savoir plus sur les types de littéraux dans le F# langage de programmation.
ms.date: 06/08/2019
ms.openlocfilehash: 93329cd868ff7a2daaffa1b87ba838bbbc98015c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816235"
---
# <a name="literals"></a><span data-ttu-id="59180-103">Littéraux</span><span class="sxs-lookup"><span data-stu-id="59180-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="59180-104">Les liens de référence des API dans cet article vous dirigera vers MSDN (pour l’instant).</span><span class="sxs-lookup"><span data-stu-id="59180-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="59180-105">Cette rubrique fournit une table qui montre comment spécifier le type d’un littéral dans F#.</span><span class="sxs-lookup"><span data-stu-id="59180-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="59180-106">Types de littéral</span><span class="sxs-lookup"><span data-stu-id="59180-106">Literal Types</span></span>

<span data-ttu-id="59180-107">Le tableau suivant présente les types de littéraux dans F#.</span><span class="sxs-lookup"><span data-stu-id="59180-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="59180-108">Les caractères qui représentent des chiffres en notation hexadécimale ne sont pas la casse ; les caractères qui identifient le type respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="59180-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="59180-109">Type</span><span class="sxs-lookup"><span data-stu-id="59180-109">Type</span></span>|<span data-ttu-id="59180-110">Description</span><span class="sxs-lookup"><span data-stu-id="59180-110">Description</span></span>|<span data-ttu-id="59180-111">Suffixe ou préfixe</span><span class="sxs-lookup"><span data-stu-id="59180-111">Suffix or prefix</span></span>|<span data-ttu-id="59180-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="59180-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="59180-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="59180-113">sbyte</span></span>|<span data-ttu-id="59180-114">entier signé 8 bits</span><span class="sxs-lookup"><span data-stu-id="59180-114">signed 8-bit integer</span></span>|<span data-ttu-id="59180-115">o</span><span class="sxs-lookup"><span data-stu-id="59180-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="59180-116">byte</span><span class="sxs-lookup"><span data-stu-id="59180-116">byte</span></span>|<span data-ttu-id="59180-117">nombre de naturel 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="59180-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="59180-118">UY</span><span class="sxs-lookup"><span data-stu-id="59180-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="59180-119">int16</span><span class="sxs-lookup"><span data-stu-id="59180-119">int16</span></span>|<span data-ttu-id="59180-120">entier signé 16 bits</span><span class="sxs-lookup"><span data-stu-id="59180-120">signed 16-bit integer</span></span>|<span data-ttu-id="59180-121">s</span><span class="sxs-lookup"><span data-stu-id="59180-121">s</span></span>|`86s`|
|<span data-ttu-id="59180-122">uint16</span><span class="sxs-lookup"><span data-stu-id="59180-122">uint16</span></span>|<span data-ttu-id="59180-123">nombre de naturel non signé 16 bits</span><span class="sxs-lookup"><span data-stu-id="59180-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="59180-124">us</span><span class="sxs-lookup"><span data-stu-id="59180-124">us</span></span>|`86us`|
|<span data-ttu-id="59180-125">int</span><span class="sxs-lookup"><span data-stu-id="59180-125">int</span></span><br /><br /><span data-ttu-id="59180-126">int32</span><span class="sxs-lookup"><span data-stu-id="59180-126">int32</span></span>|<span data-ttu-id="59180-127">entier signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="59180-127">signed 32-bit integer</span></span>|<span data-ttu-id="59180-128">« l » ou none</span><span class="sxs-lookup"><span data-stu-id="59180-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="59180-129">uint</span><span class="sxs-lookup"><span data-stu-id="59180-129">uint</span></span><br /><br /><span data-ttu-id="59180-130">uint32</span><span class="sxs-lookup"><span data-stu-id="59180-130">uint32</span></span>|<span data-ttu-id="59180-131">nombre de naturel non signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="59180-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="59180-132">u ou ul</span><span class="sxs-lookup"><span data-stu-id="59180-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="59180-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="59180-133">nativeint</span></span>|<span data-ttu-id="59180-134">pointeur natif à un nombre naturel signé</span><span class="sxs-lookup"><span data-stu-id="59180-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="59180-135">n</span><span class="sxs-lookup"><span data-stu-id="59180-135">n</span></span>|`123n`|
|<span data-ttu-id="59180-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="59180-136">unativeint</span></span>|<span data-ttu-id="59180-137">pointeur natif sous forme de nombre naturel non signé</span><span class="sxs-lookup"><span data-stu-id="59180-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="59180-138">Annuler</span><span class="sxs-lookup"><span data-stu-id="59180-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="59180-139">int64</span><span class="sxs-lookup"><span data-stu-id="59180-139">int64</span></span>|<span data-ttu-id="59180-140">entier signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="59180-140">signed 64-bit integer</span></span>|<span data-ttu-id="59180-141">L</span><span class="sxs-lookup"><span data-stu-id="59180-141">L</span></span>|`86L`|
|<span data-ttu-id="59180-142">uint64</span><span class="sxs-lookup"><span data-stu-id="59180-142">uint64</span></span>|<span data-ttu-id="59180-143">nombre de naturel non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="59180-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="59180-144">UL</span><span class="sxs-lookup"><span data-stu-id="59180-144">UL</span></span>|`86UL`|
|<span data-ttu-id="59180-145">single, float32</span><span class="sxs-lookup"><span data-stu-id="59180-145">single, float32</span></span>|<span data-ttu-id="59180-146">nombre à virgule flottante 32 bits</span><span class="sxs-lookup"><span data-stu-id="59180-146">32-bit floating point number</span></span>|<span data-ttu-id="59180-147">F ou f</span><span class="sxs-lookup"><span data-stu-id="59180-147">F or f</span></span>|<span data-ttu-id="59180-148">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="59180-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="59180-149">LF</span><span class="sxs-lookup"><span data-stu-id="59180-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="59180-150">type float ; Double</span><span class="sxs-lookup"><span data-stu-id="59180-150">float; double</span></span>|<span data-ttu-id="59180-151">nombre à virgule flottante 64 bits</span><span class="sxs-lookup"><span data-stu-id="59180-151">64-bit floating point number</span></span>|<span data-ttu-id="59180-152">none</span><span class="sxs-lookup"><span data-stu-id="59180-152">none</span></span>|<span data-ttu-id="59180-153">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="59180-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="59180-154">LF</span><span class="sxs-lookup"><span data-stu-id="59180-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="59180-155">bigint</span><span class="sxs-lookup"><span data-stu-id="59180-155">bigint</span></span>|<span data-ttu-id="59180-156">entier non limité à la représentation 64 bits</span><span class="sxs-lookup"><span data-stu-id="59180-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="59180-157">I</span><span class="sxs-lookup"><span data-stu-id="59180-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="59180-158">decimal</span><span class="sxs-lookup"><span data-stu-id="59180-158">decimal</span></span>|<span data-ttu-id="59180-159">nombre fractionnaire représenté sous la forme à virgule fixe ou un nombre rationnel</span><span class="sxs-lookup"><span data-stu-id="59180-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="59180-160">M ou m</span><span class="sxs-lookup"><span data-stu-id="59180-160">M or m</span></span>|<span data-ttu-id="59180-161">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="59180-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="59180-162">Char</span><span class="sxs-lookup"><span data-stu-id="59180-162">Char</span></span>|<span data-ttu-id="59180-163">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="59180-163">Unicode character</span></span>|<span data-ttu-id="59180-164">none</span><span class="sxs-lookup"><span data-stu-id="59180-164">none</span></span>|`'a'`|
|<span data-ttu-id="59180-165">Chaîne</span><span class="sxs-lookup"><span data-stu-id="59180-165">String</span></span>|<span data-ttu-id="59180-166">chaîne Unicode</span><span class="sxs-lookup"><span data-stu-id="59180-166">Unicode string</span></span>|<span data-ttu-id="59180-167">none</span><span class="sxs-lookup"><span data-stu-id="59180-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="59180-168">ou</span><span class="sxs-lookup"><span data-stu-id="59180-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="59180-169">ou</span><span class="sxs-lookup"><span data-stu-id="59180-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="59180-170">ou</span><span class="sxs-lookup"><span data-stu-id="59180-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="59180-171">Voir aussi [chaînes](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="59180-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="59180-172">byte</span><span class="sxs-lookup"><span data-stu-id="59180-172">byte</span></span>|<span data-ttu-id="59180-173">Caractère ASCII</span><span class="sxs-lookup"><span data-stu-id="59180-173">ASCII character</span></span>|<span data-ttu-id="59180-174">B</span><span class="sxs-lookup"><span data-stu-id="59180-174">B</span></span>|`'a'B`|
|<span data-ttu-id="59180-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="59180-175">byte[]</span></span>|<span data-ttu-id="59180-176">Chaîne ASCII</span><span class="sxs-lookup"><span data-stu-id="59180-176">ASCII string</span></span>|<span data-ttu-id="59180-177">B</span><span class="sxs-lookup"><span data-stu-id="59180-177">B</span></span>|`"text"B`|
|<span data-ttu-id="59180-178">String ou byte]</span><span class="sxs-lookup"><span data-stu-id="59180-178">String or byte[]</span></span>|<span data-ttu-id="59180-179">chaîne textuelle</span><span class="sxs-lookup"><span data-stu-id="59180-179">verbatim string</span></span>|<span data-ttu-id="59180-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="59180-180">@ prefix</span></span>|<span data-ttu-id="59180-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="59180-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="59180-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="59180-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="59180-183">Littéraux nommés</span><span class="sxs-lookup"><span data-stu-id="59180-183">Named literals</span></span>

<span data-ttu-id="59180-184">Les valeurs qui sont destinées à être des constantes peuvent être marquées avec le [littéral](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribut.</span><span class="sxs-lookup"><span data-stu-id="59180-184">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="59180-185">Cet attribut a pour effet de provoquer une valeur doit être compilé en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="59180-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="59180-186">Dans les expressions de critères spéciaux, les identificateurs qui commencent par les caractères minuscules sont toujours traités en tant que variables à lier, plutôt que comme des littéraux, par conséquent, vous devez généralement utiliser majuscules lorsque vous définissez des littéraux.</span><span class="sxs-lookup"><span data-stu-id="59180-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="59180-187">Notes</span><span class="sxs-lookup"><span data-stu-id="59180-187">Remarks</span></span>

<span data-ttu-id="59180-188">Chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivi d’un code hexadécimal 16 bits ou les encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivie d’un code hexadécimal 32 bits qui représente un Unicode paire de substitution.</span><span class="sxs-lookup"><span data-stu-id="59180-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="59180-189">L’utilisation d’autres opérateurs de bits autres que `|||` n’est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="59180-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="59180-190">Nombres entiers dans d’autres bases</span><span class="sxs-lookup"><span data-stu-id="59180-190">Integers in other bases</span></span>

<span data-ttu-id="59180-191">Entiers signés de 32 bits peuvent également être spécifiés dans hexadécimal, octal ou binaire à l’aide un `0x`, `0o` ou `0b` respectivement de préfixe.</span><span class="sxs-lookup"><span data-stu-id="59180-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="59180-192">Traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="59180-192">Underscores in numeric literals</span></span>

<span data-ttu-id="59180-193">Vous pouvez séparer les chiffres par le caractère de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="59180-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="59180-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59180-194">See also</span></span>

- [<span data-ttu-id="59180-195">Core.LiteralAttribute, classe</span><span class="sxs-lookup"><span data-stu-id="59180-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
