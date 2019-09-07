---
title: If...Then...Else, instruction (Visual Basic)
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
ms.openlocfilehash: db81a1c41809b563d5f9d0777c3feb064c5e540b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400713"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="bc34d-102">If...Then...Else, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc34d-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="bc34d-103">Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.</span><span class="sxs-lookup"><span data-stu-id="bc34d-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc34d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc34d-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="bc34d-105">Liens rapides vers l’exemple de code</span><span class="sxs-lookup"><span data-stu-id="bc34d-105">Quick links to example code</span></span>

<span data-ttu-id="bc34d-106">Cet article contient plusieurs exemples qui illustrent les `If`utilisations de... `Then`... `Else` instruction :</span><span class="sxs-lookup"><span data-stu-id="bc34d-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="bc34d-107">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="bc34d-108">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="bc34d-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="bc34d-109">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="bc34d-110">Composants</span><span class="sxs-lookup"><span data-stu-id="bc34d-110">Parts</span></span>

`condition` \
<span data-ttu-id="bc34d-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="bc34d-111">Required.</span></span> <span data-ttu-id="bc34d-112">Formule.</span><span class="sxs-lookup"><span data-stu-id="bc34d-112">Expression.</span></span> <span data-ttu-id="bc34d-113">Doit correspondre à `True` ou `False`à, ou à un type de données qui est implicitement `Boolean`convertible en.</span><span class="sxs-lookup"><span data-stu-id="bc34d-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="bc34d-114">Si l’expression est une variable [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` qui prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression était `False`, et les `ElseIf` blocs sont évalués s’ils existent, ou le `Else` bloc est exécuté s’il existe.</span><span class="sxs-lookup"><span data-stu-id="bc34d-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="bc34d-115">Obligatoire dans la syntaxe sur une seule ligne ; facultatif dans la syntaxe multiligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="bc34d-116">facultatif.</span><span class="sxs-lookup"><span data-stu-id="bc34d-116">Optional.</span></span> <span data-ttu-id="bc34d-117">Une ou plusieurs instructions qui `If`suivent... qui sont exécutés `condition` si prend la `True`valeur. `Then`</span><span class="sxs-lookup"><span data-stu-id="bc34d-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="bc34d-118">Obligatoire si `ElseIf` est présent.</span><span class="sxs-lookup"><span data-stu-id="bc34d-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="bc34d-119">Formule.</span><span class="sxs-lookup"><span data-stu-id="bc34d-119">Expression.</span></span> <span data-ttu-id="bc34d-120">Doit correspondre à `True` ou `False`à, ou à un type de données qui est implicitement `Boolean`convertible en.</span><span class="sxs-lookup"><span data-stu-id="bc34d-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="bc34d-121">facultatif.</span><span class="sxs-lookup"><span data-stu-id="bc34d-121">Optional.</span></span> <span data-ttu-id="bc34d-122">Une ou plusieurs instructions qui `ElseIf`suivent... qui sont exécutés `elseifcondition` si prend la `True`valeur. `Then`</span><span class="sxs-lookup"><span data-stu-id="bc34d-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="bc34d-123">facultatif.</span><span class="sxs-lookup"><span data-stu-id="bc34d-123">Optional.</span></span> <span data-ttu-id="bc34d-124">Une ou plusieurs instructions qui sont exécutées si aucune `condition` expression `elseifcondition` ou précédente n’a `True`la valeur.</span><span class="sxs-lookup"><span data-stu-id="bc34d-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="bc34d-125">Met fin à la version multiligne `If`de... `Then`... `Else` bloquer.</span><span class="sxs-lookup"><span data-stu-id="bc34d-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc34d-126">Notes</span><span class="sxs-lookup"><span data-stu-id="bc34d-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="bc34d-127">Syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-127">Multiline syntax</span></span>

<span data-ttu-id="bc34d-128">Quand un `If`... `Then`... `Else` l'`condition` instruction est testée.</span><span class="sxs-lookup"><span data-stu-id="bc34d-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="bc34d-129">Si `condition` `Then` est `True`, les instructions suivantes sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="bc34d-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="bc34d-130">Si `condition` est `False`, chaque`ElseIf` instruction (le cas échéant) est évaluée dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="bc34d-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="bc34d-131">Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement le `ElseIf` associé sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="bc34d-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="bc34d-132">Si la `elseifcondition` valeur de `True`n’est pas, ou s’il `ElseIf` n’y a aucune instruction `Else` , les instructions suivantes sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="bc34d-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="bc34d-133">Après l’exécution des instructions qui `Then`suivent `ElseIf`, ou `Else`, l’exécution se poursuit avec l' `End If`instruction qui suit.</span><span class="sxs-lookup"><span data-stu-id="bc34d-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="bc34d-134">Les `ElseIf` clauses et `Else` sont toutes deux facultatives.</span><span class="sxs-lookup"><span data-stu-id="bc34d-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="bc34d-135">Vous pouvez avoir `ElseIf` autant de clauses que vous le souhaitez dans `If`une... `Then`... , mais aucune clause `ElseIf` ne peut apparaître après une `Else` clause. `Else`</span><span class="sxs-lookup"><span data-stu-id="bc34d-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="bc34d-136">`If`... `Then`... `Else` les instructions peuvent être imbriquées les unes dans les autres.</span><span class="sxs-lookup"><span data-stu-id="bc34d-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="bc34d-137">Dans la syntaxe multiligne, l' `If` instruction doit être la seule instruction sur la première ligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="bc34d-138">Les `ElseIf`instructions `Else`, et`End If` ne peuvent être précédées que d’une étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="bc34d-139">`If`... `Then`... le bloc doit se terminer `End If` par une instruction. `Else`</span><span class="sxs-lookup"><span data-stu-id="bc34d-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="bc34d-140">L' [option Select... L’instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="bc34d-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="bc34d-141">Syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-141">Single-Line syntax</span></span>

<span data-ttu-id="bc34d-142">Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie.</span><span class="sxs-lookup"><span data-stu-id="bc34d-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="bc34d-143">Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="bc34d-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="bc34d-144">Ce qui suit `Then` le mot clé est examiné pour déterminer si une instruction est une seule `If`ligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="bc34d-145">Si tout autre chose qu’un commentaire apparaît `Then` après sur la même ligne, l’instruction est traitée comme une instruction sur `If` une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="bc34d-146">Si `Then` est absent, il doit s’agir du début d’une ligne `If`multiple... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="bc34d-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="bc34d-147">Dans la syntaxe d’une seule ligne, vous pouvez avoir plusieurs instructions exécutées en tant que `If`résultat d’un... `Then` décision.</span><span class="sxs-lookup"><span data-stu-id="bc34d-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="bc34d-148">Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.</span><span class="sxs-lookup"><span data-stu-id="bc34d-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="bc34d-149">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="bc34d-150">L’exemple suivant illustre l’utilisation de la syntaxe multiligne de `If`... `Then`... `Else` instruction.</span><span class="sxs-lookup"><span data-stu-id="bc34d-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="bc34d-151">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="bc34d-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="bc34d-152">L’exemple suivant contient `If`des... `Then`... `Else` instructions.</span><span class="sxs-lookup"><span data-stu-id="bc34d-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="bc34d-153">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="bc34d-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="bc34d-154">L’exemple suivant illustre l’utilisation de la syntaxe sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="bc34d-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="bc34d-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc34d-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="bc34d-156">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="bc34d-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="bc34d-157">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="bc34d-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="bc34d-158">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="bc34d-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="bc34d-159">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="bc34d-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="bc34d-160">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc34d-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="bc34d-161">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="bc34d-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
