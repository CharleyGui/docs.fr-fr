---
title: Littéraux
description: 'En savoir plus sur les types de littéraux dans le langage de programmation F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559152"
---
# <a name="literals"></a><span data-ttu-id="5beb0-103">Littéraux</span><span class="sxs-lookup"><span data-stu-id="5beb0-103">Literals</span></span>

<span data-ttu-id="5beb0-104">Cet article fournit un tableau qui montre comment spécifier le type d’un littéral en F #.</span><span class="sxs-lookup"><span data-stu-id="5beb0-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="5beb0-105">Types de littéral</span><span class="sxs-lookup"><span data-stu-id="5beb0-105">Literal types</span></span>

<span data-ttu-id="5beb0-106">Le tableau suivant présente les types de littéraux en F #.</span><span class="sxs-lookup"><span data-stu-id="5beb0-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="5beb0-107">Les caractères qui représentent des chiffres en notation hexadécimale ne respectent pas la casse ; les caractères qui identifient le type respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="5beb0-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="5beb0-108">Type</span><span class="sxs-lookup"><span data-stu-id="5beb0-108">Type</span></span>|<span data-ttu-id="5beb0-109">Description</span><span class="sxs-lookup"><span data-stu-id="5beb0-109">Description</span></span>|<span data-ttu-id="5beb0-110">Suffixe ou préfixe</span><span class="sxs-lookup"><span data-stu-id="5beb0-110">Suffix or prefix</span></span>|<span data-ttu-id="5beb0-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="5beb0-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="5beb0-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="5beb0-112">sbyte</span></span>|<span data-ttu-id="5beb0-113">entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-113">signed 8-bit integer</span></span>|<span data-ttu-id="5beb0-114">y</span><span class="sxs-lookup"><span data-stu-id="5beb0-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="5beb0-115">byte</span><span class="sxs-lookup"><span data-stu-id="5beb0-115">byte</span></span>|<span data-ttu-id="5beb0-116">nombre naturel 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="5beb0-117">uy</span><span class="sxs-lookup"><span data-stu-id="5beb0-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="5beb0-118">int16</span><span class="sxs-lookup"><span data-stu-id="5beb0-118">int16</span></span>|<span data-ttu-id="5beb0-119">entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-119">signed 16-bit integer</span></span>|<span data-ttu-id="5beb0-120">s</span><span class="sxs-lookup"><span data-stu-id="5beb0-120">s</span></span>|`86s`|
|<span data-ttu-id="5beb0-121">uint16</span><span class="sxs-lookup"><span data-stu-id="5beb0-121">uint16</span></span>|<span data-ttu-id="5beb0-122">nombre naturel 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="5beb0-123">us</span><span class="sxs-lookup"><span data-stu-id="5beb0-123">us</span></span>|`86us`|
|<span data-ttu-id="5beb0-124">int</span><span class="sxs-lookup"><span data-stu-id="5beb0-124">int</span></span><br /><br /><span data-ttu-id="5beb0-125">int32</span><span class="sxs-lookup"><span data-stu-id="5beb0-125">int32</span></span>|<span data-ttu-id="5beb0-126">entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-126">signed 32-bit integer</span></span>|<span data-ttu-id="5beb0-127">l ou aucun</span><span class="sxs-lookup"><span data-stu-id="5beb0-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="5beb0-128">uint</span><span class="sxs-lookup"><span data-stu-id="5beb0-128">uint</span></span><br /><br /><span data-ttu-id="5beb0-129">uint32</span><span class="sxs-lookup"><span data-stu-id="5beb0-129">uint32</span></span>|<span data-ttu-id="5beb0-130">nombre naturel non signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="5beb0-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="5beb0-131">u ou UL</span><span class="sxs-lookup"><span data-stu-id="5beb0-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="5beb0-132">nativeint</span><span class="sxs-lookup"><span data-stu-id="5beb0-132">nativeint</span></span>|<span data-ttu-id="5beb0-133">pointeur natif vers un nombre naturel signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="5beb0-134">n</span><span class="sxs-lookup"><span data-stu-id="5beb0-134">n</span></span>|`123n`|
|<span data-ttu-id="5beb0-135">unativeint</span><span class="sxs-lookup"><span data-stu-id="5beb0-135">unativeint</span></span>|<span data-ttu-id="5beb0-136">pointeur natif en tant que nombre naturel non signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="5beb0-137">ÉCHAPP</span><span class="sxs-lookup"><span data-stu-id="5beb0-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="5beb0-138">int64</span><span class="sxs-lookup"><span data-stu-id="5beb0-138">int64</span></span>|<span data-ttu-id="5beb0-139">entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="5beb0-139">signed 64-bit integer</span></span>|<span data-ttu-id="5beb0-140">L</span><span class="sxs-lookup"><span data-stu-id="5beb0-140">L</span></span>|`86L`|
|<span data-ttu-id="5beb0-141">uint64</span><span class="sxs-lookup"><span data-stu-id="5beb0-141">uint64</span></span>|<span data-ttu-id="5beb0-142">nombre naturel non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="5beb0-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="5beb0-143">UL</span><span class="sxs-lookup"><span data-stu-id="5beb0-143">UL</span></span>|`86UL`|
|<span data-ttu-id="5beb0-144">unique, float32</span><span class="sxs-lookup"><span data-stu-id="5beb0-144">single, float32</span></span>|<span data-ttu-id="5beb0-145">nombre à virgule flottante 32 bits</span><span class="sxs-lookup"><span data-stu-id="5beb0-145">32-bit floating point number</span></span>|<span data-ttu-id="5beb0-146">F ou f</span><span class="sxs-lookup"><span data-stu-id="5beb0-146">F or f</span></span>|<span data-ttu-id="5beb0-147">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="5beb0-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="5beb0-148">chariot</span><span class="sxs-lookup"><span data-stu-id="5beb0-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="5beb0-149">dissocié Cliquer</span><span class="sxs-lookup"><span data-stu-id="5beb0-149">float; double</span></span>|<span data-ttu-id="5beb0-150">nombre à virgule flottante 64 bits</span><span class="sxs-lookup"><span data-stu-id="5beb0-150">64-bit floating point number</span></span>|<span data-ttu-id="5beb0-151">aucun</span><span class="sxs-lookup"><span data-stu-id="5beb0-151">none</span></span>|<span data-ttu-id="5beb0-152">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="5beb0-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="5beb0-153">CHARIOT</span><span class="sxs-lookup"><span data-stu-id="5beb0-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="5beb0-154">bigint</span><span class="sxs-lookup"><span data-stu-id="5beb0-154">bigint</span></span>|<span data-ttu-id="5beb0-155">entier non limité à la représentation 64 bits</span><span class="sxs-lookup"><span data-stu-id="5beb0-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="5beb0-156">I</span><span class="sxs-lookup"><span data-stu-id="5beb0-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="5beb0-157">Décimal</span><span class="sxs-lookup"><span data-stu-id="5beb0-157">decimal</span></span>|<span data-ttu-id="5beb0-158">nombre fractionnaire représenté sous la forme d’un nombre à virgule fixe ou rationnel</span><span class="sxs-lookup"><span data-stu-id="5beb0-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="5beb0-159">M ou m</span><span class="sxs-lookup"><span data-stu-id="5beb0-159">M or m</span></span>|<span data-ttu-id="5beb0-160">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="5beb0-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="5beb0-161">Char</span><span class="sxs-lookup"><span data-stu-id="5beb0-161">Char</span></span>|<span data-ttu-id="5beb0-162">Caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="5beb0-162">Unicode character</span></span>|<span data-ttu-id="5beb0-163">aucun</span><span class="sxs-lookup"><span data-stu-id="5beb0-163">none</span></span>|<span data-ttu-id="5beb0-164">`'a'` ou `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="5beb0-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="5beb0-165">String</span><span class="sxs-lookup"><span data-stu-id="5beb0-165">String</span></span>|<span data-ttu-id="5beb0-166">chaîne Unicode</span><span class="sxs-lookup"><span data-stu-id="5beb0-166">Unicode string</span></span>|<span data-ttu-id="5beb0-167">aucun</span><span class="sxs-lookup"><span data-stu-id="5beb0-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="5beb0-168">or</span><span class="sxs-lookup"><span data-stu-id="5beb0-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="5beb0-169">or</span><span class="sxs-lookup"><span data-stu-id="5beb0-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="5beb0-170">or</span><span class="sxs-lookup"><span data-stu-id="5beb0-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="5beb0-171">Voir aussi [chaînes](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="5beb0-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="5beb0-172">byte</span><span class="sxs-lookup"><span data-stu-id="5beb0-172">byte</span></span>|<span data-ttu-id="5beb0-173">Caractère ASCII</span><span class="sxs-lookup"><span data-stu-id="5beb0-173">ASCII character</span></span>|<span data-ttu-id="5beb0-174">B</span><span class="sxs-lookup"><span data-stu-id="5beb0-174">B</span></span>|`'a'B`|
|<span data-ttu-id="5beb0-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="5beb0-175">byte[]</span></span>|<span data-ttu-id="5beb0-176">Chaîne ASCII</span><span class="sxs-lookup"><span data-stu-id="5beb0-176">ASCII string</span></span>|<span data-ttu-id="5beb0-177">B</span><span class="sxs-lookup"><span data-stu-id="5beb0-177">B</span></span>|`"text"B`|
|<span data-ttu-id="5beb0-178">String ou Byte []</span><span class="sxs-lookup"><span data-stu-id="5beb0-178">String or byte[]</span></span>|<span data-ttu-id="5beb0-179">chaîne textuelle</span><span class="sxs-lookup"><span data-stu-id="5beb0-179">verbatim string</span></span>|<span data-ttu-id="5beb0-180">@ préfixe</span><span class="sxs-lookup"><span data-stu-id="5beb0-180">@ prefix</span></span>|<span data-ttu-id="5beb0-181">`@"\\server\share"` Unicode</span><span class="sxs-lookup"><span data-stu-id="5beb0-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="5beb0-182">`@"\\server\share"B` R</span><span class="sxs-lookup"><span data-stu-id="5beb0-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="5beb0-183">Littéraux nommés</span><span class="sxs-lookup"><span data-stu-id="5beb0-183">Named literals</span></span>

<span data-ttu-id="5beb0-184">Les valeurs qui sont destinées à être des constantes peuvent être marquées avec l’attribut [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="5beb0-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="5beb0-185">Cet attribut a pour effet de provoquer la compilation d’une valeur en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="5beb0-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="5beb0-186">Dans les expressions de critères spéciaux, les identificateurs qui commencent par des caractères minuscules sont toujours traités comme des variables à lier, plutôt que comme des littéraux. vous devez donc généralement utiliser des majuscules lorsque vous définissez des littéraux.</span><span class="sxs-lookup"><span data-stu-id="5beb0-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="5beb0-187">Notes</span><span class="sxs-lookup"><span data-stu-id="5beb0-187">Remarks</span></span>

<span data-ttu-id="5beb0-188">Les chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivis d’un code hexadécimal 16 bits (0000-ffff) ou d’encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivis d’un code hexadécimal 32 bits qui représente un point de code Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="5beb0-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="5beb0-189">L’utilisation d’autres opérateurs de bits autres que `|||` n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="5beb0-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="5beb0-190">Entiers dans d’autres bases</span><span class="sxs-lookup"><span data-stu-id="5beb0-190">Integers in other bases</span></span>

<span data-ttu-id="5beb0-191">Les entiers 32 bits signés peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide d’un `0x` `0o` préfixe, ou, `0b` respectivement.</span><span class="sxs-lookup"><span data-stu-id="5beb0-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="5beb0-192">Traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="5beb0-192">Underscores in numeric literals</span></span>

<span data-ttu-id="5beb0-193">Vous pouvez séparer les chiffres par le caractère de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="5beb0-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
