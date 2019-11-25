---
title: Char, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344046"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="f5ff5-102">Char, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5ff5-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="f5ff5-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="f5ff5-104">Each *code point*, or character code, represents a single Unicode character.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5ff5-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f5ff5-105">Remarks</span></span>

<span data-ttu-id="f5ff5-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="f5ff5-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="f5ff5-108">The default value of `Char` is the character with a code point of 0.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="f5ff5-109">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="f5ff5-109">Unicode Characters</span></span>

<span data-ttu-id="f5ff5-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="f5ff5-111">These first 128 code points are the same as those the ASCII character set defines.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="f5ff5-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="f5ff5-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="f5ff5-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="f5ff5-115">Conversions de type</span><span class="sxs-lookup"><span data-stu-id="f5ff5-115">Type Conversions</span></span>

<span data-ttu-id="f5ff5-116">Visual Basic does not convert directly between `Char` and the numeric types.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="f5ff5-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="f5ff5-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="f5ff5-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="f5ff5-120">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-120">The following example illustrates this.</span></span> <span data-ttu-id="f5ff5-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="f5ff5-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="f5ff5-123">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="f5ff5-123">Programming Tips</span></span>

- <span data-ttu-id="f5ff5-124">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="f5ff5-124">**Negative Numbers.**</span></span> <span data-ttu-id="f5ff5-125">`Char` is an unsigned type and cannot represent a negative value.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="f5ff5-126">In any case, you should not use `Char` to hold numeric values.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="f5ff5-127">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="f5ff5-127">**Interop Considerations.**</span></span> <span data-ttu-id="f5ff5-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="f5ff5-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="f5ff5-130">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="f5ff5-130">**Widening.**</span></span> <span data-ttu-id="f5ff5-131">The `Char` data type widens to `String`.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="f5ff5-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="f5ff5-133">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="f5ff5-133">**Type Characters.**</span></span> <span data-ttu-id="f5ff5-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="f5ff5-135">`Char` has no identifier type character.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="f5ff5-136">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="f5ff5-136">**Framework Type.**</span></span> <span data-ttu-id="f5ff5-137">Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5ff5-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5ff5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5ff5-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="f5ff5-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="f5ff5-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f5ff5-140">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="f5ff5-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="f5ff5-141">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="f5ff5-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f5ff5-142">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="f5ff5-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f5ff5-143">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="f5ff5-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f5ff5-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="f5ff5-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
