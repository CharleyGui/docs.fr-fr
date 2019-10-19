---
title: Do...Loop, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583441"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="4e78e-102">Do...Loop, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e78e-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="4e78e-103">Répète un bloc d’instructions tant qu’une condition `Boolean` est `True` ou jusqu’à ce que la condition soit `True`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e78e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e78e-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="4e78e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4e78e-105">Parts</span></span>  
  
|<span data-ttu-id="4e78e-106">Terme</span><span class="sxs-lookup"><span data-stu-id="4e78e-106">Term</span></span>|<span data-ttu-id="4e78e-107">Définition</span><span class="sxs-lookup"><span data-stu-id="4e78e-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="4e78e-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="4e78e-108">Required.</span></span> <span data-ttu-id="4e78e-109">Démarre la définition de la boucle de `Do`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="4e78e-110">Requis, sauf si l'option `Until` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4e78e-110">Required unless `Until` is used.</span></span> <span data-ttu-id="4e78e-111">Répétez la boucle jusqu’à ce que `condition` soit `False`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="4e78e-112">Requis, sauf si l'option `While` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4e78e-112">Required unless `While` is used.</span></span> <span data-ttu-id="4e78e-113">Répétez la boucle jusqu’à ce que `condition` soit `True`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="4e78e-114">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="4e78e-114">Optional.</span></span> <span data-ttu-id="4e78e-115">expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-115">`Boolean` expression.</span></span> <span data-ttu-id="4e78e-116">Si `condition` est `Nothing`, Visual Basic le traite comme `False`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="4e78e-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="4e78e-117">Optional.</span></span> <span data-ttu-id="4e78e-118">Une ou plusieurs instructions qui sont répétées tant que `condition` n’est `True`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="4e78e-119">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="4e78e-119">Optional.</span></span> <span data-ttu-id="4e78e-120">Transfère le contrôle à l’itération suivante de la boucle `Do`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="4e78e-121">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="4e78e-121">Optional.</span></span> <span data-ttu-id="4e78e-122">Transfère le contrôle hors de la boucle de `Do`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="4e78e-123">Requis.</span><span class="sxs-lookup"><span data-stu-id="4e78e-123">Required.</span></span> <span data-ttu-id="4e78e-124">Termine la définition de la boucle `Do`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e78e-125">Notes</span><span class="sxs-lookup"><span data-stu-id="4e78e-125">Remarks</span></span>  
 <span data-ttu-id="4e78e-126">Utilisez une structure `Do...Loop` lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, jusqu’à ce qu’une condition soit satisfaite.</span><span class="sxs-lookup"><span data-stu-id="4e78e-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="4e78e-127">Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="4e78e-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="4e78e-128">Vous pouvez utiliser `While` ou `Until` pour spécifier `condition`, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="4e78e-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="4e78e-129">Vous ne pouvez tester `condition` qu’une seule fois, au début ou à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="4e78e-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="4e78e-130">Si vous testez `condition` au début de la boucle (dans l’instruction `Do`), la boucle peut ne pas s’exécuter même une fois.</span><span class="sxs-lookup"><span data-stu-id="4e78e-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="4e78e-131">Si vous testez à la fin de la boucle (dans l’instruction `Loop`), la boucle s’exécute toujours au moins une fois.</span><span class="sxs-lookup"><span data-stu-id="4e78e-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="4e78e-132">La condition résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="4e78e-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="4e78e-133">Cela comprend les valeurs d’autres types de données, tels que les types numériques, qui ont été converties en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="4e78e-134">Vous pouvez imbriquer des boucles `Do` en plaçant une boucle dans une autre.</span><span class="sxs-lookup"><span data-stu-id="4e78e-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="4e78e-135">Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux.</span><span class="sxs-lookup"><span data-stu-id="4e78e-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="4e78e-136">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="4e78e-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e78e-137">La structure `Do...Loop` offre plus de souplesse que le [tout... End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , car elle vous permet de décider s’il faut mettre fin à la boucle lorsque `condition` cesse d’être `True` ou lorsqu’elle est d’abord `True`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="4e78e-138">Elle vous permet également de tester `condition` au début ou à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="4e78e-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="4e78e-139">Quitter</span><span class="sxs-lookup"><span data-stu-id="4e78e-139">Exit Do</span></span>  
 <span data-ttu-id="4e78e-140">L’instruction [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de quitter une `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="4e78e-141">`Exit Do` transfère immédiatement le contrôle à l’instruction qui suit l’instruction `Loop`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="4e78e-142">`Exit Do` est souvent utilisé après l’évaluation d’une condition, par exemple dans une structure `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="4e78e-143">Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="4e78e-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="4e78e-144">L’une des utilisations de `Exit Do` consiste à tester une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois beaucoup voire infini.</span><span class="sxs-lookup"><span data-stu-id="4e78e-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="4e78e-145">Vous pouvez utiliser `Exit Do` pour échapper à la boucle.</span><span class="sxs-lookup"><span data-stu-id="4e78e-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="4e78e-146">Vous pouvez inclure n’importe quel nombre d’instructions `Exit Do` n’importe où dans une `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="4e78e-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="4e78e-147">Lorsqu’il est utilisé dans des boucles `Do` imbriquées, `Exit Do` transfère le contrôle hors de la boucle la plus profonde et le plus élevé de l’imbrication.</span><span class="sxs-lookup"><span data-stu-id="4e78e-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e78e-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e78e-148">Example</span></span>  
 <span data-ttu-id="4e78e-149">Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la variable `index` soit supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="4e78e-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="4e78e-150">La clause `Until` se trouve à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="4e78e-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="4e78e-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e78e-151">Example</span></span>  
 <span data-ttu-id="4e78e-152">L’exemple suivant utilise une clause `While` au lieu d’une clause `Until`, et `condition` est testé au début de la boucle et non à la fin.</span><span class="sxs-lookup"><span data-stu-id="4e78e-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="4e78e-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e78e-153">Example</span></span>  
 <span data-ttu-id="4e78e-154">Dans l’exemple suivant, `condition` arrête la boucle lorsque la variable `index` est supérieure à 100.</span><span class="sxs-lookup"><span data-stu-id="4e78e-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="4e78e-155">Toutefois, l’instruction `If` dans la boucle entraîne l’arrêt de la boucle par l’instruction `Exit Do` quand la variable d’index est supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="4e78e-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="4e78e-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e78e-156">Example</span></span>  
 <span data-ttu-id="4e78e-157">L’exemple suivant lit toutes les lignes d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="4e78e-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="4e78e-158">La méthode <xref:System.IO.File.OpenText%2A> ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.</span><span class="sxs-lookup"><span data-stu-id="4e78e-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="4e78e-159">Dans la condition `Do...Loop`, la méthode <xref:System.IO.StreamReader.Peek%2A> de l' `StreamReader` détermine s’il existe des caractères supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="4e78e-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="4e78e-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e78e-160">See also</span></span>

- [<span data-ttu-id="4e78e-161">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="4e78e-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="4e78e-162">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="4e78e-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="4e78e-163">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="4e78e-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="4e78e-164">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="4e78e-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="4e78e-165">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="4e78e-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="4e78e-166">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="4e78e-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
