---
title: Do...Loop (instruction)
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
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404782"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="3ada2-102">Do...Loop, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ada2-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="3ada2-103">Répète un bloc d’instructions tant qu’une `Boolean` condition est `True` ou jusqu’à ce que la condition devienne `True` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ada2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ada2-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="3ada2-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="3ada2-105">Parts</span></span>  
  
|<span data-ttu-id="3ada2-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3ada2-106">Term</span></span>|<span data-ttu-id="3ada2-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3ada2-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="3ada2-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3ada2-108">Required.</span></span> <span data-ttu-id="3ada2-109">Démarre la définition de la `Do` boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="3ada2-110">Requis, sauf si l'option `Until` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ada2-110">Required unless `Until` is used.</span></span> <span data-ttu-id="3ada2-111">Répétez la boucle jusqu’à ce que `condition` soit `False` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="3ada2-112">Requis, sauf si l'option `While` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ada2-112">Required unless `While` is used.</span></span> <span data-ttu-id="3ada2-113">Répétez la boucle jusqu’à ce que `condition` soit `True` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="3ada2-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ada2-114">Optional.</span></span> <span data-ttu-id="3ada2-115">Expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3ada2-115">`Boolean` expression.</span></span> <span data-ttu-id="3ada2-116">Si `condition` est `Nothing` , Visual Basic le traite comme `False` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="3ada2-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ada2-117">Optional.</span></span> <span data-ttu-id="3ada2-118">Une ou plusieurs instructions qui sont répétées quand, ou jusqu’à, `condition` est `True` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="3ada2-119">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ada2-119">Optional.</span></span> <span data-ttu-id="3ada2-120">Transfère le contrôle à l’itération suivante de la `Do` boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="3ada2-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ada2-121">Optional.</span></span> <span data-ttu-id="3ada2-122">Transfère le contrôle hors de la `Do` boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="3ada2-123">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3ada2-123">Required.</span></span> <span data-ttu-id="3ada2-124">Termine la définition de la `Do` boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ada2-125">Notes</span><span class="sxs-lookup"><span data-stu-id="3ada2-125">Remarks</span></span>  
 <span data-ttu-id="3ada2-126">Utilisez une `Do...Loop` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre indéfini de fois, jusqu’à ce qu’une condition soit satisfaite.</span><span class="sxs-lookup"><span data-stu-id="3ada2-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="3ada2-127">Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](for-next-statement.md) est généralement un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="3ada2-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="3ada2-128">Vous pouvez utiliser `While` ou `Until` pour spécifier `condition` , mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="3ada2-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="3ada2-129">Vous ne pouvez tester `condition` qu’une seule fois, au début ou à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="3ada2-130">Si vous `condition` effectuez un test au début de la boucle (dans l' `Do` instruction), la boucle peut ne pas s’exécuter même une fois.</span><span class="sxs-lookup"><span data-stu-id="3ada2-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="3ada2-131">Si vous testez à la fin de la boucle (dans l' `Loop` instruction), la boucle s’exécute toujours au moins une fois.</span><span class="sxs-lookup"><span data-stu-id="3ada2-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="3ada2-132">La condition résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../data-types/boolean-data-type.md) ( `True` ou `False` ).</span><span class="sxs-lookup"><span data-stu-id="3ada2-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="3ada2-133">Cela comprend les valeurs d’autres types de données, tels que les types numériques, qui ont été converties en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="3ada2-134">Vous pouvez imbriquer `Do` des boucles en plaçant une boucle dans une autre.</span><span class="sxs-lookup"><span data-stu-id="3ada2-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="3ada2-135">Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux.</span><span class="sxs-lookup"><span data-stu-id="3ada2-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="3ada2-136">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="3ada2-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ada2-137">La `Do...Loop` structure offre plus de souplesse que le [tout... End While](while-end-while-statement.md) , car elle vous permet de décider s’il faut mettre fin à la boucle lorsque `condition` cesse d’être `True` ou lorsqu’elle se transforme pour la première fois `True` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="3ada2-138">Elle vous permet également de tester `condition` au début ou à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="3ada2-139">Quitter</span><span class="sxs-lookup"><span data-stu-id="3ada2-139">Exit Do</span></span>  
 <span data-ttu-id="3ada2-140">L’instruction [Exit Do](exit-statement.md) peut fournir une autre façon de quitter un `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="3ada2-141">`Exit Do`transfère immédiatement le contrôle à l’instruction qui suit l' `Loop` instruction.</span><span class="sxs-lookup"><span data-stu-id="3ada2-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="3ada2-142">`Exit Do`est souvent utilisé après l’évaluation d’une condition, par exemple dans une `If...Then...Else` structure.</span><span class="sxs-lookup"><span data-stu-id="3ada2-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="3ada2-143">Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ada2-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="3ada2-144">L’une des utilisations de `Exit Do` consiste à tester une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois trop long, voire infini.</span><span class="sxs-lookup"><span data-stu-id="3ada2-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="3ada2-145">Vous pouvez utiliser `Exit Do` pour échapper à la boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="3ada2-146">Vous pouvez inclure n’importe quel nombre d' `Exit Do` instructions n’importe où dans un `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="3ada2-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="3ada2-147">Lorsqu’il est utilisé dans `Do` les boucles imbriquées, `Exit Do` transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.</span><span class="sxs-lookup"><span data-stu-id="3ada2-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ada2-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ada2-148">Example</span></span>  
 <span data-ttu-id="3ada2-149">Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la `index` variable soit supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="3ada2-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="3ada2-150">La `Until` clause se trouve à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="3ada2-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="3ada2-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ada2-151">Example</span></span>  
 <span data-ttu-id="3ada2-152">L’exemple suivant utilise une `While` clause au lieu d’une `Until` clause, et `condition` est testé au début de la boucle plutôt qu’à la fin.</span><span class="sxs-lookup"><span data-stu-id="3ada2-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="3ada2-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ada2-153">Example</span></span>  
 <span data-ttu-id="3ada2-154">Dans l’exemple suivant, `condition` arrête la boucle lorsque la `index` variable est supérieure à 100.</span><span class="sxs-lookup"><span data-stu-id="3ada2-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="3ada2-155">`If`Toutefois, l’instruction dans la boucle provoque l’arrêt de la boucle par l' `Exit Do` instruction quand la variable d’index est supérieure à 10.</span><span class="sxs-lookup"><span data-stu-id="3ada2-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="3ada2-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ada2-156">Example</span></span>  
 <span data-ttu-id="3ada2-157">L’exemple suivant lit toutes les lignes d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="3ada2-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="3ada2-158">La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.</span><span class="sxs-lookup"><span data-stu-id="3ada2-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="3ada2-159">Dans la `Do...Loop` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine s’il existe des caractères supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3ada2-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="3ada2-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ada2-160">See also</span></span>

- [<span data-ttu-id="3ada2-161">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="3ada2-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3ada2-162">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="3ada2-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="3ada2-163">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="3ada2-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="3ada2-164">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="3ada2-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3ada2-165">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="3ada2-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="3ada2-166">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="3ada2-166">While...End While Statement</span></span>](while-end-while-statement.md)
