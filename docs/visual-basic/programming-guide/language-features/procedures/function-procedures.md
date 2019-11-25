---
title: Function, procédures
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341085"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="8a898-102">Procédures Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a898-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="8a898-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span><span class="sxs-lookup"><span data-stu-id="8a898-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="8a898-104">The `Function` procedure performs a task and then returns control to the calling code.</span><span class="sxs-lookup"><span data-stu-id="8a898-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="8a898-105">When it returns control, it also returns a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="8a898-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="8a898-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span><span class="sxs-lookup"><span data-stu-id="8a898-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="8a898-107">You can define a `Function` procedure in a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="8a898-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="8a898-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span><span class="sxs-lookup"><span data-stu-id="8a898-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="8a898-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span><span class="sxs-lookup"><span data-stu-id="8a898-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="8a898-110">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="8a898-110">Declaration Syntax</span></span>  
 <span data-ttu-id="8a898-111">The syntax for declaring a `Function` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="8a898-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="8a898-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span><span class="sxs-lookup"><span data-stu-id="8a898-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="8a898-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8a898-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="8a898-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8a898-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="8a898-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="8a898-115">Data Type</span></span>  
 <span data-ttu-id="8a898-116">Every `Function` procedure has a data type, just as every variable does.</span><span class="sxs-lookup"><span data-stu-id="8a898-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="8a898-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="8a898-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="8a898-118">The following sample declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="8a898-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="8a898-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8a898-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="8a898-120">Returning Values</span><span class="sxs-lookup"><span data-stu-id="8a898-120">Returning Values</span></span>  
 <span data-ttu-id="8a898-121">The value a `Function` procedure sends back to the calling code is called its return value.</span><span class="sxs-lookup"><span data-stu-id="8a898-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="8a898-122">The procedure returns this value in one of two ways:</span><span class="sxs-lookup"><span data-stu-id="8a898-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="8a898-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span><span class="sxs-lookup"><span data-stu-id="8a898-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="8a898-124">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="8a898-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="8a898-125">It assigns a value to its own function name in one or more statements of the procedure.</span><span class="sxs-lookup"><span data-stu-id="8a898-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="8a898-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span><span class="sxs-lookup"><span data-stu-id="8a898-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="8a898-127">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="8a898-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="8a898-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="8a898-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="8a898-129">This allows you to assign a preliminary value and adjust it later if necessary.</span><span class="sxs-lookup"><span data-stu-id="8a898-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="8a898-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8a898-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="8a898-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a898-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="8a898-132">Calling Syntax</span><span class="sxs-lookup"><span data-stu-id="8a898-132">Calling Syntax</span></span>  
 <span data-ttu-id="8a898-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span><span class="sxs-lookup"><span data-stu-id="8a898-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="8a898-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="8a898-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="8a898-135">If no arguments are supplied, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="8a898-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="8a898-136">The syntax for a call to a `Function` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="8a898-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="8a898-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="8a898-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="8a898-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span><span class="sxs-lookup"><span data-stu-id="8a898-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="8a898-139">When you call a `Function` procedure, you do not have to use its return value.</span><span class="sxs-lookup"><span data-stu-id="8a898-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="8a898-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span><span class="sxs-lookup"><span data-stu-id="8a898-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="8a898-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span><span class="sxs-lookup"><span data-stu-id="8a898-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="8a898-142">Illustration of Declaration and Call</span><span class="sxs-lookup"><span data-stu-id="8a898-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="8a898-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span><span class="sxs-lookup"><span data-stu-id="8a898-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="8a898-144">The following example shows a typical call to `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="8a898-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8a898-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a898-145">See also</span></span>

- [<span data-ttu-id="8a898-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="8a898-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8a898-147">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="8a898-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="8a898-148">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="8a898-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="8a898-149">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="8a898-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="8a898-150">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="8a898-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8a898-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="8a898-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="8a898-152">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="8a898-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="8a898-153">Guide pratique : retourner une valeur d’une procédure</span><span class="sxs-lookup"><span data-stu-id="8a898-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="8a898-154">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="8a898-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
