---
title: Function, instruction
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345922"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="de698-102">Function, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de698-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="de698-103">Declares the name, parameters, and code that define a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="de698-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de698-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="de698-105">Composants</span><span class="sxs-lookup"><span data-stu-id="de698-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="de698-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-106">Optional.</span></span> <span data-ttu-id="de698-107">See [Attribute List](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="de698-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="de698-108">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-108">Optional.</span></span> <span data-ttu-id="de698-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="de698-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="de698-110">Public</span><span class="sxs-lookup"><span data-stu-id="de698-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="de698-111">Protected</span><span class="sxs-lookup"><span data-stu-id="de698-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="de698-112">Friend</span><span class="sxs-lookup"><span data-stu-id="de698-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="de698-113">Private</span><span class="sxs-lookup"><span data-stu-id="de698-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="de698-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="de698-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="de698-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="de698-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="de698-116">Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="de698-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="de698-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-117">Optional.</span></span> <span data-ttu-id="de698-118">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="de698-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="de698-119">Surcharges</span><span class="sxs-lookup"><span data-stu-id="de698-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="de698-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="de698-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="de698-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="de698-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="de698-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="de698-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="de698-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="de698-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="de698-124">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-124">Optional.</span></span> <span data-ttu-id="de698-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="de698-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="de698-126">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-126">Optional.</span></span> <span data-ttu-id="de698-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="de698-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="de698-128">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-128">Optional.</span></span> <span data-ttu-id="de698-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="de698-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="de698-130">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-130">Optional.</span></span> <span data-ttu-id="de698-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="de698-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="de698-132">Requis.</span><span class="sxs-lookup"><span data-stu-id="de698-132">Required.</span></span> <span data-ttu-id="de698-133">Name of the procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-133">Name of the procedure.</span></span> <span data-ttu-id="de698-134">Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="de698-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="de698-135">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-135">Optional.</span></span> <span data-ttu-id="de698-136">List of type parameters for a generic procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="de698-137">See [Type List](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="de698-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="de698-138">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-138">Optional.</span></span> <span data-ttu-id="de698-139">List of local variable names representing the parameters of this procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="de698-140">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="de698-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="de698-141">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="de698-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="de698-142">Data type of the value returned by this procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="de698-143">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-143">Optional.</span></span> <span data-ttu-id="de698-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="de698-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="de698-145">See [Implements Statement](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de698-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="de698-146">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="de698-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="de698-147">Liste des procédures `Function` en cours d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="de698-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="de698-148">Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="de698-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="de698-149">Élément</span><span class="sxs-lookup"><span data-stu-id="de698-149">Part</span></span>|<span data-ttu-id="de698-150">Description</span><span class="sxs-lookup"><span data-stu-id="de698-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="de698-151">Requis.</span><span class="sxs-lookup"><span data-stu-id="de698-151">Required.</span></span> <span data-ttu-id="de698-152">Name of an interface implemented by this procedure's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="de698-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="de698-153">Requis.</span><span class="sxs-lookup"><span data-stu-id="de698-153">Required.</span></span> <span data-ttu-id="de698-154">Nom par lequel la procédure est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="de698-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="de698-155">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-155">Optional.</span></span> <span data-ttu-id="de698-156">Indicates that this procedure can handle one or more specific events.</span><span class="sxs-lookup"><span data-stu-id="de698-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="de698-157">See [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="de698-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="de698-158">Obligatoire si `Handles` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="de698-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="de698-159">List of events this procedure handles.</span><span class="sxs-lookup"><span data-stu-id="de698-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="de698-160">Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="de698-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="de698-161">Élément</span><span class="sxs-lookup"><span data-stu-id="de698-161">Part</span></span>|<span data-ttu-id="de698-162">Description</span><span class="sxs-lookup"><span data-stu-id="de698-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="de698-163">Requis.</span><span class="sxs-lookup"><span data-stu-id="de698-163">Required.</span></span> <span data-ttu-id="de698-164">Object variable declared with the data type of the class or structure that raises the event.</span><span class="sxs-lookup"><span data-stu-id="de698-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="de698-165">Requis.</span><span class="sxs-lookup"><span data-stu-id="de698-165">Required.</span></span> <span data-ttu-id="de698-166">Name of the event this procedure handles.</span><span class="sxs-lookup"><span data-stu-id="de698-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="de698-167">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="de698-167">Optional.</span></span> <span data-ttu-id="de698-168">Block of statements to be executed within this procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="de698-169">Terminates the definition of this procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="de698-170">Notes</span><span class="sxs-lookup"><span data-stu-id="de698-170">Remarks</span></span>

<span data-ttu-id="de698-171">All executable code must be inside a procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="de698-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="de698-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="de698-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="de698-174">Defining a Function</span><span class="sxs-lookup"><span data-stu-id="de698-174">Defining a Function</span></span>

<span data-ttu-id="de698-175">You can define a `Function` procedure only at the module level.</span><span class="sxs-lookup"><span data-stu-id="de698-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="de698-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span><span class="sxs-lookup"><span data-stu-id="de698-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="de698-177">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="de698-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="de698-178">`Function` procedures default to public access.</span><span class="sxs-lookup"><span data-stu-id="de698-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="de698-179">You can adjust their access levels with the access modifiers.</span><span class="sxs-lookup"><span data-stu-id="de698-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="de698-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span><span class="sxs-lookup"><span data-stu-id="de698-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="de698-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span><span class="sxs-lookup"><span data-stu-id="de698-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="de698-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span><span class="sxs-lookup"><span data-stu-id="de698-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="de698-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="de698-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="de698-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="de698-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="de698-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span><span class="sxs-lookup"><span data-stu-id="de698-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="de698-186">You can use lambda expressions to define function expressions inline.</span><span class="sxs-lookup"><span data-stu-id="de698-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="de698-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="de698-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="de698-188">Returning from a Function</span><span class="sxs-lookup"><span data-stu-id="de698-188">Returning from a Function</span></span>

<span data-ttu-id="de698-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="de698-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="de698-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="de698-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="de698-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="de698-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span><span class="sxs-lookup"><span data-stu-id="de698-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="de698-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="de698-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="de698-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="de698-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span><span class="sxs-lookup"><span data-stu-id="de698-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="de698-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span><span class="sxs-lookup"><span data-stu-id="de698-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="de698-197">Appel d’une fonction</span><span class="sxs-lookup"><span data-stu-id="de698-197">Calling a Function</span></span>

<span data-ttu-id="de698-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span><span class="sxs-lookup"><span data-stu-id="de698-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="de698-199">You can omit the parentheses only if you aren't supplying any arguments.</span><span class="sxs-lookup"><span data-stu-id="de698-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="de698-200">However, your code is more readable if you always include the parentheses.</span><span class="sxs-lookup"><span data-stu-id="de698-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="de698-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="de698-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="de698-202">You can also call a function by using the `Call` keyword.</span><span class="sxs-lookup"><span data-stu-id="de698-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="de698-203">In that case, the return value is ignored.</span><span class="sxs-lookup"><span data-stu-id="de698-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="de698-204">Use of the `Call` keyword isn't recommended in most cases.</span><span class="sxs-lookup"><span data-stu-id="de698-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="de698-205">For more information, see [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de698-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="de698-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span><span class="sxs-lookup"><span data-stu-id="de698-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="de698-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span><span class="sxs-lookup"><span data-stu-id="de698-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="de698-208">Async Functions</span><span class="sxs-lookup"><span data-stu-id="de698-208">Async Functions</span></span>

<span data-ttu-id="de698-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span><span class="sxs-lookup"><span data-stu-id="de698-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="de698-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span><span class="sxs-lookup"><span data-stu-id="de698-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="de698-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span><span class="sxs-lookup"><span data-stu-id="de698-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="de698-212">When the task is complete, execution can resume in the function.</span><span class="sxs-lookup"><span data-stu-id="de698-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="de698-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span><span class="sxs-lookup"><span data-stu-id="de698-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="de698-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="de698-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="de698-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span><span class="sxs-lookup"><span data-stu-id="de698-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="de698-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span><span class="sxs-lookup"><span data-stu-id="de698-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="de698-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span><span class="sxs-lookup"><span data-stu-id="de698-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="de698-218">This is primarily used for event handlers, where a value cannot be returned.</span><span class="sxs-lookup"><span data-stu-id="de698-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="de698-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="de698-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="de698-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="de698-221">Iterator Functions</span><span class="sxs-lookup"><span data-stu-id="de698-221">Iterator Functions</span></span>

<span data-ttu-id="de698-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span><span class="sxs-lookup"><span data-stu-id="de698-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="de698-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span><span class="sxs-lookup"><span data-stu-id="de698-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="de698-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span><span class="sxs-lookup"><span data-stu-id="de698-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="de698-225">L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="de698-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="de698-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span><span class="sxs-lookup"><span data-stu-id="de698-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="de698-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="de698-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="de698-228">Pour plus d’informations, consultez [Itérateurs](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="de698-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="de698-229">Exemple</span><span class="sxs-lookup"><span data-stu-id="de698-229">Example</span></span>

<span data-ttu-id="de698-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="de698-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span><span class="sxs-lookup"><span data-stu-id="de698-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="de698-232">Exemple</span><span class="sxs-lookup"><span data-stu-id="de698-232">Example</span></span>

<span data-ttu-id="de698-233">The following example invokes the function declared in the preceding example.</span><span class="sxs-lookup"><span data-stu-id="de698-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="de698-234">Exemple</span><span class="sxs-lookup"><span data-stu-id="de698-234">Example</span></span>

<span data-ttu-id="de698-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="de698-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="de698-236">`DelayAsync` a une instruction `Return` qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="de698-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="de698-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="de698-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="de698-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span><span class="sxs-lookup"><span data-stu-id="de698-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="de698-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="de698-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="de698-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="de698-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="de698-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="de698-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="de698-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="de698-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="de698-243">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de698-243">See also</span></span>

- [<span data-ttu-id="de698-244">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="de698-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="de698-245">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="de698-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="de698-246">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="de698-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="de698-247">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="de698-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="de698-248">Call (instruction)</span><span class="sxs-lookup"><span data-stu-id="de698-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="de698-249">Of</span><span class="sxs-lookup"><span data-stu-id="de698-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="de698-250">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="de698-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="de698-251">Guide pratique : utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="de698-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="de698-252">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="de698-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="de698-253">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="de698-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="de698-254">Expression de fonction</span><span class="sxs-lookup"><span data-stu-id="de698-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
