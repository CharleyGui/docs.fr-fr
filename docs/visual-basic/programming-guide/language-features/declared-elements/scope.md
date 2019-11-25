---
title: Étendue
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 37fcfa897accb23e9c8c56407ce4ebd956b39c4d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345288"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="d7d11-102">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7d11-102">Scope in Visual Basic</span></span>

<span data-ttu-id="d7d11-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="d7d11-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="d7d11-104">An element can have scope at one of the following levels:</span><span class="sxs-lookup"><span data-stu-id="d7d11-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="d7d11-105">Level</span><span class="sxs-lookup"><span data-stu-id="d7d11-105">Level</span></span>|<span data-ttu-id="d7d11-106">Description</span><span class="sxs-lookup"><span data-stu-id="d7d11-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="d7d11-107">Portée de bloc</span><span class="sxs-lookup"><span data-stu-id="d7d11-107">Block scope</span></span>|<span data-ttu-id="d7d11-108">Available only within the code block in which it is declared</span><span class="sxs-lookup"><span data-stu-id="d7d11-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="d7d11-109">Procedure scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-109">Procedure scope</span></span>|<span data-ttu-id="d7d11-110">Available to all code within the procedure in which it is declared</span><span class="sxs-lookup"><span data-stu-id="d7d11-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="d7d11-111">Module scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-111">Module scope</span></span>|<span data-ttu-id="d7d11-112">Available to all code within the module, class, or structure in which it is declared</span><span class="sxs-lookup"><span data-stu-id="d7d11-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="d7d11-113">Namespace scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-113">Namespace scope</span></span>|<span data-ttu-id="d7d11-114">Available to all code in the namespace in which it is declared</span><span class="sxs-lookup"><span data-stu-id="d7d11-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="d7d11-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span><span class="sxs-lookup"><span data-stu-id="d7d11-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="d7d11-116">For more information, see "Levels of Scope" on this page.</span><span class="sxs-lookup"><span data-stu-id="d7d11-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="d7d11-117">Specifying Scope and Defining Variables</span><span class="sxs-lookup"><span data-stu-id="d7d11-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="d7d11-118">You specify the scope of an element when you declare it.</span><span class="sxs-lookup"><span data-stu-id="d7d11-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="d7d11-119">The scope can depend on the following factors:</span><span class="sxs-lookup"><span data-stu-id="d7d11-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="d7d11-120">The region (block, procedure, module, class, or structure) in which you declare the element</span><span class="sxs-lookup"><span data-stu-id="d7d11-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="d7d11-121">The namespace containing the element's declaration</span><span class="sxs-lookup"><span data-stu-id="d7d11-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="d7d11-122">The access level you declare for the element</span><span class="sxs-lookup"><span data-stu-id="d7d11-122">The access level you declare for the element</span></span>

<span data-ttu-id="d7d11-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span><span class="sxs-lookup"><span data-stu-id="d7d11-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="d7d11-124">Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="d7d11-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="d7d11-125">Levels of Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-125">Levels of Scope</span></span>

<span data-ttu-id="d7d11-126">A programming element is available throughout the region in which you declare it.</span><span class="sxs-lookup"><span data-stu-id="d7d11-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="d7d11-127">All code in the same region can refer to the element without qualifying its name.</span><span class="sxs-lookup"><span data-stu-id="d7d11-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="d7d11-128">Block Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-128">Block Scope</span></span>

<span data-ttu-id="d7d11-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span><span class="sxs-lookup"><span data-stu-id="d7d11-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="d7d11-130">`Do` et `Loop`</span><span class="sxs-lookup"><span data-stu-id="d7d11-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="d7d11-131">`For` [`Each`] and `Next`</span><span class="sxs-lookup"><span data-stu-id="d7d11-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="d7d11-132">`If` et `End If`</span><span class="sxs-lookup"><span data-stu-id="d7d11-132">`If` and `End If`</span></span>

- <span data-ttu-id="d7d11-133">`Select` et `End Select`</span><span class="sxs-lookup"><span data-stu-id="d7d11-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="d7d11-134">`SyncLock` et `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="d7d11-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="d7d11-135">`Try` et `End Try`</span><span class="sxs-lookup"><span data-stu-id="d7d11-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="d7d11-136">`While` et `End While`</span><span class="sxs-lookup"><span data-stu-id="d7d11-136">`While` and `End While`</span></span>

- <span data-ttu-id="d7d11-137">`With` et `End With`</span><span class="sxs-lookup"><span data-stu-id="d7d11-137">`With` and `End With`</span></span>

<span data-ttu-id="d7d11-138">If you declare a variable within a block, you can use it only within that block.</span><span class="sxs-lookup"><span data-stu-id="d7d11-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="d7d11-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span><span class="sxs-lookup"><span data-stu-id="d7d11-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="d7d11-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span><span class="sxs-lookup"><span data-stu-id="d7d11-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="d7d11-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span><span class="sxs-lookup"><span data-stu-id="d7d11-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="d7d11-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span><span class="sxs-lookup"><span data-stu-id="d7d11-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="d7d11-143">Procedure Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-143">Procedure Scope</span></span>

<span data-ttu-id="d7d11-144">An element declared within a procedure is not available outside that procedure.</span><span class="sxs-lookup"><span data-stu-id="d7d11-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="d7d11-145">Only the procedure that contains the declaration can use it.</span><span class="sxs-lookup"><span data-stu-id="d7d11-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="d7d11-146">Variables at this level are also known as *local variables*.</span><span class="sxs-lookup"><span data-stu-id="d7d11-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="d7d11-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="d7d11-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="d7d11-148">Procedure and block scope are closely related.</span><span class="sxs-lookup"><span data-stu-id="d7d11-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="d7d11-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span><span class="sxs-lookup"><span data-stu-id="d7d11-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="d7d11-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span><span class="sxs-lookup"><span data-stu-id="d7d11-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="d7d11-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span><span class="sxs-lookup"><span data-stu-id="d7d11-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="d7d11-152">Module Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-152">Module Scope</span></span>

<span data-ttu-id="d7d11-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span><span class="sxs-lookup"><span data-stu-id="d7d11-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="d7d11-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="d7d11-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="d7d11-155">When you make a declaration at the module level, the access level you choose determines the scope.</span><span class="sxs-lookup"><span data-stu-id="d7d11-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="d7d11-156">The namespace that contains the module, class, or structure also affects the scope.</span><span class="sxs-lookup"><span data-stu-id="d7d11-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="d7d11-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span><span class="sxs-lookup"><span data-stu-id="d7d11-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="d7d11-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span><span class="sxs-lookup"><span data-stu-id="d7d11-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="d7d11-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="d7d11-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="d7d11-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="d7d11-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="d7d11-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span><span class="sxs-lookup"><span data-stu-id="d7d11-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="d7d11-162">Namespace Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-162">Namespace Scope</span></span>

<span data-ttu-id="d7d11-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span><span class="sxs-lookup"><span data-stu-id="d7d11-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="d7d11-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span><span class="sxs-lookup"><span data-stu-id="d7d11-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="d7d11-165">Namespace scope includes nested namespaces.</span><span class="sxs-lookup"><span data-stu-id="d7d11-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="d7d11-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span><span class="sxs-lookup"><span data-stu-id="d7d11-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="d7d11-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span><span class="sxs-lookup"><span data-stu-id="d7d11-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="d7d11-168">In this case, namespace scope can be thought of as project scope.</span><span class="sxs-lookup"><span data-stu-id="d7d11-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="d7d11-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span><span class="sxs-lookup"><span data-stu-id="d7d11-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="d7d11-170">Choice of Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-170">Choice of Scope</span></span>

<span data-ttu-id="d7d11-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span><span class="sxs-lookup"><span data-stu-id="d7d11-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="d7d11-172">Advantages of Local Variables</span><span class="sxs-lookup"><span data-stu-id="d7d11-172">Advantages of Local Variables</span></span>

<span data-ttu-id="d7d11-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span><span class="sxs-lookup"><span data-stu-id="d7d11-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="d7d11-174">**Name Conflict Avoidance.**</span><span class="sxs-lookup"><span data-stu-id="d7d11-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="d7d11-175">Local variable names are not susceptible to conflict.</span><span class="sxs-lookup"><span data-stu-id="d7d11-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="d7d11-176">For example, you can create several different procedures containing a variable called `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="d7d11-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="d7d11-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="d7d11-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="d7d11-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span><span class="sxs-lookup"><span data-stu-id="d7d11-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="d7d11-179">**Memory Consumption.**</span><span class="sxs-lookup"><span data-stu-id="d7d11-179">**Memory Consumption.**</span></span> <span data-ttu-id="d7d11-180">Local variables consume memory only while their procedure is running.</span><span class="sxs-lookup"><span data-stu-id="d7d11-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="d7d11-181">Their memory is released when the procedure returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="d7d11-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="d7d11-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span><span class="sxs-lookup"><span data-stu-id="d7d11-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="d7d11-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span><span class="sxs-lookup"><span data-stu-id="d7d11-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="d7d11-184">Minimizing Scope</span><span class="sxs-lookup"><span data-stu-id="d7d11-184">Minimizing Scope</span></span>

<span data-ttu-id="d7d11-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span><span class="sxs-lookup"><span data-stu-id="d7d11-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="d7d11-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span><span class="sxs-lookup"><span data-stu-id="d7d11-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="d7d11-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span><span class="sxs-lookup"><span data-stu-id="d7d11-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7d11-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7d11-188">See also</span></span>

- [<span data-ttu-id="d7d11-189">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="d7d11-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="d7d11-190">Guide pratique : contrôler la portée d'une variable</span><span class="sxs-lookup"><span data-stu-id="d7d11-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="d7d11-191">Lifetime in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7d11-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="d7d11-192">Access levels in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7d11-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="d7d11-193">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="d7d11-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="d7d11-194">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="d7d11-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
