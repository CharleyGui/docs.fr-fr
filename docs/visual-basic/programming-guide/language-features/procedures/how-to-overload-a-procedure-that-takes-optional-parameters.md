---
title: 'Comment : surcharger une procédure qui accepte des paramètres optionnels'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350862"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="ec274-102">Comment : surcharger une procédure qui accepte des paramètres optionnels (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec274-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="ec274-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="ec274-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="ec274-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ec274-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="ec274-105">One Optional Parameter</span><span class="sxs-lookup"><span data-stu-id="ec274-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="ec274-106">To overload a procedure that takes one optional parameter</span><span class="sxs-lookup"><span data-stu-id="ec274-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="ec274-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span><span class="sxs-lookup"><span data-stu-id="ec274-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="ec274-108">Do not use the `Optional` keyword in this overloaded version.</span><span class="sxs-lookup"><span data-stu-id="ec274-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="ec274-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="ec274-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="ec274-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span><span class="sxs-lookup"><span data-stu-id="ec274-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="ec274-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="ec274-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="ec274-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span><span class="sxs-lookup"><span data-stu-id="ec274-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="ec274-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span><span class="sxs-lookup"><span data-stu-id="ec274-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="ec274-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="ec274-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="ec274-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span><span class="sxs-lookup"><span data-stu-id="ec274-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="ec274-116">Multiple Optional Parameters</span><span class="sxs-lookup"><span data-stu-id="ec274-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="ec274-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span><span class="sxs-lookup"><span data-stu-id="ec274-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="ec274-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span><span class="sxs-lookup"><span data-stu-id="ec274-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="ec274-119">As the number of optional parameters increases, the complexity of the overloading increases.</span><span class="sxs-lookup"><span data-stu-id="ec274-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="ec274-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span><span class="sxs-lookup"><span data-stu-id="ec274-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="ec274-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span><span class="sxs-lookup"><span data-stu-id="ec274-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="ec274-122">To overload a procedure that takes more than one optional parameter</span><span class="sxs-lookup"><span data-stu-id="ec274-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="ec274-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span><span class="sxs-lookup"><span data-stu-id="ec274-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="ec274-124">An unacceptable combination might arise if one optional parameter depends on another.</span><span class="sxs-lookup"><span data-stu-id="ec274-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="ec274-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span><span class="sxs-lookup"><span data-stu-id="ec274-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="ec274-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span><span class="sxs-lookup"><span data-stu-id="ec274-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="ec274-127">Do not use the `Optional` keyword.</span><span class="sxs-lookup"><span data-stu-id="ec274-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="ec274-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="ec274-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="ec274-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span><span class="sxs-lookup"><span data-stu-id="ec274-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="ec274-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="ec274-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec274-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec274-131">See also</span></span>

- [<span data-ttu-id="ec274-132">Procédures</span><span class="sxs-lookup"><span data-stu-id="ec274-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ec274-133">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="ec274-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ec274-134">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="ec274-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="ec274-135">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="ec274-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="ec274-136">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="ec274-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="ec274-137">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="ec274-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="ec274-138">Guide pratique : définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="ec274-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="ec274-139">Guide pratique : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="ec274-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="ec274-140">Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="ec274-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="ec274-141">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="ec274-141">Overload Resolution</span></span>](./overload-resolution.md)
