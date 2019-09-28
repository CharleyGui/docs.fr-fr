---
title: Fonctions de conversion de types de données (Visual Basic)
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
ms.openlocfilehash: 6b448fa23368f7a0848c44362337b0ccc70b6162
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592075"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="b6419-102">Fonctions de conversion de types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6419-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="b6419-103">Ces fonctions sont compilées Inline, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression.</span><span class="sxs-lookup"><span data-stu-id="b6419-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b6419-104">Il arrive parfois qu’il n’y ait pas d’appel à une procédure pour effectuer la conversion, ce qui améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="b6419-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="b6419-105">Chaque fonction convertit une expression en un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="b6419-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6419-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6419-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="b6419-107">Élément</span><span class="sxs-lookup"><span data-stu-id="b6419-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="b6419-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6419-108">Required.</span></span> <span data-ttu-id="b6419-109">Toute expression du type de données source.</span><span class="sxs-lookup"><span data-stu-id="b6419-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="b6419-110">Type de données de la valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6419-110">Return Value Data Type</span></span>  
 <span data-ttu-id="b6419-111">Le nom de la fonction détermine le type de données de la valeur qu’il retourne, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b6419-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6419-112">Nom de la fonction</span><span class="sxs-lookup"><span data-stu-id="b6419-112">Function name</span></span>|<span data-ttu-id="b6419-113">Type de données de retour</span><span class="sxs-lookup"><span data-stu-id="b6419-113">Return data type</span></span>|<span data-ttu-id="b6419-114">Plage pour l’argument `expression`</span><span class="sxs-lookup"><span data-stu-id="b6419-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="b6419-115">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="b6419-116">Toute expression valide `Char`, `String` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="b6419-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="b6419-117">Byte (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="b6419-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) à <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (non signé); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-119">À partir de Visual Basic 15,8, Visual Basic optimise les performances de la conversion à virgule flottante en octet avec la fonction `CByte` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-120">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="b6419-121">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="b6419-122">Toute expression valide `Char` ou `String` ; seul le premier caractère d’un `String` est converti ; la valeur peut être comprise entre 0 et 65535 (non signé).</span><span class="sxs-lookup"><span data-stu-id="b6419-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="b6419-123">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="b6419-124">Toute représentation valide d’une date et d’une heure.</span><span class="sxs-lookup"><span data-stu-id="b6419-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="b6419-125">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="b6419-126">-1.79769313486231570 e + 308 à-4.94065645841246544 E-324 pour les valeurs négatives ; 4.94065645841246544 e-324 à 1.79769313486231570 E + 308 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="b6419-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="b6419-127">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="b6419-128">+/-79 228 335 pour les nombres à échelle zéro, autrement dit, les nombres sans décimales.</span><span class="sxs-lookup"><span data-stu-id="b6419-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="b6419-129">Pour les nombres avec 28 décimales, la plage est +/-7,9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="b6419-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="b6419-130">Le plus petit nombre non nul possible est 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="b6419-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="b6419-131">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="b6419-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2 147 483 648) à <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="b6419-133">À partir de Visual Basic 15,8, Visual Basic optimise les performances de la conversion à virgule flottante en valeur entière avec la fonction `CInt` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-134">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="b6419-135">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="b6419-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) à <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-137">À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 64 bits avec la fonction `CLng` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-138">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="b6419-139">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="b6419-140">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="b6419-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="b6419-141">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="b6419-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) à <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-143">À partir de Visual Basic 15,8, Visual Basic optimise les performances de la conversion à virgule flottante en octet signé avec la fonction `CSByte` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-144">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="b6419-145">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="b6419-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) à <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-147">À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 16 bits avec la fonction `CShort` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-148">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="b6419-149">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="b6419-150">-3.402823 e + 38 à-1.401298 E-45 pour les valeurs négatives ; 1.401298 e-45 à 3.402823 E + 38 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="b6419-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="b6419-151">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="b6419-152">Retourne pour `CStr` dépend de l’argument `expression`.</span><span class="sxs-lookup"><span data-stu-id="b6419-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="b6419-153">Consultez [valeurs de retour pour la fonction CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="b6419-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="b6419-154">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="b6419-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) à <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (non signé); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-156">À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en non signée avec la fonction `CUInt` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-157">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="b6419-158">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="b6419-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) à <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (non signé); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-160">À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion de virgule flottante en valeur entière non signée avec la fonction `CULng` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-161">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="b6419-162">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="b6419-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="b6419-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) à <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (non signé); les parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6419-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b6419-164">À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 16 bits non signé avec la fonction `CUShort` ; Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b6419-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b6419-165">Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="b6419-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="b6419-166"><sup>1</sup> les parties fractionnaires peuvent être soumises à un type spécial d’arrondi appelé « *arrondi bancaire*».</span><span class="sxs-lookup"><span data-stu-id="b6419-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="b6419-167">Pour plus d’informations, consultez « Remarques ».</span><span class="sxs-lookup"><span data-stu-id="b6419-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6419-168">Notes</span><span class="sxs-lookup"><span data-stu-id="b6419-168">Remarks</span></span>  
 <span data-ttu-id="b6419-169">En règle générale, vous devez utiliser les fonctions de conversion de type Visual Basic de préférence aux méthodes de .NET Framework telles que `ToString()`, soit sur la classe <xref:System.Convert>, soit sur une structure ou une classe de type individuelle.</span><span class="sxs-lookup"><span data-stu-id="b6419-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="b6419-170">Les fonctions Visual Basic sont conçues pour une interaction optimale avec Visual Basic Code, et elles rendent également votre code source plus concis et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="b6419-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="b6419-171">En outre, les méthodes de conversion .NET Framework ne produisent pas toujours les mêmes résultats que les fonctions Visual Basic, par exemple lors de la conversion de `Boolean` en `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b6419-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="b6419-172">Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6419-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  

<span data-ttu-id="b6419-173">À partir de Visual Basic 15,8, les performances de la conversion de virgule flottante en nombres entiers sont optimisées quand vous transmettez la valeur <xref:System.Single> ou <xref:System.Double> retournée par les méthodes suivantes à l’une des fonctions de conversion d’entiers (`CByte`, `CShort`, `CInt` @no__ t-5, `CSByte`, `CUShort`, `CUInt`, `CULng`) :</span><span class="sxs-lookup"><span data-stu-id="b6419-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="b6419-174">Cette optimisation permet au code qui effectue un grand nombre de conversions entières de s’exécuter jusqu’à deux fois plus vite.</span><span class="sxs-lookup"><span data-stu-id="b6419-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="b6419-175">L’exemple suivant illustre ces conversions à virgule flottante, à virgule flottante optimisées :</span><span class="sxs-lookup"><span data-stu-id="b6419-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="b6419-176">Comportement</span><span class="sxs-lookup"><span data-stu-id="b6419-176">Behavior</span></span>  
  
- <span data-ttu-id="b6419-177">**Contrainte.**</span><span class="sxs-lookup"><span data-stu-id="b6419-177">**Coercion.**</span></span> <span data-ttu-id="b6419-178">En général, vous pouvez utiliser les fonctions de conversion de type de données pour forcer le résultat d’une opération sur un type de données particulier plutôt que sur le type de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="b6419-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="b6419-179">Par exemple, utilisez `CDec` pour forcer l’arithmétique décimale dans les cas où une simple précision, une double précision ou une opération arithmétique sur les entiers aurait normalement lieu.</span><span class="sxs-lookup"><span data-stu-id="b6419-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
- <span data-ttu-id="b6419-180">**Échec des conversions.**</span><span class="sxs-lookup"><span data-stu-id="b6419-180">**Failed Conversions.**</span></span> <span data-ttu-id="b6419-181">Si le `expression` passé à la fonction est en dehors de la plage du type de données vers lequel il doit être converti, une <xref:System.OverflowException> se produit.</span><span class="sxs-lookup"><span data-stu-id="b6419-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
- <span data-ttu-id="b6419-182">**Parties fractionnaires.**</span><span class="sxs-lookup"><span data-stu-id="b6419-182">**Fractional Parts.**</span></span> <span data-ttu-id="b6419-183">Quand vous convertissez une valeur non intégrale en type intégral, les fonctions de conversion d’entier (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` et `CUShort`) suppriment la partie fractionnaire et arrondissent la valeur à l’entier le plus proche.</span><span class="sxs-lookup"><span data-stu-id="b6419-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="b6419-184">Si la partie fractionnaire est exactement 0,5, les fonctions de conversion d’entiers l’arrondissent à l’entier pair le plus proche.</span><span class="sxs-lookup"><span data-stu-id="b6419-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="b6419-185">Par exemple, 0,5 est arrondi à 0, et 1,5 et 2,5 à 2.</span><span class="sxs-lookup"><span data-stu-id="b6419-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="b6419-186">C’est ce que l’on appelle parfois *l’arrondi de Banker*, et son objectif est de compenser un biais qui peut s’accumuler lors de l’ajout de nombreux nombres de ce type.</span><span class="sxs-lookup"><span data-stu-id="b6419-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="b6419-187">`CInt` et `CLng` diffèrent des fonctions <xref:Microsoft.VisualBasic.Conversion.Int%2A> et <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, qui tronquent, au lieu de les arrondir, la partie fractionnaire d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="b6419-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="b6419-188">En outre, `Fix` et `Int` retournent toujours une valeur du même type de données que celui que vous transmettez.</span><span class="sxs-lookup"><span data-stu-id="b6419-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
- <span data-ttu-id="b6419-189">**Conversions de date/heure.**</span><span class="sxs-lookup"><span data-stu-id="b6419-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="b6419-190">Utilisez la fonction <xref:Microsoft.VisualBasic.Information.IsDate%2A> pour déterminer si une valeur peut être convertie en date et heure.</span><span class="sxs-lookup"><span data-stu-id="b6419-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="b6419-191">`CDate` reconnaît les littéraux de date et d’heure, mais pas les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="b6419-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="b6419-192">Pour convertir une valeur Visual Basic 6,0 `Date` en valeur `Date` dans Visual Basic 2005 ou versions ultérieures, vous pouvez utiliser la méthode <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6419-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="b6419-193">**Valeurs de date/heure neutres.**</span><span class="sxs-lookup"><span data-stu-id="b6419-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="b6419-194">Le [type de données date](../../../visual-basic/language-reference/data-types/date-data-type.md) contient toujours des informations de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="b6419-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="b6419-195">À des fins de conversion de type, Visual Basic considère que 1/1/0001 (1er janvier de l’année 1) comme étant une *valeur neutre* pour la date, et 00:00:00 (minuit) comme valeur neutre pour le moment.</span><span class="sxs-lookup"><span data-stu-id="b6419-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="b6419-196">Si vous convertissez une valeur `Date` en chaîne, `CStr` n’inclut pas de valeurs neutres dans la chaîne résultante.</span><span class="sxs-lookup"><span data-stu-id="b6419-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="b6419-197">Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en chaîne, le résultat est « 9:30:00 AM ». les informations de date sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="b6419-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="b6419-198">Toutefois, les informations de date sont toujours présentes dans la valeur `Date` d’origine et peuvent être récupérées avec des fonctions telles que la fonction <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6419-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
- <span data-ttu-id="b6419-199">**Sensibilité de la culture.**</span><span class="sxs-lookup"><span data-stu-id="b6419-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="b6419-200">Les fonctions de conversion de type impliquant des chaînes effectuent des conversions basées sur les paramètres de culture actuels de l’application.</span><span class="sxs-lookup"><span data-stu-id="b6419-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="b6419-201">Par exemple, `CDate` reconnaît les formats de date en fonction des paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="b6419-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="b6419-202">Vous devez fournir le jour, le mois et l’année dans le bon ordre pour vos paramètres régionaux, ou la date peut ne pas être interprétée correctement.</span><span class="sxs-lookup"><span data-stu-id="b6419-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="b6419-203">Un format de date longue n’est pas reconnu s’il contient une chaîne de jour de la semaine, par exemple « mercredi ».</span><span class="sxs-lookup"><span data-stu-id="b6419-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="b6419-204">Si vous devez convertir vers ou à partir d’une représentation sous forme de chaîne d’une valeur dans un format autre que celui spécifié par vos paramètres régionaux, vous ne pouvez pas utiliser les fonctions de conversion de type Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b6419-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="b6419-205">Pour ce faire, utilisez les méthodes `ToString(IFormatProvider)` et `Parse(String, IFormatProvider)` du type de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="b6419-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="b6419-206">Par exemple, utilisez <xref:System.Double.Parse%2A?displayProperty=nameWithType> lors de la conversion d’une chaîne en `Double` et utilisez <xref:System.Double.ToString%2A?displayProperty=nameWithType> lors de la conversion d’une valeur de type `Double` en chaîne.</span><span class="sxs-lookup"><span data-stu-id="b6419-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="b6419-207">CType Function</span><span class="sxs-lookup"><span data-stu-id="b6419-207">CType Function</span></span>  
 <span data-ttu-id="b6419-208">La [fonction CType](../../../visual-basic/language-reference/functions/ctype-function.md) accepte un deuxième argument, `typename`, et convertit `expression` en `typename`, où `typename` peut être n’importe quel type de données, structure, classe ou interface pour laquelle il existe une conversion valide.</span><span class="sxs-lookup"><span data-stu-id="b6419-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="b6419-209">Pour obtenir une comparaison entre `CType` et les autres mots clés de conversion de type, consultez l’opérateur [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) et l' [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b6419-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="b6419-210">CBool, exemple</span><span class="sxs-lookup"><span data-stu-id="b6419-210">CBool Example</span></span>  
 <span data-ttu-id="b6419-211">L’exemple suivant utilise la fonction `CBool` pour convertir des expressions en valeurs `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6419-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="b6419-212">Si une expression est évaluée à une valeur différente de zéro, `CBool` retourne `True` ; Sinon, elle retourne `False`.</span><span class="sxs-lookup"><span data-stu-id="b6419-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="b6419-213">CByte, exemple</span><span class="sxs-lookup"><span data-stu-id="b6419-213">CByte Example</span></span>  
 <span data-ttu-id="b6419-214">L’exemple suivant utilise la fonction `CByte` pour convertir une expression en `Byte`.</span><span class="sxs-lookup"><span data-stu-id="b6419-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a><span data-ttu-id="b6419-215">Exemple CChar</span><span class="sxs-lookup"><span data-stu-id="b6419-215">CChar Example</span></span>  
 <span data-ttu-id="b6419-216">L’exemple suivant utilise la fonction `CChar` pour convertir le premier caractère d’une expression `String` en type `Char`.</span><span class="sxs-lookup"><span data-stu-id="b6419-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 <span data-ttu-id="b6419-217">L’argument d’entrée pour `CChar` doit être de type de données `Char` ou `String`.</span><span class="sxs-lookup"><span data-stu-id="b6419-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="b6419-218">Vous ne pouvez pas utiliser `CChar` pour convertir un nombre en caractère, car `CChar` ne peut pas accepter un type de données numérique.</span><span class="sxs-lookup"><span data-stu-id="b6419-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="b6419-219">L’exemple suivant obtient un nombre qui représente un point de code (code de caractère) et le convertit en caractère correspondant.</span><span class="sxs-lookup"><span data-stu-id="b6419-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="b6419-220">Elle utilise la fonction <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> pour obtenir la chaîne de chiffres, `CInt` pour convertir la chaîne en type `Integer`, et `ChrW` pour convertir le nombre en type `Char`.</span><span class="sxs-lookup"><span data-stu-id="b6419-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a><span data-ttu-id="b6419-221">Exemple CDate</span><span class="sxs-lookup"><span data-stu-id="b6419-221">CDate Example</span></span>  
 <span data-ttu-id="b6419-222">L’exemple suivant utilise la fonction `CDate` pour convertir des chaînes en valeurs `Date`.</span><span class="sxs-lookup"><span data-stu-id="b6419-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="b6419-223">En général, les dates et heures de codage en dur en tant que chaînes (comme indiqué dans cet exemple) ne sont pas recommandées.</span><span class="sxs-lookup"><span data-stu-id="b6419-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="b6419-224">Utilisez des littéraux de date et d’heure, tels que #Feb 12, 1969 # et #4:45:23 PM #, à la place.</span><span class="sxs-lookup"><span data-stu-id="b6419-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="b6419-225">Exemple de CDbl</span><span class="sxs-lookup"><span data-stu-id="b6419-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a><span data-ttu-id="b6419-226">Exemple CDec</span><span class="sxs-lookup"><span data-stu-id="b6419-226">CDec Example</span></span>  
 <span data-ttu-id="b6419-227">L’exemple suivant utilise la fonction `CDec` pour convertir une valeur numérique en `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b6419-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a><span data-ttu-id="b6419-228">Exemple CInt</span><span class="sxs-lookup"><span data-stu-id="b6419-228">CInt Example</span></span>  
 <span data-ttu-id="b6419-229">L’exemple suivant utilise la fonction `CInt` pour convertir une valeur en `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b6419-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a><span data-ttu-id="b6419-230">Exemple CLng</span><span class="sxs-lookup"><span data-stu-id="b6419-230">CLng Example</span></span>
 <span data-ttu-id="b6419-231">L’exemple suivant utilise la fonction `CLng` pour convertir des valeurs en `Long`.</span><span class="sxs-lookup"><span data-stu-id="b6419-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a><span data-ttu-id="b6419-232">Exemple CObj</span><span class="sxs-lookup"><span data-stu-id="b6419-232">CObj Example</span></span>  
 <span data-ttu-id="b6419-233">L’exemple suivant utilise la fonction `CObj` pour convertir une valeur numérique en `Object`.</span><span class="sxs-lookup"><span data-stu-id="b6419-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="b6419-234">La variable `Object` elle-même contient uniquement un pointeur de 4 octets, qui pointe vers la valeur `Double` qui lui est assignée.</span><span class="sxs-lookup"><span data-stu-id="b6419-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="b6419-235">Exemple CSByte</span><span class="sxs-lookup"><span data-stu-id="b6419-235">CSByte Example</span></span>  
 <span data-ttu-id="b6419-236">L’exemple suivant utilise la fonction `CSByte` pour convertir une valeur numérique en `SByte`.</span><span class="sxs-lookup"><span data-stu-id="b6419-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a><span data-ttu-id="b6419-237">CShort, exemple</span><span class="sxs-lookup"><span data-stu-id="b6419-237">CShort Example</span></span>  
 <span data-ttu-id="b6419-238">L’exemple suivant utilise la fonction `CShort` pour convertir une valeur numérique en `Short`.</span><span class="sxs-lookup"><span data-stu-id="b6419-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a><span data-ttu-id="b6419-239">CSng, exemple</span><span class="sxs-lookup"><span data-stu-id="b6419-239">CSng Example</span></span>  
 <span data-ttu-id="b6419-240">L’exemple suivant utilise la fonction `CSng` pour convertir des valeurs en `Single`.</span><span class="sxs-lookup"><span data-stu-id="b6419-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a><span data-ttu-id="b6419-241">Exemple CStr</span><span class="sxs-lookup"><span data-stu-id="b6419-241">CStr Example</span></span>  
 <span data-ttu-id="b6419-242">L’exemple suivant utilise la fonction `CStr` pour convertir une valeur numérique en `String`.</span><span class="sxs-lookup"><span data-stu-id="b6419-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 <span data-ttu-id="b6419-243">L’exemple suivant utilise la fonction `CStr` pour convertir les valeurs `Date` en valeurs `String`.</span><span class="sxs-lookup"><span data-stu-id="b6419-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b6419-244">`CStr` affiche toujours une valeur `Date` au format abrégé standard pour les paramètres régionaux actuels, par exemple, « 6/15/2003 4:35:47 PM ».</span><span class="sxs-lookup"><span data-stu-id="b6419-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="b6419-245">Toutefois, `CStr` supprime les *valeurs neutres* de 1/1/0001 pour la date et 00:00:00 pour l’heure.</span><span class="sxs-lookup"><span data-stu-id="b6419-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="b6419-246">Pour plus d’informations sur les valeurs retournées par `CStr`, consultez [valeurs de retour pour la fonction CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="b6419-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="b6419-247">Exemple CUInt</span><span class="sxs-lookup"><span data-stu-id="b6419-247">CUInt Example</span></span>  
 <span data-ttu-id="b6419-248">L’exemple suivant utilise la fonction `CUInt` pour convertir une valeur numérique en `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="b6419-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a><span data-ttu-id="b6419-249">Exemple CULng</span><span class="sxs-lookup"><span data-stu-id="b6419-249">CULng Example</span></span>  
 <span data-ttu-id="b6419-250">L’exemple suivant utilise la fonction `CULng` pour convertir une valeur numérique en `ULong`.</span><span class="sxs-lookup"><span data-stu-id="b6419-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a><span data-ttu-id="b6419-251">Exemple CUShort</span><span class="sxs-lookup"><span data-stu-id="b6419-251">CUShort Example</span></span>  
 <span data-ttu-id="b6419-252">L’exemple suivant utilise la fonction `CUShort` pour convertir une valeur numérique en `UShort`.</span><span class="sxs-lookup"><span data-stu-id="b6419-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="b6419-253">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6419-253">See also</span></span>

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
- [<span data-ttu-id="b6419-254">Fonctions de conversion</span><span class="sxs-lookup"><span data-stu-id="b6419-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="b6419-255">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6419-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
