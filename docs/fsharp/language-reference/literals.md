---
title: Littéraux
description: En savoir plus sur les types de F# littéraux dans le langage de programmation.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041034"
---
# <a name="literals"></a><span data-ttu-id="31d83-103">Littéraux</span><span class="sxs-lookup"><span data-stu-id="31d83-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="31d83-104">Les liens de référence sur les API de cet article vous feront accéder à MSDN (pour l’instant).</span><span class="sxs-lookup"><span data-stu-id="31d83-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="31d83-105">Cette rubrique fournit un tableau qui indique comment spécifier le type d’un littéral dans F#.</span><span class="sxs-lookup"><span data-stu-id="31d83-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="31d83-106">Types de littéraux</span><span class="sxs-lookup"><span data-stu-id="31d83-106">Literal Types</span></span>

<span data-ttu-id="31d83-107">Le tableau suivant présente les types de littéraux dans F#.</span><span class="sxs-lookup"><span data-stu-id="31d83-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="31d83-108">Les caractères qui représentent des chiffres en notation hexadécimale ne respectent pas la casse ; les caractères qui identifient le type respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="31d83-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="31d83-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="31d83-109">Type</span></span>|<span data-ttu-id="31d83-110">Description</span><span class="sxs-lookup"><span data-stu-id="31d83-110">Description</span></span>|<span data-ttu-id="31d83-111">Suffixe ou préfixe</span><span class="sxs-lookup"><span data-stu-id="31d83-111">Suffix or prefix</span></span>|<span data-ttu-id="31d83-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="31d83-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="31d83-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="31d83-113">sbyte</span></span>|<span data-ttu-id="31d83-114">entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="31d83-114">signed 8-bit integer</span></span>|<span data-ttu-id="31d83-115">o</span><span class="sxs-lookup"><span data-stu-id="31d83-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="31d83-116">byte</span><span class="sxs-lookup"><span data-stu-id="31d83-116">byte</span></span>|<span data-ttu-id="31d83-117">nombre naturel 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="31d83-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="31d83-118">uy</span><span class="sxs-lookup"><span data-stu-id="31d83-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="31d83-119">int16</span><span class="sxs-lookup"><span data-stu-id="31d83-119">int16</span></span>|<span data-ttu-id="31d83-120">entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="31d83-120">signed 16-bit integer</span></span>|<span data-ttu-id="31d83-121">s</span><span class="sxs-lookup"><span data-stu-id="31d83-121">s</span></span>|`86s`|
|<span data-ttu-id="31d83-122">uint16</span><span class="sxs-lookup"><span data-stu-id="31d83-122">uint16</span></span>|<span data-ttu-id="31d83-123">nombre naturel 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="31d83-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="31d83-124">us</span><span class="sxs-lookup"><span data-stu-id="31d83-124">us</span></span>|`86us`|
|<span data-ttu-id="31d83-125">int</span><span class="sxs-lookup"><span data-stu-id="31d83-125">int</span></span><br /><br /><span data-ttu-id="31d83-126">int32</span><span class="sxs-lookup"><span data-stu-id="31d83-126">int32</span></span>|<span data-ttu-id="31d83-127">entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="31d83-127">signed 32-bit integer</span></span>|<span data-ttu-id="31d83-128">l ou aucun</span><span class="sxs-lookup"><span data-stu-id="31d83-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="31d83-129">uint</span><span class="sxs-lookup"><span data-stu-id="31d83-129">uint</span></span><br /><br /><span data-ttu-id="31d83-130">uint32</span><span class="sxs-lookup"><span data-stu-id="31d83-130">uint32</span></span>|<span data-ttu-id="31d83-131">nombre naturel non signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="31d83-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="31d83-132">u ou UL</span><span class="sxs-lookup"><span data-stu-id="31d83-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="31d83-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="31d83-133">nativeint</span></span>|<span data-ttu-id="31d83-134">pointeur natif vers un nombre naturel signé</span><span class="sxs-lookup"><span data-stu-id="31d83-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="31d83-135">n</span><span class="sxs-lookup"><span data-stu-id="31d83-135">n</span></span>|`123n`|
|<span data-ttu-id="31d83-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="31d83-136">unativeint</span></span>|<span data-ttu-id="31d83-137">pointeur natif en tant que nombre naturel non signé</span><span class="sxs-lookup"><span data-stu-id="31d83-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="31d83-138">ÉCHAPP</span><span class="sxs-lookup"><span data-stu-id="31d83-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="31d83-139">int64</span><span class="sxs-lookup"><span data-stu-id="31d83-139">int64</span></span>|<span data-ttu-id="31d83-140">entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="31d83-140">signed 64-bit integer</span></span>|<span data-ttu-id="31d83-141">L</span><span class="sxs-lookup"><span data-stu-id="31d83-141">L</span></span>|`86L`|
|<span data-ttu-id="31d83-142">uint64</span><span class="sxs-lookup"><span data-stu-id="31d83-142">uint64</span></span>|<span data-ttu-id="31d83-143">nombre naturel non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="31d83-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="31d83-144">UL</span><span class="sxs-lookup"><span data-stu-id="31d83-144">UL</span></span>|`86UL`|
|<span data-ttu-id="31d83-145">unique, float32</span><span class="sxs-lookup"><span data-stu-id="31d83-145">single, float32</span></span>|<span data-ttu-id="31d83-146">nombre à virgule flottante 32 bits</span><span class="sxs-lookup"><span data-stu-id="31d83-146">32-bit floating point number</span></span>|<span data-ttu-id="31d83-147">F ou f</span><span class="sxs-lookup"><span data-stu-id="31d83-147">F or f</span></span>|<span data-ttu-id="31d83-148">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="31d83-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="31d83-149">chariot</span><span class="sxs-lookup"><span data-stu-id="31d83-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="31d83-150">dissocié Cliquer</span><span class="sxs-lookup"><span data-stu-id="31d83-150">float; double</span></span>|<span data-ttu-id="31d83-151">nombre à virgule flottante 64 bits</span><span class="sxs-lookup"><span data-stu-id="31d83-151">64-bit floating point number</span></span>|<span data-ttu-id="31d83-152">none</span><span class="sxs-lookup"><span data-stu-id="31d83-152">none</span></span>|<span data-ttu-id="31d83-153">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="31d83-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="31d83-154">CHARIOT</span><span class="sxs-lookup"><span data-stu-id="31d83-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="31d83-155">bigint</span><span class="sxs-lookup"><span data-stu-id="31d83-155">bigint</span></span>|<span data-ttu-id="31d83-156">entier non limité à la représentation 64 bits</span><span class="sxs-lookup"><span data-stu-id="31d83-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="31d83-157">I</span><span class="sxs-lookup"><span data-stu-id="31d83-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="31d83-158">decimal</span><span class="sxs-lookup"><span data-stu-id="31d83-158">decimal</span></span>|<span data-ttu-id="31d83-159">nombre fractionnaire représenté sous la forme d’un nombre à virgule fixe ou rationnel</span><span class="sxs-lookup"><span data-stu-id="31d83-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="31d83-160">M ou m</span><span class="sxs-lookup"><span data-stu-id="31d83-160">M or m</span></span>|<span data-ttu-id="31d83-161">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="31d83-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="31d83-162">Char</span><span class="sxs-lookup"><span data-stu-id="31d83-162">Char</span></span>|<span data-ttu-id="31d83-163">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="31d83-163">Unicode character</span></span>|<span data-ttu-id="31d83-164">none</span><span class="sxs-lookup"><span data-stu-id="31d83-164">none</span></span>|<span data-ttu-id="31d83-165">`'a'` ou `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="31d83-165">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="31d83-166">Chaîne</span><span class="sxs-lookup"><span data-stu-id="31d83-166">String</span></span>|<span data-ttu-id="31d83-167">chaîne Unicode</span><span class="sxs-lookup"><span data-stu-id="31d83-167">Unicode string</span></span>|<span data-ttu-id="31d83-168">none</span><span class="sxs-lookup"><span data-stu-id="31d83-168">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="31d83-169">or</span><span class="sxs-lookup"><span data-stu-id="31d83-169">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="31d83-170">or</span><span class="sxs-lookup"><span data-stu-id="31d83-170">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="31d83-171">or</span><span class="sxs-lookup"><span data-stu-id="31d83-171">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="31d83-172">Voir aussi [chaînes](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="31d83-172">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="31d83-173">byte</span><span class="sxs-lookup"><span data-stu-id="31d83-173">byte</span></span>|<span data-ttu-id="31d83-174">Caractère ASCII</span><span class="sxs-lookup"><span data-stu-id="31d83-174">ASCII character</span></span>|<span data-ttu-id="31d83-175">B</span><span class="sxs-lookup"><span data-stu-id="31d83-175">B</span></span>|`'a'B`|
|<span data-ttu-id="31d83-176">byte[]</span><span class="sxs-lookup"><span data-stu-id="31d83-176">byte[]</span></span>|<span data-ttu-id="31d83-177">Chaîne ASCII</span><span class="sxs-lookup"><span data-stu-id="31d83-177">ASCII string</span></span>|<span data-ttu-id="31d83-178">B</span><span class="sxs-lookup"><span data-stu-id="31d83-178">B</span></span>|`"text"B`|
|<span data-ttu-id="31d83-179">String ou Byte []</span><span class="sxs-lookup"><span data-stu-id="31d83-179">String or byte[]</span></span>|<span data-ttu-id="31d83-180">chaîne textuelle</span><span class="sxs-lookup"><span data-stu-id="31d83-180">verbatim string</span></span>|<span data-ttu-id="31d83-181">@ préfixe</span><span class="sxs-lookup"><span data-stu-id="31d83-181">@ prefix</span></span>|<span data-ttu-id="31d83-182">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="31d83-182">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="31d83-183">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="31d83-183">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="31d83-184">Littéraux nommés</span><span class="sxs-lookup"><span data-stu-id="31d83-184">Named literals</span></span>

<span data-ttu-id="31d83-185">Les valeurs qui sont destinées à être des constantes peuvent être marquées avec l’attribut [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="31d83-185">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="31d83-186">Cet attribut a pour effet de provoquer la compilation d’une valeur en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="31d83-186">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="31d83-187">Dans les expressions de critères spéciaux, les identificateurs qui commencent par des caractères minuscules sont toujours traités comme des variables à lier, plutôt que comme des littéraux. vous devez donc généralement utiliser des majuscules lorsque vous définissez des littéraux.</span><span class="sxs-lookup"><span data-stu-id="31d83-187">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="31d83-188">Notes</span><span class="sxs-lookup"><span data-stu-id="31d83-188">Remarks</span></span>

<span data-ttu-id="31d83-189">Les chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivis d’un code hexadécimal 16 bits (0000-FFFF) ou d’encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivi d’un code hexadécimal 32 bits qui représente tout Unicode. point de code (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="31d83-189">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="31d83-190">L’utilisation d’autres opérateurs de bits autres que `|||` n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="31d83-190">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="31d83-191">Entiers dans d’autres bases</span><span class="sxs-lookup"><span data-stu-id="31d83-191">Integers in other bases</span></span>

<span data-ttu-id="31d83-192">Les entiers 32 bits signés peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide d’un préfixe `0x`, `0o` ou `0b` respectivement.</span><span class="sxs-lookup"><span data-stu-id="31d83-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="31d83-193">Traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="31d83-193">Underscores in numeric literals</span></span>

<span data-ttu-id="31d83-194">Vous pouvez séparer les chiffres par le caractère de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="31d83-194">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="31d83-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d83-195">See also</span></span>

- [<span data-ttu-id="31d83-196">Core. LiteralAttribute (, classe</span><span class="sxs-lookup"><span data-stu-id="31d83-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
