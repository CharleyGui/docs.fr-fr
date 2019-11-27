---
title: If...Then...Else, instruction
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351161"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="e16af-102">If...Then...Else, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e16af-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="e16af-103">Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.</span><span class="sxs-lookup"><span data-stu-id="e16af-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="e16af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e16af-104">Syntax</span></span>

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a><span data-ttu-id="e16af-105">Liens rapides vers l’exemple de code</span><span class="sxs-lookup"><span data-stu-id="e16af-105">Quick links to example code</span></span>

<span data-ttu-id="e16af-106">Cet article contient plusieurs exemples qui illustrent l’utilisation de l’instruction `If`...`Then`...`Else` :</span><span class="sxs-lookup"><span data-stu-id="e16af-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="e16af-107">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="e16af-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="e16af-108">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="e16af-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="e16af-109">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="e16af-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="e16af-110">Composants</span><span class="sxs-lookup"><span data-stu-id="e16af-110">Parts</span></span>

`condition` \
<span data-ttu-id="e16af-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="e16af-111">Required.</span></span> <span data-ttu-id="e16af-112">Formule.</span><span class="sxs-lookup"><span data-stu-id="e16af-112">Expression.</span></span> <span data-ttu-id="e16af-113">Doit correspondre à `True` ou `False`, ou à un type de données implicitement convertible en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e16af-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="e16af-114">Si l’expression est une variable `Boolean` [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) qui prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression était `False`, et les blocs `ElseIf` sont évalués s’ils existent, ou le bloc `Else` est exécuté s’il existe.</span><span class="sxs-lookup"><span data-stu-id="e16af-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="e16af-115">Obligatoire dans la syntaxe sur une seule ligne ; facultatif dans la syntaxe multiligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="e16af-116">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e16af-116">Optional.</span></span> <span data-ttu-id="e16af-117">Une ou plusieurs instructions qui suivent `If`...`Then` qui sont exécutées si `condition` prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="e16af-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="e16af-118">Obligatoire si `ElseIf` est présent.</span><span class="sxs-lookup"><span data-stu-id="e16af-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="e16af-119">Formule.</span><span class="sxs-lookup"><span data-stu-id="e16af-119">Expression.</span></span> <span data-ttu-id="e16af-120">Doit correspondre à `True` ou `False`, ou à un type de données implicitement convertible en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e16af-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="e16af-121">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e16af-121">Optional.</span></span> <span data-ttu-id="e16af-122">Une ou plusieurs instructions qui suivent `ElseIf`...`Then` qui sont exécutées si `elseifcondition` prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="e16af-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="e16af-123">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e16af-123">Optional.</span></span> <span data-ttu-id="e16af-124">Une ou plusieurs instructions qui sont exécutées si aucune expression `condition` ou `elseifcondition` précédente ne prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="e16af-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="e16af-125">Met fin à la version multiligne du bloc `If`...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="e16af-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="e16af-126">Notes</span><span class="sxs-lookup"><span data-stu-id="e16af-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="e16af-127">Syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="e16af-127">Multiline syntax</span></span>

<span data-ttu-id="e16af-128">Lorsqu’une `If`...`Then`instruction`Else` est rencontrée, `condition` est testé.</span><span class="sxs-lookup"><span data-stu-id="e16af-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="e16af-129">Si `condition` est `True`, les instructions qui suivent `Then` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="e16af-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="e16af-130">Si `condition` est `False`, chaque instruction `ElseIf` (le cas échéant) est évaluée dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="e16af-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="e16af-131">Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement les `ElseIf` associées sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="e16af-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="e16af-132">Si aucun `elseifcondition` n’a la valeur `True`, ou s’il n’existe aucune instruction `ElseIf`, les instructions qui suivent `Else` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="e16af-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="e16af-133">Après l’exécution des instructions qui suivent `Then`, `ElseIf`ou `Else`, l’exécution se poursuit avec l’instruction qui suit `End If`.</span><span class="sxs-lookup"><span data-stu-id="e16af-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="e16af-134">Les clauses `ElseIf` et `Else` sont toutes deux facultatives.</span><span class="sxs-lookup"><span data-stu-id="e16af-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="e16af-135">Vous pouvez avoir autant de clauses de `ElseIf` que vous le souhaitez dans une instruction `If`...`Then`...`Else`, mais aucune clause `ElseIf` ne peut apparaître après une clause `Else`.</span><span class="sxs-lookup"><span data-stu-id="e16af-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="e16af-136">les instructions `If`...`Then`...`Else` peuvent être imbriquées les unes dans les autres.</span><span class="sxs-lookup"><span data-stu-id="e16af-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="e16af-137">Dans la syntaxe multiligne, l’instruction `If` doit être la seule instruction sur la première ligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="e16af-138">Les instructions `ElseIf`, `Else`et `End If` peuvent être précédées uniquement d’une étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="e16af-139">Le bloc `If`...`Then`...`Else` doit se terminer par une instruction `End If`.</span><span class="sxs-lookup"><span data-stu-id="e16af-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="e16af-140">L' [option Select... L’instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="e16af-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="e16af-141">Syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="e16af-141">Single-Line syntax</span></span>

<span data-ttu-id="e16af-142">Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie.</span><span class="sxs-lookup"><span data-stu-id="e16af-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="e16af-143">Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="e16af-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="e16af-144">Ce qui suit le mot clé `Then` est examiné pour déterminer si une instruction est un `If`à une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="e16af-145">Si tout autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une instruction de `If` à une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="e16af-146">Si `Then` est absent, il doit s’agir du début d’un `If`à plusieurs lignes...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="e16af-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="e16af-147">Dans la syntaxe d’une seule ligne, vous pouvez exécuter plusieurs instructions à la suite d’une `If`...`Then` décision.</span><span class="sxs-lookup"><span data-stu-id="e16af-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="e16af-148">Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.</span><span class="sxs-lookup"><span data-stu-id="e16af-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="e16af-149">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="e16af-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="e16af-150">L’exemple suivant illustre l’utilisation de la syntaxe multiligne de l’instruction `If`...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="e16af-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="e16af-151">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="e16af-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="e16af-152">L’exemple suivant contient des instructions `If`...`Then`...`Else` imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e16af-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="e16af-153">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="e16af-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="e16af-154">L’exemple suivant illustre l’utilisation de la syntaxe sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e16af-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="e16af-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e16af-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="e16af-156">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="e16af-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="e16af-157">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="e16af-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="e16af-158">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="e16af-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="e16af-159">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="e16af-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="e16af-160">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e16af-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="e16af-161">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e16af-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
