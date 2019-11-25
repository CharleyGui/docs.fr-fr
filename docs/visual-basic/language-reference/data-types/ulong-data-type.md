---
title: ULong, type de données
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343883"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="04e7e-102">ULong data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04e7e-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="04e7e-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="04e7e-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="04e7e-104">Notes</span><span class="sxs-lookup"><span data-stu-id="04e7e-104">Remarks</span></span>

<span data-ttu-id="04e7e-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span><span class="sxs-lookup"><span data-stu-id="04e7e-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="04e7e-106">La valeur par défaut de `ULong` est 0.</span><span class="sxs-lookup"><span data-stu-id="04e7e-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="04e7e-107">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="04e7e-107">Literal assignments</span></span>

<span data-ttu-id="04e7e-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="04e7e-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="04e7e-109">Si le littéral entier est en dehors de la plage de `ULong` (autrement dit, s’il est inférieur à <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="04e7e-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="04e7e-110">Dans l’exemple suivant, les entiers égaux à 7 934 076 125 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `ULong`.</span><span class="sxs-lookup"><span data-stu-id="04e7e-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="04e7e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="04e7e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="04e7e-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="04e7e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="04e7e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="04e7e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="04e7e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="04e7e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="04e7e-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="04e7e-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="04e7e-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="04e7e-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="04e7e-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="04e7e-117">Programming tips</span></span>

- <span data-ttu-id="04e7e-118">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-118">**Negative Numbers.**</span></span> <span data-ttu-id="04e7e-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span><span class="sxs-lookup"><span data-stu-id="04e7e-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="04e7e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span><span class="sxs-lookup"><span data-stu-id="04e7e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="04e7e-121">**CLS Compliance.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-121">**CLS Compliance.**</span></span> <span data-ttu-id="04e7e-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span><span class="sxs-lookup"><span data-stu-id="04e7e-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="04e7e-123">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-123">**Interop Considerations.**</span></span> <span data-ttu-id="04e7e-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span><span class="sxs-lookup"><span data-stu-id="04e7e-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="04e7e-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="04e7e-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="04e7e-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="04e7e-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="04e7e-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span><span class="sxs-lookup"><span data-stu-id="04e7e-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="04e7e-128">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-128">**Widening.**</span></span> <span data-ttu-id="04e7e-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="04e7e-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="04e7e-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="04e7e-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="04e7e-131">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-131">**Type Characters.**</span></span> <span data-ttu-id="04e7e-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span><span class="sxs-lookup"><span data-stu-id="04e7e-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="04e7e-133">`ULong` has no identifier type character.</span><span class="sxs-lookup"><span data-stu-id="04e7e-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="04e7e-134">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="04e7e-134">**Framework Type.**</span></span> <span data-ttu-id="04e7e-135">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04e7e-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="04e7e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04e7e-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="04e7e-137">Types de données</span><span class="sxs-lookup"><span data-stu-id="04e7e-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="04e7e-138">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="04e7e-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="04e7e-139">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="04e7e-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="04e7e-140">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="04e7e-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="04e7e-141">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="04e7e-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
