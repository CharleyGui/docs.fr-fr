---
title: Exit, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956934"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="c408b-102">Exit, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c408b-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="c408b-103">Quitte une procédure ou un bloc et transfère immédiatement le contrôle à l’instruction qui suit l’appel de procédure ou la définition de bloc.</span><span class="sxs-lookup"><span data-stu-id="c408b-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="c408b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c408b-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="c408b-105">Instructions</span><span class="sxs-lookup"><span data-stu-id="c408b-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="c408b-106">Quitte immédiatement la boucle `Do` dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="c408b-107">L’exécution se poursuit avec l’instruction qui suit l’instruction `Loop`.</span><span class="sxs-lookup"><span data-stu-id="c408b-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="c408b-108">`Exit Do` ne peut être utilisé qu’à l’intérieur d’une boucle `Do`.</span><span class="sxs-lookup"><span data-stu-id="c408b-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="c408b-109">En cas d’utilisation dans des boucles `Do` imbriquées, `Exit Do` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.</span><span class="sxs-lookup"><span data-stu-id="c408b-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="c408b-110">Quitte immédiatement la boucle `For` dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="c408b-111">L’exécution se poursuit avec l’instruction qui suit l’instruction `Next`.</span><span class="sxs-lookup"><span data-stu-id="c408b-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="c408b-112">`Exit For` ne peut être utilisé qu’à l’intérieur d’une boucle `For`... `Next` ou `For Each`... `Next`.</span><span class="sxs-lookup"><span data-stu-id="c408b-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="c408b-113">En cas d’utilisation dans des boucles `For` imbriquées, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.</span><span class="sxs-lookup"><span data-stu-id="c408b-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="c408b-114">Quitte immédiatement la procédure `Function` dans laquelle il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="c408b-115">L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure `Function`.</span><span class="sxs-lookup"><span data-stu-id="c408b-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="c408b-116">`Exit Function` ne peut être utilisé qu’à l’intérieur d’une procédure `Function`.</span><span class="sxs-lookup"><span data-stu-id="c408b-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="c408b-117">Pour spécifier une valeur de retour, vous pouvez affecter la valeur au nom de la fonction sur une ligne avant l’instruction `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="c408b-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="c408b-118">Pour affecter la valeur de retour et quitter la fonction dans une instruction, vous pouvez utiliser à la place l' [instruction return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c408b-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="c408b-119">Quitte immédiatement la procédure `Property` dans laquelle il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="c408b-120">L’exécution se poursuit avec l’instruction qui a appelé la procédure `Property`, c’est-à-dire, avec l’instruction qui demande ou définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c408b-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="c408b-121">`Exit Property` ne peut être utilisé qu’à l’intérieur d’une procédure `Get` ou `Set` d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="c408b-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="c408b-122">Pour spécifier une valeur de retour dans une procédure `Get`, vous pouvez affecter la valeur au nom de la fonction sur une ligne avant l’instruction `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="c408b-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="c408b-123">Pour affecter la valeur de retour et quitter la procédure `Get` dans une instruction, vous pouvez utiliser à la place l’instruction `Return`.</span><span class="sxs-lookup"><span data-stu-id="c408b-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="c408b-124">Dans une procédure `Set`, l’instruction `Exit Property` équivaut à l’instruction `Return`.</span><span class="sxs-lookup"><span data-stu-id="c408b-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="c408b-125">Quitte immédiatement le bloc `Select Case` dans lequel il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="c408b-126">L’exécution se poursuit avec l’instruction qui suit l’instruction `End Select`.</span><span class="sxs-lookup"><span data-stu-id="c408b-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="c408b-127">`Exit Select` ne peut être utilisé qu’à l’intérieur d’une instruction `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="c408b-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="c408b-128">Quitte immédiatement la procédure `Sub` dans laquelle il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="c408b-129">L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure `Sub`.</span><span class="sxs-lookup"><span data-stu-id="c408b-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="c408b-130">`Exit Sub` ne peut être utilisé qu’à l’intérieur d’une procédure `Sub`.</span><span class="sxs-lookup"><span data-stu-id="c408b-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="c408b-131">Dans une procédure `Sub`, l’instruction `Exit Sub` équivaut à l’instruction `Return`.</span><span class="sxs-lookup"><span data-stu-id="c408b-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="c408b-132">Quitte immédiatement le bloc `Try` ou `Catch` dans lequel il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="c408b-133">L’exécution se poursuit avec le bloc `Finally` s’il en existe un, ou avec l’instruction qui suit l’instruction `End Try` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="c408b-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="c408b-134">`Exit Try` ne peut être utilisé qu’à l’intérieur d’un bloc `Try` ou `Catch`, et non à l’intérieur d’un bloc `Finally`.</span><span class="sxs-lookup"><span data-stu-id="c408b-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="c408b-135">Quitte immédiatement la boucle `While` dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="c408b-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="c408b-136">L’exécution se poursuit avec l’instruction qui suit l’instruction `End While`.</span><span class="sxs-lookup"><span data-stu-id="c408b-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="c408b-137">`Exit While` ne peut être utilisé qu’à l’intérieur d’une boucle `While`.</span><span class="sxs-lookup"><span data-stu-id="c408b-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="c408b-138">Lorsqu’il est utilisé dans des boucles `While` imbriquées, `Exit While` transfère le contrôle à la boucle qui est un niveau imbriqué au-dessus de la boucle où `Exit While` se produit.</span><span class="sxs-lookup"><span data-stu-id="c408b-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="c408b-139">Notes</span><span class="sxs-lookup"><span data-stu-id="c408b-139">Remarks</span></span>

<span data-ttu-id="c408b-140">Ne confondez pas les instructions `Exit` avec des instructions `End`.</span><span class="sxs-lookup"><span data-stu-id="c408b-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="c408b-141">`Exit` ne définit pas la fin d’une instruction.</span><span class="sxs-lookup"><span data-stu-id="c408b-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="c408b-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="c408b-142">Example</span></span>

<span data-ttu-id="c408b-143">Dans l’exemple suivant, la condition de boucle arrête la boucle lorsque la variable `index` est supérieure à 100.</span><span class="sxs-lookup"><span data-stu-id="c408b-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="c408b-144">Toutefois, l’instruction `If` dans la boucle entraîne l’arrêt de la boucle par l’instruction `Exit Do` lorsque la variable d’index est supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="c408b-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="c408b-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="c408b-145">Example</span></span>

<span data-ttu-id="c408b-146">L’exemple suivant affecte la valeur de retour au nom de la fonction `myFunction`, puis utilise `Exit Function` pour retourner à partir de la fonction :</span><span class="sxs-lookup"><span data-stu-id="c408b-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="c408b-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="c408b-147">Example</span></span>

<span data-ttu-id="c408b-148">L’exemple suivant utilise l' [instruction return](return-statement.md) pour assigner la valeur de retour et quitter la fonction :</span><span class="sxs-lookup"><span data-stu-id="c408b-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="c408b-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c408b-149">See also</span></span>

- [<span data-ttu-id="c408b-150">Continue (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="c408b-151">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="c408b-152">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="c408b-153">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="c408b-154">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="c408b-155">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="c408b-156">Return (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="c408b-157">Stop (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="c408b-158">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c408b-159">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="c408b-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
