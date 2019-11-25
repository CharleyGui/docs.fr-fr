---
title: Type Conversion Functions
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 3924da6ccbfea00668370f2fbcf4baf289be80db
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349966"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="86253-102">Fonctions de conversion de types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86253-102">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="86253-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span><span class="sxs-lookup"><span data-stu-id="86253-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="86253-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span><span class="sxs-lookup"><span data-stu-id="86253-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="86253-105">Each function coerces an expression to a specific data type.</span><span class="sxs-lookup"><span data-stu-id="86253-105">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="86253-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86253-106">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="86253-107">Élément</span><span class="sxs-lookup"><span data-stu-id="86253-107">Part</span></span>

`expression`  
<span data-ttu-id="86253-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="86253-108">Required.</span></span> <span data-ttu-id="86253-109">Any expression of the source data type.</span><span class="sxs-lookup"><span data-stu-id="86253-109">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="86253-110">Return Value Data Type</span><span class="sxs-lookup"><span data-stu-id="86253-110">Return Value Data Type</span></span>

<span data-ttu-id="86253-111">The function name determines the data type of the value it returns, as shown in the following table.</span><span class="sxs-lookup"><span data-stu-id="86253-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="86253-112">Nom de la fonction</span><span class="sxs-lookup"><span data-stu-id="86253-112">Function name</span></span>|<span data-ttu-id="86253-113">Return data type</span><span class="sxs-lookup"><span data-stu-id="86253-113">Return data type</span></span>|<span data-ttu-id="86253-114">Range for `expression` argument</span><span class="sxs-lookup"><span data-stu-id="86253-114">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="86253-115">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="86253-116">Any valid `Char` or `String` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="86253-116">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="86253-117">Byte (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="86253-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-120">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-120">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="86253-121">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="86253-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span><span class="sxs-lookup"><span data-stu-id="86253-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="86253-123">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="86253-124">Any valid representation of a date and time.</span><span class="sxs-lookup"><span data-stu-id="86253-124">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="86253-125">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="86253-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span><span class="sxs-lookup"><span data-stu-id="86253-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="86253-127">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="86253-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span><span class="sxs-lookup"><span data-stu-id="86253-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="86253-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="86253-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="86253-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="86253-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="86253-131">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="86253-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="86253-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-134">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-134">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="86253-135">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="86253-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-138">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-138">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="86253-139">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="86253-140">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="86253-140">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="86253-141">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="86253-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-144">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-144">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="86253-145">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="86253-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-148">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-148">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="86253-149">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="86253-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span><span class="sxs-lookup"><span data-stu-id="86253-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="86253-151">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="86253-152">Returns for `CStr` depend on the `expression` argument.</span><span class="sxs-lookup"><span data-stu-id="86253-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="86253-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="86253-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="86253-154">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="86253-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-157">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-157">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="86253-158">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="86253-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-161">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-161">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="86253-162">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="86253-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="86253-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86253-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="86253-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="86253-165">See the [CInt Example](#cint-example) section for an example.</span><span class="sxs-lookup"><span data-stu-id="86253-165">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="86253-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span><span class="sxs-lookup"><span data-stu-id="86253-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="86253-167">See "Remarks" for more information.</span><span class="sxs-lookup"><span data-stu-id="86253-167">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="86253-168">Notes</span><span class="sxs-lookup"><span data-stu-id="86253-168">Remarks</span></span>

<span data-ttu-id="86253-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span><span class="sxs-lookup"><span data-stu-id="86253-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="86253-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span><span class="sxs-lookup"><span data-stu-id="86253-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="86253-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="86253-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="86253-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="86253-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="86253-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="86253-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="86253-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span><span class="sxs-lookup"><span data-stu-id="86253-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="86253-175">The following example illustrates these optimized floating-point-to-integer conversions:</span><span class="sxs-lookup"><span data-stu-id="86253-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="86253-176">Comportement</span><span class="sxs-lookup"><span data-stu-id="86253-176">Behavior</span></span>

- <span data-ttu-id="86253-177">**Coercion.**</span><span class="sxs-lookup"><span data-stu-id="86253-177">**Coercion.**</span></span> <span data-ttu-id="86253-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span><span class="sxs-lookup"><span data-stu-id="86253-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="86253-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span><span class="sxs-lookup"><span data-stu-id="86253-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="86253-180">**Failed Conversions.**</span><span class="sxs-lookup"><span data-stu-id="86253-180">**Failed Conversions.**</span></span> <span data-ttu-id="86253-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span><span class="sxs-lookup"><span data-stu-id="86253-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="86253-182">**Fractional Parts.**</span><span class="sxs-lookup"><span data-stu-id="86253-182">**Fractional Parts.**</span></span> <span data-ttu-id="86253-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span><span class="sxs-lookup"><span data-stu-id="86253-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="86253-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span><span class="sxs-lookup"><span data-stu-id="86253-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="86253-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span><span class="sxs-lookup"><span data-stu-id="86253-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="86253-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span><span class="sxs-lookup"><span data-stu-id="86253-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="86253-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span><span class="sxs-lookup"><span data-stu-id="86253-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="86253-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span><span class="sxs-lookup"><span data-stu-id="86253-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="86253-189">**Date/Time Conversions.**</span><span class="sxs-lookup"><span data-stu-id="86253-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="86253-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span><span class="sxs-lookup"><span data-stu-id="86253-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="86253-191">`CDate` recognizes date literals and time literals but not numeric values.</span><span class="sxs-lookup"><span data-stu-id="86253-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="86253-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="86253-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="86253-193">**Neutral Date/Time Values.**</span><span class="sxs-lookup"><span data-stu-id="86253-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="86253-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span><span class="sxs-lookup"><span data-stu-id="86253-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="86253-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span><span class="sxs-lookup"><span data-stu-id="86253-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="86253-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span><span class="sxs-lookup"><span data-stu-id="86253-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="86253-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span><span class="sxs-lookup"><span data-stu-id="86253-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="86253-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span><span class="sxs-lookup"><span data-stu-id="86253-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="86253-199">**Culture Sensitivity.**</span><span class="sxs-lookup"><span data-stu-id="86253-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="86253-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span><span class="sxs-lookup"><span data-stu-id="86253-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="86253-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span><span class="sxs-lookup"><span data-stu-id="86253-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="86253-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span><span class="sxs-lookup"><span data-stu-id="86253-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="86253-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span><span class="sxs-lookup"><span data-stu-id="86253-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="86253-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span><span class="sxs-lookup"><span data-stu-id="86253-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="86253-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span><span class="sxs-lookup"><span data-stu-id="86253-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="86253-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span><span class="sxs-lookup"><span data-stu-id="86253-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="86253-207">CType Function</span><span class="sxs-lookup"><span data-stu-id="86253-207">CType Function</span></span>

<span data-ttu-id="86253-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span><span class="sxs-lookup"><span data-stu-id="86253-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="86253-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="86253-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="86253-210">CBool Example</span><span class="sxs-lookup"><span data-stu-id="86253-210">CBool Example</span></span>

<span data-ttu-id="86253-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span><span class="sxs-lookup"><span data-stu-id="86253-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="86253-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span><span class="sxs-lookup"><span data-stu-id="86253-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="86253-213">CByte Example</span><span class="sxs-lookup"><span data-stu-id="86253-213">CByte Example</span></span>

<span data-ttu-id="86253-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="86253-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="86253-215">CChar Example</span><span class="sxs-lookup"><span data-stu-id="86253-215">CChar Example</span></span>

<span data-ttu-id="86253-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span><span class="sxs-lookup"><span data-stu-id="86253-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="86253-217">The input argument to `CChar` must be of data type `Char` or `String`.</span><span class="sxs-lookup"><span data-stu-id="86253-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="86253-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span><span class="sxs-lookup"><span data-stu-id="86253-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="86253-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span><span class="sxs-lookup"><span data-stu-id="86253-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="86253-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span><span class="sxs-lookup"><span data-stu-id="86253-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="86253-221">CDate Example</span><span class="sxs-lookup"><span data-stu-id="86253-221">CDate Example</span></span>

<span data-ttu-id="86253-222">The following example uses the `CDate` function to convert strings to `Date` values.</span><span class="sxs-lookup"><span data-stu-id="86253-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="86253-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span><span class="sxs-lookup"><span data-stu-id="86253-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="86253-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span><span class="sxs-lookup"><span data-stu-id="86253-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="86253-225">CDbl Example</span><span class="sxs-lookup"><span data-stu-id="86253-225">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="86253-226">CDec Example</span><span class="sxs-lookup"><span data-stu-id="86253-226">CDec Example</span></span>

<span data-ttu-id="86253-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="86253-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="86253-228">CInt Example</span><span class="sxs-lookup"><span data-stu-id="86253-228">CInt Example</span></span>

<span data-ttu-id="86253-229">The following example uses the `CInt` function to convert a value to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="86253-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="86253-230">CLng Example</span><span class="sxs-lookup"><span data-stu-id="86253-230">CLng Example</span></span>

<span data-ttu-id="86253-231">The following example uses the `CLng` function to convert values to `Long`.</span><span class="sxs-lookup"><span data-stu-id="86253-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="86253-232">CObj Example</span><span class="sxs-lookup"><span data-stu-id="86253-232">CObj Example</span></span>

<span data-ttu-id="86253-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span><span class="sxs-lookup"><span data-stu-id="86253-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="86253-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span><span class="sxs-lookup"><span data-stu-id="86253-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="86253-235">CSByte Example</span><span class="sxs-lookup"><span data-stu-id="86253-235">CSByte Example</span></span>

<span data-ttu-id="86253-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span><span class="sxs-lookup"><span data-stu-id="86253-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="86253-237">CShort Example</span><span class="sxs-lookup"><span data-stu-id="86253-237">CShort Example</span></span>

<span data-ttu-id="86253-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span><span class="sxs-lookup"><span data-stu-id="86253-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="86253-239">CSng Example</span><span class="sxs-lookup"><span data-stu-id="86253-239">CSng Example</span></span>

<span data-ttu-id="86253-240">The following example uses the `CSng` function to convert values to `Single`.</span><span class="sxs-lookup"><span data-stu-id="86253-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="86253-241">CStr Example</span><span class="sxs-lookup"><span data-stu-id="86253-241">CStr Example</span></span>

<span data-ttu-id="86253-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span><span class="sxs-lookup"><span data-stu-id="86253-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="86253-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span><span class="sxs-lookup"><span data-stu-id="86253-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="86253-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="86253-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="86253-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span><span class="sxs-lookup"><span data-stu-id="86253-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="86253-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="86253-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="86253-247">CUInt Example</span><span class="sxs-lookup"><span data-stu-id="86253-247">CUInt Example</span></span>

<span data-ttu-id="86253-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="86253-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="86253-249">CULng Example</span><span class="sxs-lookup"><span data-stu-id="86253-249">CULng Example</span></span>

<span data-ttu-id="86253-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span><span class="sxs-lookup"><span data-stu-id="86253-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="86253-251">CUShort Example</span><span class="sxs-lookup"><span data-stu-id="86253-251">CUShort Example</span></span>

<span data-ttu-id="86253-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span><span class="sxs-lookup"><span data-stu-id="86253-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="86253-253">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86253-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="86253-254">Fonctions de conversion</span><span class="sxs-lookup"><span data-stu-id="86253-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="86253-255">Type Conversions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86253-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
