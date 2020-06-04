---
title: Structures de boucle
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403514"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="7b0f7-102">Structures de boucle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b0f7-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="7b0f7-103">Les structures de boucle Visual Basic vous permettent d’exécuter une ou plusieurs lignes de code de façon répétée.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="7b0f7-104">Vous pouvez répéter les instructions dans une structure de boucle jusqu’à ce qu’une condition soit, `True` `False` un nombre de fois spécifié ou une fois pour chaque élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="7b0f7-105">L’illustration suivante montre une structure de boucle qui exécute un ensemble d’instructions jusqu’à ce qu’une condition devienne vraie :</span><span class="sxs-lookup"><span data-stu-id="7b0f7-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Organigramme qui affiche un... Boucle until.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="7b0f7-107">Boucles While</span><span class="sxs-lookup"><span data-stu-id="7b0f7-107">While Loops</span></span>  
 <span data-ttu-id="7b0f7-108">La `While` construction... `End While` exécute un ensemble d’instructions tant que la condition spécifiée dans l' `While` instruction est `True` .</span><span class="sxs-lookup"><span data-stu-id="7b0f7-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="7b0f7-109">Pour plus d’informations, consultez [while... Instruction End While](../../../language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b0f7-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="7b0f7-110">Boucles do</span><span class="sxs-lookup"><span data-stu-id="7b0f7-110">Do Loops</span></span>  
 <span data-ttu-id="7b0f7-111">La `Do` construction... `Loop` vous permet de tester une condition au début ou à la fin d’une structure de boucle.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="7b0f7-112">Vous pouvez également spécifier si la boucle doit être répétée pendant que la condition est conservée `True` ou jusqu’à ce qu’elle devienne `True` .</span><span class="sxs-lookup"><span data-stu-id="7b0f7-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="7b0f7-113">Pour plus d’informations, consultez [do... Instruction de boucle](../../../language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b0f7-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="7b0f7-114">Boucles for</span><span class="sxs-lookup"><span data-stu-id="7b0f7-114">For Loops</span></span>  
 <span data-ttu-id="7b0f7-115">La `For` construction... `Next` exécute la boucle un nombre de fois défini.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="7b0f7-116">Elle utilise une variable de contrôle de boucle, également appelée *compteur*, pour effectuer le suivi des répétitions.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="7b0f7-117">Vous spécifiez les valeurs de début et de fin pour ce compteur et vous pouvez éventuellement spécifier la quantité d’augmentation d’une répétition à la suivante.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="7b0f7-118">Pour plus d’informations, consultez [pour... Instruction suivante](../../../language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b0f7-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="7b0f7-119">Boucles for each</span><span class="sxs-lookup"><span data-stu-id="7b0f7-119">For Each Loops</span></span>  
 <span data-ttu-id="7b0f7-120">La `For Each` construction... `Next` exécute un ensemble d’instructions une fois pour chaque élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="7b0f7-121">Vous spécifiez la variable de contrôle de boucle, mais vous n’avez pas besoin de déterminer les valeurs de début ou de fin pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="7b0f7-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="7b0f7-122">Pour plus d’informations, consultez [for each... Instruction suivante](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b0f7-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0f7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b0f7-123">See also</span></span>

- [<span data-ttu-id="7b0f7-124">Workflow de contrôle</span><span class="sxs-lookup"><span data-stu-id="7b0f7-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="7b0f7-125">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="7b0f7-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="7b0f7-126">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="7b0f7-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="7b0f7-127">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="7b0f7-127">Nested Control Structures</span></span>](nested-control-structures.md)
