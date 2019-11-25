---
title: Byte, type de données
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344079"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="66a53-102">Byte data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66a53-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="66a53-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span><span class="sxs-lookup"><span data-stu-id="66a53-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="66a53-104">Notes</span><span class="sxs-lookup"><span data-stu-id="66a53-104">Remarks</span></span>

<span data-ttu-id="66a53-105">Use the `Byte` data type to contain binary data.</span><span class="sxs-lookup"><span data-stu-id="66a53-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="66a53-106">La valeur par défaut de `Byte` est 0.</span><span class="sxs-lookup"><span data-stu-id="66a53-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="66a53-107">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="66a53-107">Literal assignments</span></span>

<span data-ttu-id="66a53-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="66a53-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="66a53-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span><span class="sxs-lookup"><span data-stu-id="66a53-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="66a53-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span><span class="sxs-lookup"><span data-stu-id="66a53-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="66a53-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="66a53-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="66a53-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="66a53-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="66a53-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="66a53-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="66a53-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="66a53-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="66a53-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="66a53-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="66a53-116">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="66a53-116">Programming tips</span></span>

- <span data-ttu-id="66a53-117">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="66a53-117">**Negative Numbers.**</span></span> <span data-ttu-id="66a53-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span><span class="sxs-lookup"><span data-stu-id="66a53-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="66a53-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span><span class="sxs-lookup"><span data-stu-id="66a53-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="66a53-120">**Format Conversions.**</span><span class="sxs-lookup"><span data-stu-id="66a53-120">**Format Conversions.**</span></span> <span data-ttu-id="66a53-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span><span class="sxs-lookup"><span data-stu-id="66a53-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="66a53-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span><span class="sxs-lookup"><span data-stu-id="66a53-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="66a53-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span><span class="sxs-lookup"><span data-stu-id="66a53-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="66a53-124">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="66a53-124">**Widening.**</span></span> <span data-ttu-id="66a53-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="66a53-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="66a53-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="66a53-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="66a53-127">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="66a53-127">**Type Characters.**</span></span> <span data-ttu-id="66a53-128">`Byte` has no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="66a53-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="66a53-129">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="66a53-129">**Framework Type.**</span></span> <span data-ttu-id="66a53-130">Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66a53-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="66a53-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="66a53-131">Example</span></span>

 <span data-ttu-id="66a53-132">In the following example, `b` is a `Byte` variable.</span><span class="sxs-lookup"><span data-stu-id="66a53-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="66a53-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span><span class="sxs-lookup"><span data-stu-id="66a53-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="66a53-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a53-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="66a53-135">Types de données</span><span class="sxs-lookup"><span data-stu-id="66a53-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="66a53-136">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="66a53-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="66a53-137">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="66a53-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="66a53-138">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="66a53-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
