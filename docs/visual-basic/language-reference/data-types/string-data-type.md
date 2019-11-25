---
title: String, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: c2c6f9632646c432abb7b6da8887253e526cc994
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343909"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="78164-102">String, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78164-102">String Data Type (Visual Basic)</span></span>

<span data-ttu-id="78164-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span><span class="sxs-lookup"><span data-stu-id="78164-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="78164-104">Each *code point*, or character code, represents a single Unicode character.</span><span class="sxs-lookup"><span data-stu-id="78164-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="78164-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="78164-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78164-106">Notes</span><span class="sxs-lookup"><span data-stu-id="78164-106">Remarks</span></span>  

 <span data-ttu-id="78164-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span><span class="sxs-lookup"><span data-stu-id="78164-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="78164-108">The default value of `String` is `Nothing` (a null reference).</span><span class="sxs-lookup"><span data-stu-id="78164-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="78164-109">Note that this is not the same as the empty string (value `""`).</span><span class="sxs-lookup"><span data-stu-id="78164-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="78164-110">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="78164-110">Unicode Characters</span></span>  

 <span data-ttu-id="78164-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span><span class="sxs-lookup"><span data-stu-id="78164-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="78164-112">These first 128 code points are the same as those the ASCII character set defines.</span><span class="sxs-lookup"><span data-stu-id="78164-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="78164-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span><span class="sxs-lookup"><span data-stu-id="78164-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="78164-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span><span class="sxs-lookup"><span data-stu-id="78164-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="78164-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span><span class="sxs-lookup"><span data-stu-id="78164-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="78164-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span><span class="sxs-lookup"><span data-stu-id="78164-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="78164-117">Exigences relatives au format</span><span class="sxs-lookup"><span data-stu-id="78164-117">Format Requirements</span></span>  

 <span data-ttu-id="78164-118">You must enclose a `String` literal within quotation marks (`" "`).</span><span class="sxs-lookup"><span data-stu-id="78164-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="78164-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span><span class="sxs-lookup"><span data-stu-id="78164-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="78164-120">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="78164-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="78164-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span><span class="sxs-lookup"><span data-stu-id="78164-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="78164-122">String Manipulations</span><span class="sxs-lookup"><span data-stu-id="78164-122">String Manipulations</span></span>  

 <span data-ttu-id="78164-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span><span class="sxs-lookup"><span data-stu-id="78164-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="78164-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span><span class="sxs-lookup"><span data-stu-id="78164-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="78164-125">The `String` variable then points to the new string.</span><span class="sxs-lookup"><span data-stu-id="78164-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="78164-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span><span class="sxs-lookup"><span data-stu-id="78164-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="78164-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span><span class="sxs-lookup"><span data-stu-id="78164-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="78164-128">A string created by another component might be padded with leading or trailing spaces.</span><span class="sxs-lookup"><span data-stu-id="78164-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="78164-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span><span class="sxs-lookup"><span data-stu-id="78164-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="78164-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="78164-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="78164-131">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="78164-131">Programming Tips</span></span>  
  
- <span data-ttu-id="78164-132">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="78164-132">**Negative Numbers.**</span></span> <span data-ttu-id="78164-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span><span class="sxs-lookup"><span data-stu-id="78164-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="78164-134">In any case, you should not use `String` to hold numeric values.</span><span class="sxs-lookup"><span data-stu-id="78164-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="78164-135">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="78164-135">**Interop Considerations.**</span></span> <span data-ttu-id="78164-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span><span class="sxs-lookup"><span data-stu-id="78164-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="78164-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="78164-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="78164-138">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="78164-138">**Type Characters.**</span></span> <span data-ttu-id="78164-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span><span class="sxs-lookup"><span data-stu-id="78164-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="78164-140">`String` has no literal type character.</span><span class="sxs-lookup"><span data-stu-id="78164-140">`String` has no literal type character.</span></span> <span data-ttu-id="78164-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span><span class="sxs-lookup"><span data-stu-id="78164-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="78164-142">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="78164-142">**Framework Type.**</span></span> <span data-ttu-id="78164-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span><span class="sxs-lookup"><span data-stu-id="78164-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78164-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78164-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="78164-145">Types de données</span><span class="sxs-lookup"><span data-stu-id="78164-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="78164-146">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="78164-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="78164-147">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="78164-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="78164-148">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="78164-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="78164-149">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="78164-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="78164-150">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="78164-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
