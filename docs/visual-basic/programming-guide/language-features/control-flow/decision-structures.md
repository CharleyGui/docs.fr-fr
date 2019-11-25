---
title: Structures de décision
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353974"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="e3093-102">Structures de décision (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3093-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="e3093-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span><span class="sxs-lookup"><span data-stu-id="e3093-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="e3093-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span><span class="sxs-lookup"><span data-stu-id="e3093-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="e3093-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span><span class="sxs-lookup"><span data-stu-id="e3093-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![A flow chart of an If...Then...Else construction.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="e3093-107">If...Then...Else Construction</span><span class="sxs-lookup"><span data-stu-id="e3093-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="e3093-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span><span class="sxs-lookup"><span data-stu-id="e3093-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="e3093-109">You can test conditions and take actions in the following ways:</span><span class="sxs-lookup"><span data-stu-id="e3093-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="e3093-110">Run one or more statements if a condition is `True`</span><span class="sxs-lookup"><span data-stu-id="e3093-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="e3093-111">Run one or more statements if a condition is `False`</span><span class="sxs-lookup"><span data-stu-id="e3093-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="e3093-112">Run some statements if a condition is `True` and others if it is `False`</span><span class="sxs-lookup"><span data-stu-id="e3093-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="e3093-113">Test an additional condition if a prior condition is `False`</span><span class="sxs-lookup"><span data-stu-id="e3093-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="e3093-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3093-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="e3093-115">You can use a single-line version if you have just one test and one statement to run.</span><span class="sxs-lookup"><span data-stu-id="e3093-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="e3093-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span><span class="sxs-lookup"><span data-stu-id="e3093-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="e3093-117">Select...Case Construction</span><span class="sxs-lookup"><span data-stu-id="e3093-117">Select...Case Construction</span></span>  
 <span data-ttu-id="e3093-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span><span class="sxs-lookup"><span data-stu-id="e3093-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="e3093-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3093-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="e3093-120">Try...Catch...Finally Construction</span><span class="sxs-lookup"><span data-stu-id="e3093-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="e3093-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span><span class="sxs-lookup"><span data-stu-id="e3093-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="e3093-122">You can take different actions for different exceptions.</span><span class="sxs-lookup"><span data-stu-id="e3093-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="e3093-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span><span class="sxs-lookup"><span data-stu-id="e3093-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="e3093-124">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3093-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3093-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span><span class="sxs-lookup"><span data-stu-id="e3093-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="e3093-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span><span class="sxs-lookup"><span data-stu-id="e3093-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="e3093-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span><span class="sxs-lookup"><span data-stu-id="e3093-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3093-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3093-128">See also</span></span>

- [<span data-ttu-id="e3093-129">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="e3093-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="e3093-130">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="e3093-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="e3093-131">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="e3093-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="e3093-132">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="e3093-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="e3093-133">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e3093-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
