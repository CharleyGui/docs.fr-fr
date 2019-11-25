---
title: Considérations sur les surcharges de procédures
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351012"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="b0a8c-102">Considérations sur les surcharges de procédures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0a8c-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="b0a8c-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="b0a8c-104">This usually means each version must specify a different parameter list.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="b0a8c-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="b0a8c-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="b0a8c-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="b0a8c-107">Two overloads cannot differ only in that one has a return value and the other does not.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="b0a8c-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="b0a8c-109">However, you cannot overload a procedure with a property, or vice versa.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="b0a8c-110">Alternatives to Overloaded Versions</span><span class="sxs-lookup"><span data-stu-id="b0a8c-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="b0a8c-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="b0a8c-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="b0a8c-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="b0a8c-114">Overloads and Optional Arguments</span><span class="sxs-lookup"><span data-stu-id="b0a8c-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="b0a8c-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="b0a8c-116">When to Use Overloaded Versions</span><span class="sxs-lookup"><span data-stu-id="b0a8c-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="b0a8c-117">You can consider defining a series of overloaded versions in the following cases:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="b0a8c-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="b0a8c-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="b0a8c-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="b0a8c-121">When to Use Optional Parameters</span><span class="sxs-lookup"><span data-stu-id="b0a8c-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="b0a8c-122">You might prefer one or more optional parameters in the following cases:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="b0a8c-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="b0a8c-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="b0a8c-125">For more information, see [Optional Parameters](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b0a8c-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="b0a8c-126">Overloads and ParamArrays</span><span class="sxs-lookup"><span data-stu-id="b0a8c-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="b0a8c-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="b0a8c-128">When to Use Overloaded Versions</span><span class="sxs-lookup"><span data-stu-id="b0a8c-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="b0a8c-129">You can consider defining a series of overloaded versions in the following cases:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="b0a8c-130">You know that the calling code never passes more than a small number of values to the parameter array.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="b0a8c-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="b0a8c-132">The calling code can pass values of different data types.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="b0a8c-133">When to Use a Parameter Array</span><span class="sxs-lookup"><span data-stu-id="b0a8c-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="b0a8c-134">You are better served by a `ParamArray` parameter in the following cases:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="b0a8c-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="b0a8c-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="b0a8c-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="b0a8c-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="b0a8c-138">Implicit Overloads for Optional Parameters</span><span class="sxs-lookup"><span data-stu-id="b0a8c-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="b0a8c-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="b0a8c-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="b0a8c-141">The following declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="b0a8c-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="b0a8c-143">Implicit Overloads for a ParamArray Parameter</span><span class="sxs-lookup"><span data-stu-id="b0a8c-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="b0a8c-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="b0a8c-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="b0a8c-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="b0a8c-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span><span class="sxs-lookup"><span data-stu-id="b0a8c-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="b0a8c-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span><span class="sxs-lookup"><span data-stu-id="b0a8c-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="b0a8c-148">The following declarations illustrate these implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="b0a8c-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="b0a8c-150">However, you can use the signatures of the other implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="b0a8c-151">The following declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="b0a8c-152">Typeless Programming as an Alternative to Overloading</span><span class="sxs-lookup"><span data-stu-id="b0a8c-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="b0a8c-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="b0a8c-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="b0a8c-155">Then you do not have to declare the parameter's data type.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="b0a8c-156">However, this approach has the following disadvantages compared to overloading:</span><span class="sxs-lookup"><span data-stu-id="b0a8c-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="b0a8c-157">Typeless programming produces less efficient execution code.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="b0a8c-158">The procedure must test for every data type it anticipates being passed.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="b0a8c-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span><span class="sxs-lookup"><span data-stu-id="b0a8c-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a8c-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0a8c-160">See also</span></span>

- [<span data-ttu-id="b0a8c-161">Procédures</span><span class="sxs-lookup"><span data-stu-id="b0a8c-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b0a8c-162">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b0a8c-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b0a8c-163">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="b0a8c-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="b0a8c-164">Guide pratique : définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b0a8c-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="b0a8c-165">Guide pratique : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="b0a8c-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="b0a8c-166">Guide pratique : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="b0a8c-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="b0a8c-167">Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="b0a8c-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="b0a8c-168">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="b0a8c-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="b0a8c-169">Surcharges</span><span class="sxs-lookup"><span data-stu-id="b0a8c-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
