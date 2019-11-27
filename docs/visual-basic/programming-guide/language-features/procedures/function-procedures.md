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
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="eadcc-102">Procédures Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadcc-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="eadcc-103">Une procédure `Function` est une série d’instructions Visual Basic délimitée par les instructions `Function` et `End Function`.</span><span class="sxs-lookup"><span data-stu-id="eadcc-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="eadcc-104">La procédure `Function` effectue une tâche, puis retourne le contrôle au code appelant.</span><span class="sxs-lookup"><span data-stu-id="eadcc-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="eadcc-105">Quand elle retourne le contrôle, elle retourne également une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="eadcc-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="eadcc-106">Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après l’instruction `Function` et en se terminant par la première instruction `End Function`, `Exit Function`ou `Return` rencontrée.</span><span class="sxs-lookup"><span data-stu-id="eadcc-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="eadcc-107">Vous pouvez définir une procédure `Function` dans un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="eadcc-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="eadcc-108">Il est `Public` par défaut, ce qui signifie que vous pouvez l’appeler à partir de n’importe quel endroit de votre application ayant accès au module, à la classe ou à la structure dans laquelle vous l’avez défini.</span><span class="sxs-lookup"><span data-stu-id="eadcc-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="eadcc-109">Une procédure `Function` peut prendre des arguments, tels que des constantes, des variables ou des expressions, qui lui sont passés par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="eadcc-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="eadcc-110">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="eadcc-110">Declaration Syntax</span></span>  
 <span data-ttu-id="eadcc-111">La syntaxe de la déclaration d’une procédure `Function` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="eadcc-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="eadcc-112">Les *modificateurs* peuvent spécifier le niveau d’accès et les informations relatives à la surcharge, au remplacement, au partage et à l’occultation.</span><span class="sxs-lookup"><span data-stu-id="eadcc-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="eadcc-113">Pour plus d’informations, consultez [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eadcc-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="eadcc-114">Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eadcc-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="eadcc-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="eadcc-115">Data Type</span></span>  
 <span data-ttu-id="eadcc-116">Chaque `Function` procédure a un type de données, comme c’est le cas pour chaque variable.</span><span class="sxs-lookup"><span data-stu-id="eadcc-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="eadcc-117">Ce type de données est spécifié par la clause `As` dans l’instruction `Function` et détermine le type de données de la valeur renvoyée par la fonction au code appelant.</span><span class="sxs-lookup"><span data-stu-id="eadcc-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="eadcc-118">Les exemples de déclarations suivants illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="eadcc-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="eadcc-119">Pour plus d’informations, consultez « parts » dans l' [instruction de fonction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eadcc-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="eadcc-120">Retour de valeurs</span><span class="sxs-lookup"><span data-stu-id="eadcc-120">Returning Values</span></span>  
 <span data-ttu-id="eadcc-121">La valeur qu’une procédure de `Function` renvoie au code appelant est appelée sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="eadcc-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="eadcc-122">La procédure retourne cette valeur de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="eadcc-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="eadcc-123">Elle utilise l’instruction `Return` pour spécifier la valeur de retour et retourne immédiatement le contrôle au programme appelant.</span><span class="sxs-lookup"><span data-stu-id="eadcc-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="eadcc-124">L’exemple suivant illustre ces actions.</span><span class="sxs-lookup"><span data-stu-id="eadcc-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="eadcc-125">Elle assigne une valeur à son propre nom de fonction dans une ou plusieurs instructions de la procédure.</span><span class="sxs-lookup"><span data-stu-id="eadcc-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="eadcc-126">Le contrôle ne retourne pas au programme appelant tant qu’une instruction `Exit Function` ou `End Function` n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="eadcc-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="eadcc-127">L’exemple suivant illustre ces actions.</span><span class="sxs-lookup"><span data-stu-id="eadcc-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="eadcc-128">L’avantage de l’attribution de la valeur de retour au nom de la fonction est que le contrôle ne retourne pas de la procédure tant qu’il n’a pas rencontré d’instruction `Exit Function` ou `End Function`.</span><span class="sxs-lookup"><span data-stu-id="eadcc-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="eadcc-129">Cela vous permet d’attribuer une valeur préliminaire et de l’ajuster ultérieurement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="eadcc-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="eadcc-130">Pour plus d’informations sur le retour de valeurs, consultez [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eadcc-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="eadcc-131">Pour plus d’informations sur le retour de tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="eadcc-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="eadcc-132">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="eadcc-132">Calling Syntax</span></span>  
 <span data-ttu-id="eadcc-133">Pour appeler une procédure `Function`, vous devez inclure son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="eadcc-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="eadcc-134">Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="eadcc-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="eadcc-135">Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="eadcc-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="eadcc-136">La syntaxe d’un appel à une procédure `Function` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="eadcc-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="eadcc-137">*lvalue*`=`*nomfonction* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="eadcc-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="eadcc-138">`If ((` *nomfonction* `[(` *`)] / 3) <=`* *expression* `) Then`</span><span class="sxs-lookup"><span data-stu-id="eadcc-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="eadcc-139">Lorsque vous appelez une procédure `Function`, il n’est pas nécessaire d’utiliser sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="eadcc-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="eadcc-140">Si vous ne le faites pas, toutes les actions de la fonction sont exécutées, mais la valeur de retour est ignorée.</span><span class="sxs-lookup"><span data-stu-id="eadcc-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="eadcc-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> est souvent appelée de cette manière.</span><span class="sxs-lookup"><span data-stu-id="eadcc-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="eadcc-142">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="eadcc-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="eadcc-143">La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.</span><span class="sxs-lookup"><span data-stu-id="eadcc-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="eadcc-144">L’exemple suivant montre un appel typique à `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="eadcc-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="eadcc-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eadcc-145">See also</span></span>

- [<span data-ttu-id="eadcc-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="eadcc-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eadcc-147">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="eadcc-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="eadcc-148">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="eadcc-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="eadcc-149">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="eadcc-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="eadcc-150">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="eadcc-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eadcc-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="eadcc-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="eadcc-152">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="eadcc-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="eadcc-153">Guide pratique : retourner une valeur d’une procédure</span><span class="sxs-lookup"><span data-stu-id="eadcc-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="eadcc-154">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="eadcc-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
