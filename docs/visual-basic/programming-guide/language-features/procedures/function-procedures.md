---
title: procédures Function
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388749"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="b8816-102">Function procedures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8816-102">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="b8816-103">Une `Function` procédure est une série d’instructions Visual Basic délimitées par les `Function` `End Function` instructions et.</span><span class="sxs-lookup"><span data-stu-id="b8816-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="b8816-104">La `Function` procédure effectue une tâche, puis retourne le contrôle au code appelant.</span><span class="sxs-lookup"><span data-stu-id="b8816-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="b8816-105">Quand elle retourne le contrôle, elle retourne également une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="b8816-105">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="b8816-106">Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après l' `Function` instruction et en terminant par la première `End Function` `Exit Function` instruction, ou `Return` rencontrée.</span><span class="sxs-lookup"><span data-stu-id="b8816-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="b8816-107">Vous pouvez définir une `Function` procédure dans un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="b8816-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="b8816-108">C’est `Public` par défaut le cas, ce qui signifie que vous pouvez l’appeler à partir de n’importe quel endroit de votre application ayant accès au module, à la classe ou à la structure dans laquelle vous l’avez défini.</span><span class="sxs-lookup"><span data-stu-id="b8816-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="b8816-109">Une `Function` procédure peut prendre des arguments, tels que des constantes, des variables ou des expressions, qui lui sont passés par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="b8816-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="b8816-110">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="b8816-110">Declaration syntax</span></span>

<span data-ttu-id="b8816-111">La syntaxe permettant de déclarer une `Function` procédure est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b8816-111">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="b8816-112">Les *modificateurs* peuvent spécifier le niveau d’accès et les informations relatives à la surcharge, au remplacement, au partage et à l’occultation.</span><span class="sxs-lookup"><span data-stu-id="b8816-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="b8816-113">Pour plus d’informations, consultez [Function, instruction](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8816-113">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="b8816-114">Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b8816-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="b8816-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="b8816-115">Data type</span></span>

<span data-ttu-id="b8816-116">Chaque `Function` procédure a un type de données, comme c’est le cas pour chaque variable.</span><span class="sxs-lookup"><span data-stu-id="b8816-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="b8816-117">Ce type de données est spécifié par la `As` clause dans l' `Function` instruction et détermine le type de données de la valeur que la fonction retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="b8816-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="b8816-118">Les exemples de déclarations suivants illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="b8816-118">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="b8816-119">Pour plus d’informations, consultez « parts » dans l' [instruction de fonction](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8816-119">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="b8816-120">Retour de valeurs</span><span class="sxs-lookup"><span data-stu-id="b8816-120">Returning values</span></span>

<span data-ttu-id="b8816-121">La valeur `Function` qu’une procédure renvoie au code appelant est appelée sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b8816-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="b8816-122">La procédure retourne cette valeur de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8816-122">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="b8816-123">Elle utilise l' `Return` instruction pour spécifier la valeur de retour et retourne immédiatement le contrôle au programme appelant.</span><span class="sxs-lookup"><span data-stu-id="b8816-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="b8816-124">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="b8816-124">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="b8816-125">Elle assigne une valeur à son propre nom de fonction dans une ou plusieurs instructions de la procédure.</span><span class="sxs-lookup"><span data-stu-id="b8816-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="b8816-126">Le contrôle ne retourne pas au programme appelant tant qu' `Exit Function` une `End Function` instruction ou n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b8816-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="b8816-127">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="b8816-127">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="b8816-128">L’avantage de l’attribution de la valeur de retour au nom de la fonction est que le contrôle ne retourne pas de la procédure tant qu’il n’a pas rencontré une `Exit Function` `End Function` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="b8816-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="b8816-129">Cela vous permet d’attribuer une valeur préliminaire et de l’ajuster ultérieurement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b8816-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="b8816-130">Pour plus d’informations sur le retour de valeurs, consultez [Function, instruction](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8816-130">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="b8816-131">Pour plus d’informations sur le retour de tableaux, consultez [tableaux](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8816-131">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="b8816-132">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="b8816-132">Calling syntax</span></span>

<span data-ttu-id="b8816-133">Pour appeler une procédure, vous devez `Function` inclure son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="b8816-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="b8816-134">Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b8816-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="b8816-135">Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b8816-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="b8816-136">La syntaxe d’un appel à une `Function` procédure est la suivante.</span><span class="sxs-lookup"><span data-stu-id="b8816-136">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="b8816-137">*lvalue* `=` *nomfonction* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="b8816-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="b8816-138">`If ((`*nomfonction* `[(` *argumentlist* `)] / 3) <=` *expression*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="b8816-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="b8816-139">Lorsque vous appelez une `Function` procédure, il n’est pas nécessaire d’utiliser sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b8816-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="b8816-140">Si vous ne le faites pas, toutes les actions de la fonction sont exécutées, mais la valeur de retour est ignorée.</span><span class="sxs-lookup"><span data-stu-id="b8816-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="b8816-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>est souvent appelée de cette manière.</span><span class="sxs-lookup"><span data-stu-id="b8816-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b8816-142">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="b8816-142">Illustration of declaration and call</span></span>

<span data-ttu-id="b8816-143">La `Function` procédure suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.</span><span class="sxs-lookup"><span data-stu-id="b8816-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="b8816-144">L’exemple suivant montre un appel typique à `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="b8816-144">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="b8816-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8816-145">See also</span></span>

- [<span data-ttu-id="b8816-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="b8816-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b8816-147">Sub, procédures</span><span class="sxs-lookup"><span data-stu-id="b8816-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b8816-148">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="b8816-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b8816-149">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="b8816-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b8816-150">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b8816-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b8816-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="b8816-151">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="b8816-152">Comment : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="b8816-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="b8816-153">Comment : retourner une valeur d'une procédure</span><span class="sxs-lookup"><span data-stu-id="b8816-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="b8816-154">Comment : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="b8816-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
