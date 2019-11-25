---
title: SByte, type de données
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343952"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="5d3ec-102">SByte data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d3ec-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="5d3ec-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d3ec-104">Notes</span><span class="sxs-lookup"><span data-stu-id="5d3ec-104">Remarks</span></span>

<span data-ttu-id="5d3ec-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="5d3ec-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="5d3ec-107">La valeur par défaut de `SByte` est 0.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="5d3ec-108">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="5d3ec-108">Literal assignments</span></span>

<span data-ttu-id="5d3ec-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="5d3ec-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="5d3ec-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="5d3ec-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5d3ec-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5d3ec-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="5d3ec-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5d3ec-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5d3ec-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5d3ec-117">Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="5d3ec-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="5d3ec-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="5d3ec-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5d3ec-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span><span class="sxs-lookup"><span data-stu-id="5d3ec-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="5d3ec-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="5d3ec-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="5d3ec-124">The following example assigns a negative literal `Short` value to an `SByte`.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="5d3ec-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="5d3ec-126">In the case of our example, this is bit 15 of the literal `Short` value.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="5d3ec-127">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="5d3ec-127">Programming tips</span></span>

- <span data-ttu-id="5d3ec-128">**CLS Compliance.**</span><span class="sxs-lookup"><span data-stu-id="5d3ec-128">**CLS Compliance.**</span></span> <span data-ttu-id="5d3ec-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="5d3ec-130">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="5d3ec-130">**Widening.**</span></span> <span data-ttu-id="5d3ec-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="5d3ec-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="5d3ec-133">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="5d3ec-133">**Type Characters.**</span></span> <span data-ttu-id="5d3ec-134">`SByte` has no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="5d3ec-135">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="5d3ec-135">**Framework Type.**</span></span> <span data-ttu-id="5d3ec-136">Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d3ec-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d3ec-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d3ec-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="5d3ec-138">Types de données</span><span class="sxs-lookup"><span data-stu-id="5d3ec-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="5d3ec-139">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="5d3ec-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5d3ec-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="5d3ec-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="5d3ec-141">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="5d3ec-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="5d3ec-142">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="5d3ec-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="5d3ec-143">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="5d3ec-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="5d3ec-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="5d3ec-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
