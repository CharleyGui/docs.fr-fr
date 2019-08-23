---
title: While...End While, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965813"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="e1e32-102">While...End While, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1e32-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="e1e32-103">Exécute une série d’instructions tant qu’une condition donnée a `True`la valeur.</span><span class="sxs-lookup"><span data-stu-id="e1e32-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1e32-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="e1e32-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e1e32-105">Parts</span></span>  
  
|<span data-ttu-id="e1e32-106">Terme</span><span class="sxs-lookup"><span data-stu-id="e1e32-106">Term</span></span>|<span data-ttu-id="e1e32-107">Définition</span><span class="sxs-lookup"><span data-stu-id="e1e32-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="e1e32-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="e1e32-108">Required.</span></span> <span data-ttu-id="e1e32-109">`Boolean`formule.</span><span class="sxs-lookup"><span data-stu-id="e1e32-109">`Boolean` expression.</span></span> <span data-ttu-id="e1e32-110">Si `condition` `False`est `Nothing`, Visual Basic le traite comme.</span><span class="sxs-lookup"><span data-stu-id="e1e32-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="e1e32-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1e32-111">Optional.</span></span> <span data-ttu-id="e1e32-112">Une ou plusieurs instructions qui `While`suivent sont `True`exécutées à `condition` chaque fois.</span><span class="sxs-lookup"><span data-stu-id="e1e32-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="e1e32-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1e32-113">Optional.</span></span> <span data-ttu-id="e1e32-114">Transfère le contrôle à l’itération suivante du `While` bloc.</span><span class="sxs-lookup"><span data-stu-id="e1e32-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="e1e32-115">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1e32-115">Optional.</span></span> <span data-ttu-id="e1e32-116">Transfère le `While` contrôle hors du bloc.</span><span class="sxs-lookup"><span data-stu-id="e1e32-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="e1e32-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="e1e32-117">Required.</span></span> <span data-ttu-id="e1e32-118">Met fin à la définition du bloc `While`.</span><span class="sxs-lookup"><span data-stu-id="e1e32-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e32-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e1e32-119">Remarks</span></span>  
 <span data-ttu-id="e1e32-120">Utilisez une `While...End While` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, tant qu’une condition est conservée `True`.</span><span class="sxs-lookup"><span data-stu-id="e1e32-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="e1e32-121">Si vous souhaitez plus de flexibilité lorsque vous testez la condition ou le résultat pour lequel vous la Testez, vous pouvez préférer le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e1e32-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="e1e32-122">Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="e1e32-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1e32-123">Le `While` mot clé est également utilisé dans le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md), la [clause Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) et la [clause Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e1e32-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="e1e32-124">Si `condition` est `True`, tout `statements` est exécuté jusqu’à ce `End While` que l’instruction soit rencontrée.</span><span class="sxs-lookup"><span data-stu-id="e1e32-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="e1e32-125">Le contrôle retourne ensuite à `While` l’instruction et `condition` est à nouveau vérifié.</span><span class="sxs-lookup"><span data-stu-id="e1e32-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="e1e32-126">Si `condition` est toujours `True`, le processus est répété.</span><span class="sxs-lookup"><span data-stu-id="e1e32-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="e1e32-127">Si c’est `False`le cas, le contrôle passe à l’instruction `End While` qui suit l’instruction.</span><span class="sxs-lookup"><span data-stu-id="e1e32-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="e1e32-128">L' `While` instruction vérifie toujours la condition avant de démarrer la boucle.</span><span class="sxs-lookup"><span data-stu-id="e1e32-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="e1e32-129">Le bouclage continue tant que la condition `True`est conservée.</span><span class="sxs-lookup"><span data-stu-id="e1e32-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="e1e32-130">Si `condition` est`False` lorsque vous entrez pour la première fois la boucle, elle ne s’exécute pas même une fois.</span><span class="sxs-lookup"><span data-stu-id="e1e32-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="e1e32-131">Le `condition` résultat est généralement une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de`True` type `False`de [données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (ou).</span><span class="sxs-lookup"><span data-stu-id="e1e32-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="e1e32-132">Cette expression peut inclure une valeur d’un autre type de données, tel qu’un type numérique, qui a été `Boolean`converti en.</span><span class="sxs-lookup"><span data-stu-id="e1e32-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="e1e32-133">Vous pouvez imbriquer `While` des boucles en plaçant une boucle dans une autre.</span><span class="sxs-lookup"><span data-stu-id="e1e32-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="e1e32-134">Vous pouvez également imbriquer différents genres de structures de contrôle dans l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="e1e32-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="e1e32-135">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="e1e32-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="e1e32-136">Quitter pendant</span><span class="sxs-lookup"><span data-stu-id="e1e32-136">Exit While</span></span>  
 <span data-ttu-id="e1e32-137">L’instruction [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de `While` quitter une boucle.</span><span class="sxs-lookup"><span data-stu-id="e1e32-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="e1e32-138">`Exit While`transfère immédiatement le contrôle à l’instruction qui suit `End While` l’instruction.</span><span class="sxs-lookup"><span data-stu-id="e1e32-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="e1e32-139">Vous utilisez `Exit While` généralement une fois que certaines conditions ont été évaluées (par `If...Then...Else` exemple, dans une structure).</span><span class="sxs-lookup"><span data-stu-id="e1e32-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="e1e32-140">Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e1e32-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="e1e32-141">Vous pouvez utiliser `Exit While` lorsque vous testez une condition susceptible de provoquer une *boucle*infinie, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini.</span><span class="sxs-lookup"><span data-stu-id="e1e32-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="e1e32-142">Vous pouvez ensuite utiliser `Exit While` pour échapper la boucle.</span><span class="sxs-lookup"><span data-stu-id="e1e32-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="e1e32-143">Vous pouvez placer n’importe quel `Exit While` nombre d’instructions n' `While` importe où dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="e1e32-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="e1e32-144">Lorsqu’il est utilisé dans `While` les boucles `Exit While` imbriquées, transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e32-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="e1e32-145">L' `Continue While` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e1e32-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="e1e32-146">Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e1e32-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e32-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1e32-147">Example</span></span>  
 <span data-ttu-id="e1e32-148">Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu' `index` à ce que la variable soit supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="e1e32-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="e1e32-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1e32-149">Example</span></span>  
 <span data-ttu-id="e1e32-150">L’exemple suivant illustre l’utilisation des `Continue While` instructions et. `Exit While`</span><span class="sxs-lookup"><span data-stu-id="e1e32-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="e1e32-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1e32-151">Example</span></span>  
 <span data-ttu-id="e1e32-152">L’exemple suivant lit toutes les lignes d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e1e32-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="e1e32-153">La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.</span><span class="sxs-lookup"><span data-stu-id="e1e32-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="e1e32-154">Dans la `While` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine si le fichier contient des caractères supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e1e32-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="e1e32-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1e32-155">See also</span></span>

- [<span data-ttu-id="e1e32-156">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="e1e32-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="e1e32-157">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="e1e32-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="e1e32-158">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="e1e32-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="e1e32-159">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="e1e32-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="e1e32-160">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="e1e32-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="e1e32-161">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="e1e32-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="e1e32-162">Continue (instruction)</span><span class="sxs-lookup"><span data-stu-id="e1e32-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
