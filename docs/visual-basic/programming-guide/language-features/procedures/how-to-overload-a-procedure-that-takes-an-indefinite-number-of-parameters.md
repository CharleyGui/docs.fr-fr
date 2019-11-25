---
title: 'Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345849"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="02154-102">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02154-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="02154-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span><span class="sxs-lookup"><span data-stu-id="02154-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="02154-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="02154-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="02154-105">To overload a procedure that takes a variable number of parameters</span><span class="sxs-lookup"><span data-stu-id="02154-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="02154-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span><span class="sxs-lookup"><span data-stu-id="02154-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="02154-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="02154-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="02154-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span><span class="sxs-lookup"><span data-stu-id="02154-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="02154-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span><span class="sxs-lookup"><span data-stu-id="02154-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="02154-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span><span class="sxs-lookup"><span data-stu-id="02154-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="02154-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span><span class="sxs-lookup"><span data-stu-id="02154-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="02154-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="02154-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="02154-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span><span class="sxs-lookup"><span data-stu-id="02154-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="02154-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="02154-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02154-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="02154-115">Example</span></span>  
 <span data-ttu-id="02154-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span><span class="sxs-lookup"><span data-stu-id="02154-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="02154-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span><span class="sxs-lookup"><span data-stu-id="02154-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="02154-118">However, you can use the signatures of the other implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="02154-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="02154-119">The following declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="02154-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="02154-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span><span class="sxs-lookup"><span data-stu-id="02154-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="02154-121">Visual Basic passes control to the version matching the calling argument list.</span><span class="sxs-lookup"><span data-stu-id="02154-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02154-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="02154-122">Compiling the Code</span></span>  
 <span data-ttu-id="02154-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="02154-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="02154-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="02154-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="02154-125">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02154-125">.NET Framework Security</span></span>  
 <span data-ttu-id="02154-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span><span class="sxs-lookup"><span data-stu-id="02154-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="02154-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span><span class="sxs-lookup"><span data-stu-id="02154-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02154-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02154-128">See also</span></span>

- [<span data-ttu-id="02154-129">Procédures</span><span class="sxs-lookup"><span data-stu-id="02154-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="02154-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="02154-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="02154-131">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="02154-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="02154-132">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="02154-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="02154-133">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="02154-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="02154-134">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="02154-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="02154-135">Guide pratique : définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="02154-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="02154-136">Guide pratique : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="02154-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="02154-137">Guide pratique : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="02154-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="02154-138">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="02154-138">Overload Resolution</span></span>](./overload-resolution.md)
