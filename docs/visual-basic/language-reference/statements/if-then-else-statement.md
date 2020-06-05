---
title: If...Then...Else (instruction)
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404587"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="f0f22-102">If...Then...Else, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f22-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="f0f22-103">Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.</span><span class="sxs-lookup"><span data-stu-id="f0f22-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0f22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0f22-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="f0f22-105">Liens rapides vers l’exemple de code</span><span class="sxs-lookup"><span data-stu-id="f0f22-105">Quick links to example code</span></span>

<span data-ttu-id="f0f22-106">Cet article contient plusieurs exemples qui illustrent les utilisations de `If` ... `Then` ...`Else` gestion</span><span class="sxs-lookup"><span data-stu-id="f0f22-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="f0f22-107">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="f0f22-108">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="f0f22-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="f0f22-109">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="f0f22-110">Éléments</span><span class="sxs-lookup"><span data-stu-id="f0f22-110">Parts</span></span>

`condition` \
<span data-ttu-id="f0f22-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f0f22-111">Required.</span></span> <span data-ttu-id="f0f22-112">Expression.</span><span class="sxs-lookup"><span data-stu-id="f0f22-112">Expression.</span></span> <span data-ttu-id="f0f22-113">Doit correspondre à `True` ou `False` à, ou à un type de données qui est implicitement convertible en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="f0f22-114">Si l’expression est une [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable Nullable qui prend la valeur [Nothing](../nothing.md), la condition est traitée comme si l’expression était `False` , et les `ElseIf` blocs sont évalués s’ils existent, ou le `Else` bloc est exécuté s’il existe.</span><span class="sxs-lookup"><span data-stu-id="f0f22-114">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="f0f22-115">Obligatoire dans la syntaxe sur une seule ligne ; facultatif dans la syntaxe multiligne.</span><span class="sxs-lookup"><span data-stu-id="f0f22-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="f0f22-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0f22-116">Optional.</span></span> <span data-ttu-id="f0f22-117">Une ou plusieurs instructions `If` qui suivent... `Then` qui sont exécutées si `condition` prend la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="f0f22-118">Obligatoire si `ElseIf` est présent.</span><span class="sxs-lookup"><span data-stu-id="f0f22-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="f0f22-119">Expression.</span><span class="sxs-lookup"><span data-stu-id="f0f22-119">Expression.</span></span> <span data-ttu-id="f0f22-120">Doit correspondre à `True` ou `False` à, ou à un type de données qui est implicitement convertible en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="f0f22-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0f22-121">Optional.</span></span> <span data-ttu-id="f0f22-122">Une ou plusieurs instructions `ElseIf` qui suivent... `Then` qui sont exécutées si `elseifcondition` prend la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="f0f22-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0f22-123">Optional.</span></span> <span data-ttu-id="f0f22-124">Une ou plusieurs instructions qui sont exécutées si aucune expression ou précédente n’a la `condition` `elseifcondition` valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="f0f22-125">Met fin à la version multiligne de `If` ... `Then` ...`Else` plage.</span><span class="sxs-lookup"><span data-stu-id="f0f22-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0f22-126">Notes</span><span class="sxs-lookup"><span data-stu-id="f0f22-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="f0f22-127">Syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-127">Multiline syntax</span></span>

<span data-ttu-id="f0f22-128">Quand un `If` ... `Then` ...`Else` l’instruction est `condition` testée.</span><span class="sxs-lookup"><span data-stu-id="f0f22-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="f0f22-129">Si `condition` est `True` , les instructions suivantes `Then` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="f0f22-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="f0f22-130">Si `condition` est `False` , chaque `ElseIf` instruction (le cas échéant) est évaluée dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="f0f22-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="f0f22-131">Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement le associé `ElseIf` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="f0f22-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="f0f22-132">Si `elseifcondition` la valeur de n' `True` est pas, ou s’il n’y a aucune `ElseIf` instruction, les instructions suivantes `Else` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="f0f22-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="f0f22-133">Après l’exécution des instructions qui suivent `Then` , `ElseIf` ou `Else` , l’exécution se poursuit avec l’instruction qui suit `End If` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="f0f22-134">Les `ElseIf` `Else` clauses et sont toutes deux facultatives.</span><span class="sxs-lookup"><span data-stu-id="f0f22-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="f0f22-135">Vous pouvez avoir autant `ElseIf` de clauses que vous le souhaitez dans une `If` ... `Then` ...`Else` , mais aucune `ElseIf` clause ne peut apparaître après une `Else` clause.</span><span class="sxs-lookup"><span data-stu-id="f0f22-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="f0f22-136">`If`...`Then` ...`Else` les instructions peuvent être imbriquées les unes dans les autres.</span><span class="sxs-lookup"><span data-stu-id="f0f22-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="f0f22-137">Dans la syntaxe multiligne, l' `If` instruction doit être la seule instruction sur la première ligne.</span><span class="sxs-lookup"><span data-stu-id="f0f22-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="f0f22-138">Les `ElseIf` `Else` instructions, et `End If` ne peuvent être précédées que d’une étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="f0f22-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="f0f22-139">`If`... `Then` ...`Else` le bloc doit se terminer par une `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="f0f22-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="f0f22-140">L' [option Select... L’instruction case](select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="f0f22-140">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="f0f22-141">Syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-141">Single-Line syntax</span></span>

<span data-ttu-id="f0f22-142">Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie.</span><span class="sxs-lookup"><span data-stu-id="f0f22-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="f0f22-143">Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="f0f22-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="f0f22-144">Ce qui suit le `Then` mot clé est examiné pour déterminer si une instruction est une seule ligne `If` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="f0f22-145">Si tout autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une instruction sur une seule ligne `If` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="f0f22-146">Si `Then` est absent, il doit s’agir du début d’une ligne multiple `If` ... `Then` ...`Else`.</span><span class="sxs-lookup"><span data-stu-id="f0f22-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="f0f22-147">Dans la syntaxe d’une seule ligne, vous pouvez avoir plusieurs instructions exécutées en tant que résultat d’une `If` décision... `Then` .</span><span class="sxs-lookup"><span data-stu-id="f0f22-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="f0f22-148">Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.</span><span class="sxs-lookup"><span data-stu-id="f0f22-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="f0f22-149">Exemple de syntaxe multiligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="f0f22-150">L’exemple suivant illustre l’utilisation de la syntaxe multiligne de `If` ... `Then` ...`Else` gestion.</span><span class="sxs-lookup"><span data-stu-id="f0f22-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="f0f22-151">Exemple de syntaxe imbriquée</span><span class="sxs-lookup"><span data-stu-id="f0f22-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="f0f22-152">L’exemple suivant contient des `If` ... `Then` ...`Else` publication.</span><span class="sxs-lookup"><span data-stu-id="f0f22-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="f0f22-153">Exemple de syntaxe sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="f0f22-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="f0f22-154">L’exemple suivant illustre l’utilisation de la syntaxe sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="f0f22-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="f0f22-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0f22-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="f0f22-156">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="f0f22-156">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="f0f22-157">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0f22-157">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="f0f22-158">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="f0f22-158">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="f0f22-159">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="f0f22-159">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="f0f22-160">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0f22-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="f0f22-161">If, opérateur</span><span class="sxs-lookup"><span data-stu-id="f0f22-161">If Operator</span></span>](../operators/if-operator.md)
