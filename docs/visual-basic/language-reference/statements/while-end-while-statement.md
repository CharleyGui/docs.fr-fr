---
title: While...End While (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391584"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="3f7a5-102">While...End While, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="3f7a5-103">Exécute une série d’instructions tant qu’une condition donnée a la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f7a5-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="3f7a5-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="3f7a5-105">Parts</span></span>  
  
|<span data-ttu-id="3f7a5-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3f7a5-106">Term</span></span>|<span data-ttu-id="3f7a5-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3f7a5-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="3f7a5-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-108">Required.</span></span> <span data-ttu-id="3f7a5-109">Expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-109">`Boolean` expression.</span></span> <span data-ttu-id="3f7a5-110">Si `condition` est `Nothing` , Visual Basic le traite comme `False` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="3f7a5-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-111">Optional.</span></span> <span data-ttu-id="3f7a5-112">Une ou plusieurs instructions `While` qui suivent sont exécutées à chaque fois `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="3f7a5-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-113">Optional.</span></span> <span data-ttu-id="3f7a5-114">Transfère le contrôle à l’itération suivante du `While` bloc.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="3f7a5-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-115">Optional.</span></span> <span data-ttu-id="3f7a5-116">Transfère le contrôle hors du `While` bloc.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="3f7a5-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-117">Required.</span></span> <span data-ttu-id="3f7a5-118">Met fin à la définition du bloc `While`.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f7a5-119">Notes</span><span class="sxs-lookup"><span data-stu-id="3f7a5-119">Remarks</span></span>  
 <span data-ttu-id="3f7a5-120">Utilisez une `While...End While` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, tant qu’une condition est conservée `True` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="3f7a5-121">Si vous souhaitez plus de flexibilité lorsque vous testez la condition ou le résultat pour lequel vous la Testez, vous pouvez préférer le [... Instruction de boucle](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="3f7a5-122">Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](for-next-statement.md) est généralement un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-122">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f7a5-123">Le `While` mot clé est également utilisé dans le [... Instruction de boucle](do-loop-statement.md), la [clause Skip While](../queries/skip-while-clause.md) et la [clause Take While](../queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-123">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="3f7a5-124">Si `condition` est `True` , tout est `statements` exécuté jusqu’à ce que l' `End While` instruction soit rencontrée.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="3f7a5-125">Le contrôle retourne ensuite à l' `While` instruction et `condition` est à nouveau vérifié.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="3f7a5-126">Si `condition` est toujours `True` , le processus est répété.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="3f7a5-127">Si c’est le cas `False` , le contrôle passe à l’instruction qui suit l' `End While` instruction.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="3f7a5-128">L' `While` instruction vérifie toujours la condition avant de démarrer la boucle.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="3f7a5-129">Le bouclage continue tant que la condition est conservée `True` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="3f7a5-130">Si `condition` est `False` lorsque vous entrez pour la première fois la boucle, elle ne s’exécute pas même une fois.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="3f7a5-131">Le `condition` résultat est généralement une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../data-types/boolean-data-type.md) ( `True` ou `False` ).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="3f7a5-132">Cette expression peut inclure une valeur d’un autre type de données, tel qu’un type numérique, qui a été converti en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3f7a5-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="3f7a5-133">Vous pouvez imbriquer `While` des boucles en plaçant une boucle dans une autre.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="3f7a5-134">Vous pouvez également imbriquer différents genres de structures de contrôle dans l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="3f7a5-135">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-135">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="3f7a5-136">Quitter pendant</span><span class="sxs-lookup"><span data-stu-id="3f7a5-136">Exit While</span></span>  
 <span data-ttu-id="3f7a5-137">L’instruction [Exit while](exit-statement.md) peut fournir une autre façon de quitter une `While` boucle.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-137">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="3f7a5-138">`Exit While`transfère immédiatement le contrôle à l’instruction qui suit l' `End While` instruction.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="3f7a5-139">Vous utilisez généralement `Exit While` une fois que certaines conditions ont été évaluées (par exemple, dans une `If...Then...Else` structure).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="3f7a5-140">Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="3f7a5-141">Vous pouvez utiliser `Exit While` lorsque vous testez une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="3f7a5-142">Vous pouvez ensuite utiliser `Exit While` pour échapper la boucle.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="3f7a5-143">Vous pouvez placer n’importe quel nombre d' `Exit While` instructions n’importe où dans la `While` boucle.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="3f7a5-144">Lorsqu’il est utilisé dans `While` les boucles imbriquées, `Exit While` transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="3f7a5-145">L' `Continue While` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="3f7a5-146">Pour plus d’informations, consultez [instruction continue](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3f7a5-146">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f7a5-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f7a5-147">Example</span></span>  
 <span data-ttu-id="3f7a5-148">Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la `index` variable soit supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="3f7a5-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f7a5-149">Example</span></span>  
 <span data-ttu-id="3f7a5-150">L’exemple suivant illustre l’utilisation des `Continue While` `Exit While` instructions et.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="3f7a5-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f7a5-151">Example</span></span>  
 <span data-ttu-id="3f7a5-152">L’exemple suivant lit toutes les lignes d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="3f7a5-153">La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="3f7a5-154">Dans la `While` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine si le fichier contient des caractères supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3f7a5-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="3f7a5-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f7a5-155">See also</span></span>

- [<span data-ttu-id="3f7a5-156">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="3f7a5-156">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3f7a5-157">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-157">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="3f7a5-158">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-158">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="3f7a5-159">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-159">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="3f7a5-160">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="3f7a5-160">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3f7a5-161">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="3f7a5-162">Continue (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-162">Continue Statement</span></span>](continue-statement.md)
