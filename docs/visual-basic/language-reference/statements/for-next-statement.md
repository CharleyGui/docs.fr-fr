---
title: For...Next (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404639"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="e03ba-102">For...Next, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e03ba-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="e03ba-103">Répète un groupe d’instructions un nombre de fois spécifié.</span><span class="sxs-lookup"><span data-stu-id="e03ba-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="e03ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e03ba-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="e03ba-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="e03ba-105">Parts</span></span>

|<span data-ttu-id="e03ba-106">Élément</span><span class="sxs-lookup"><span data-stu-id="e03ba-106">Part</span></span>|<span data-ttu-id="e03ba-107">Description</span><span class="sxs-lookup"><span data-stu-id="e03ba-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="e03ba-108">Obligatoire dans l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-108">Required in the `For` statement.</span></span> <span data-ttu-id="e03ba-109">Variable numérique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-109">Numeric variable.</span></span> <span data-ttu-id="e03ba-110">Variable de contrôle de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-110">The control variable for the loop.</span></span> <span data-ttu-id="e03ba-111">Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="e03ba-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-112">Optional.</span></span> <span data-ttu-id="e03ba-113">Type de données de `counter` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-113">Data type of `counter`.</span></span> <span data-ttu-id="e03ba-114">Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="e03ba-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e03ba-115">Required.</span></span> <span data-ttu-id="e03ba-116">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-116">Numeric expression.</span></span> <span data-ttu-id="e03ba-117">Valeur initiale de `counter`.</span><span class="sxs-lookup"><span data-stu-id="e03ba-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="e03ba-118">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e03ba-118">Required.</span></span> <span data-ttu-id="e03ba-119">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-119">Numeric expression.</span></span> <span data-ttu-id="e03ba-120">Valeur finale de `counter` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="e03ba-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-121">Optional.</span></span> <span data-ttu-id="e03ba-122">Expression numérique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-122">Numeric expression.</span></span> <span data-ttu-id="e03ba-123">Quantité d' `counter` incrémentation à chaque fois par la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="e03ba-124">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-124">Optional.</span></span> <span data-ttu-id="e03ba-125">Une ou plusieurs instructions entre `For` et `Next` qui exécutent le nombre de fois spécifié.</span><span class="sxs-lookup"><span data-stu-id="e03ba-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="e03ba-126">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-126">Optional.</span></span> <span data-ttu-id="e03ba-127">Transfère le contrôle à l’itération de boucle suivante.</span><span class="sxs-lookup"><span data-stu-id="e03ba-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="e03ba-128">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-128">Optional.</span></span> <span data-ttu-id="e03ba-129">Transfère le contrôle hors de la `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="e03ba-130">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e03ba-130">Required.</span></span> <span data-ttu-id="e03ba-131">Termine la définition de la `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="e03ba-132">Le `To` mot clé est utilisé dans cette instruction pour spécifier la plage du compteur.</span><span class="sxs-lookup"><span data-stu-id="e03ba-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="e03ba-133">Vous pouvez également utiliser ce mot clé dans la [sélection... Instruction case](select-case-statement.md) et déclarations de tableau.</span><span class="sxs-lookup"><span data-stu-id="e03ba-133">You can also use this keyword in the [Select...Case Statement](select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="e03ba-134">Pour plus d’informations sur les déclarations de tableau, consultez [Dim, instruction](dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-134">For more information about array declarations, see [Dim Statement](dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="e03ba-135"> Exemples simples</span><span class="sxs-lookup"><span data-stu-id="e03ba-135">Simple Examples</span></span>

<span data-ttu-id="e03ba-136">Vous utilisez une `For` structure... `Next` lorsque vous souhaitez répéter un ensemble d’instructions un nombre défini de fois.</span><span class="sxs-lookup"><span data-stu-id="e03ba-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="e03ba-137">Dans l’exemple suivant, la `index` variable commence par une valeur de 1 et est incrémentée à chaque itération de la boucle, se terminant après que la valeur de `index` atteint 5.</span><span class="sxs-lookup"><span data-stu-id="e03ba-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="e03ba-138">Dans l’exemple suivant, la `number` variable commence à 2 et est réduite de 0,25 sur chaque itération de la boucle, se terminant après que la valeur de `number` atteint 0.</span><span class="sxs-lookup"><span data-stu-id="e03ba-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="e03ba-139">L' `Step` argument de `-.25` réduit la valeur de 0,25 à chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="e03ba-140">Une [fois... Instruction End While](while-end-while-statement.md) ou [do... Loop](do-loop-statement.md) fonctionne bien lorsque vous ne connaissez pas à l’avance le nombre de fois où les instructions doivent être exécutées dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-140">A [While...End While Statement](while-end-while-statement.md) or [Do...Loop Statement](do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="e03ba-141">Toutefois, lorsque vous prévoyez d’exécuter la boucle un nombre spécifique de fois, une `For` boucle... `Next` est un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="e03ba-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="e03ba-142">Vous déterminez le nombre d’itérations lorsque vous entrez pour la première fois la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="e03ba-143">Imbrication de boucles</span><span class="sxs-lookup"><span data-stu-id="e03ba-143">Nesting Loops</span></span>

<span data-ttu-id="e03ba-144">Vous pouvez imbriquer `For` des boucles en plaçant une boucle dans une autre.</span><span class="sxs-lookup"><span data-stu-id="e03ba-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="e03ba-145">L’exemple suivant montre des structures imbriquées `For` ... `Next` qui ont des valeurs d’étape différentes.</span><span class="sxs-lookup"><span data-stu-id="e03ba-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="e03ba-146">La boucle externe crée une chaîne pour chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="e03ba-147">La boucle interne décrémente une variable de compteur de boucle pour chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="e03ba-148">Lors de l’imbrication de boucles, chaque boucle doit avoir une `counter` variable unique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="e03ba-149">Vous pouvez également imbriquer des structures de contrôle de types différents les unes dans les autres.</span><span class="sxs-lookup"><span data-stu-id="e03ba-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="e03ba-150">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-150">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="e03ba-151">Quitter pour et continuer pour</span><span class="sxs-lookup"><span data-stu-id="e03ba-151">Exit For and Continue For</span></span>

<span data-ttu-id="e03ba-152">L' `Exit For` instruction quitte immédiatement `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e03ba-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="e03ba-153">effectue une boucle et transfère le contrôle à l’instruction qui suit l' `Next` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="e03ba-154">L' `Continue For` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="e03ba-155">Pour plus d’informations, consultez [instruction continue](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-155">For more information, see [Continue Statement](continue-statement.md).</span></span>

<span data-ttu-id="e03ba-156">L’exemple suivant illustre l’utilisation des `Continue For` `Exit For` instructions et.</span><span class="sxs-lookup"><span data-stu-id="e03ba-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="e03ba-157">Vous pouvez placer n’importe quel nombre d' `Exit For` instructions dans un `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e03ba-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="e03ba-158">loop.</span><span class="sxs-lookup"><span data-stu-id="e03ba-158">loop.</span></span> <span data-ttu-id="e03ba-159">En cas d’utilisation dans des `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e03ba-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="e03ba-160">boucles, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau supérieur d’imbrication suivant.</span><span class="sxs-lookup"><span data-stu-id="e03ba-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="e03ba-161">`Exit For`est souvent utilisé après l’évaluation d’une condition (par exemple, dans une `If` ... `Then` ...`Else` structure).</span><span class="sxs-lookup"><span data-stu-id="e03ba-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="e03ba-162">Vous pouvez utiliser `Exit For` pour les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e03ba-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="e03ba-163">La poursuite de l’itération est inutile ou impossible.</span><span class="sxs-lookup"><span data-stu-id="e03ba-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="e03ba-164">Une valeur erronée ou une demande d’arrêt peut créer cette condition.</span><span class="sxs-lookup"><span data-stu-id="e03ba-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="e03ba-165">`Try`... `Catch` ...`Finally` l’instruction intercepte une exception.</span><span class="sxs-lookup"><span data-stu-id="e03ba-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="e03ba-166">Vous pouvez utiliser `Exit For` à la fin du `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="e03ba-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="e03ba-167">Vous avez une boucle infinie, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini.</span><span class="sxs-lookup"><span data-stu-id="e03ba-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="e03ba-168">Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour échapper la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="e03ba-169">Pour plus d’informations, consultez [do... Instruction de boucle](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-169">For more information, see [Do...Loop Statement](do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="e03ba-170">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="e03ba-170">Technical Implementation</span></span>

<span data-ttu-id="e03ba-171">Quand une `For` boucle... `Next` démarre, Visual Basic évalue `start` , `end` et `step` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="e03ba-172">Visual Basic évalue ces valeurs uniquement à ce moment-là, puis affecte `start` à `counter` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="e03ba-173">Avant l’exécution du bloc d’instructions, Visual Basic est comparé `counter` à `end` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="e03ba-174">Si `counter` est déjà supérieur à la `end` valeur (ou plus petit si `step` est négatif), la `For` boucle se termine et le contrôle passe à l’instruction qui suit l' `Next` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="e03ba-175">Dans le cas contraire, le bloc d’instructions s’exécute.</span><span class="sxs-lookup"><span data-stu-id="e03ba-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="e03ba-176">Chaque fois que Visual Basic rencontre l' `Next` instruction, il s’incrémente `counter` de `step` et retourne à l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="e03ba-177">Là encore, il `counter` effectue une comparaison avec `end` , et il exécute à nouveau le bloc ou quitte la boucle, en fonction du résultat.</span><span class="sxs-lookup"><span data-stu-id="e03ba-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="e03ba-178">Ce processus se poursuit jusqu’à la `counter` réussite `end` ou l’exécution d’une `Exit For` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="e03ba-179">La boucle ne s’arrête pas tant que `counter` n’a pas réussi `end` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="e03ba-180">Si `counter` est égal à `end` , la boucle continue.</span><span class="sxs-lookup"><span data-stu-id="e03ba-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="e03ba-181">La comparaison qui détermine s’il faut exécuter le bloc est `counter`  <=  `end` si `step` est positif et `counter`  >=  `end` si `step` est négatif.</span><span class="sxs-lookup"><span data-stu-id="e03ba-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="e03ba-182">Si vous modifiez la valeur de `counter` dans une boucle, votre code peut être plus difficile à lire et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="e03ba-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="e03ba-183">La modification de la valeur de `start` , `end` ou `step` n’affecte pas les valeurs d’itération qui ont été déterminées lors de la première entrée de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="e03ba-184">Si vous imbriquez des boucles, le compilateur signale une erreur s’il rencontre l' `Next` instruction d’un niveau d’imbrication externe avant l' `Next` instruction d’un niveau interne.</span><span class="sxs-lookup"><span data-stu-id="e03ba-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="e03ba-185">Toutefois, le compilateur peut détecter cette erreur qui se chevauche uniquement si vous spécifiez `counter` dans chaque `Next` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="e03ba-186">Argument Step</span><span class="sxs-lookup"><span data-stu-id="e03ba-186">Step Argument</span></span>

<span data-ttu-id="e03ba-187">La valeur de `step` peut être positive ou négative.</span><span class="sxs-lookup"><span data-stu-id="e03ba-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="e03ba-188">Ce paramètre détermine le traitement des boucles en fonction du tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="e03ba-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="e03ba-189">**Valeur de l’étape**</span><span class="sxs-lookup"><span data-stu-id="e03ba-189">**Step value**</span></span>|<span data-ttu-id="e03ba-190">**La boucle s’exécute si**</span><span class="sxs-lookup"><span data-stu-id="e03ba-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="e03ba-191">Positif ou zéro</span><span class="sxs-lookup"><span data-stu-id="e03ba-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="e03ba-192">Negative</span><span class="sxs-lookup"><span data-stu-id="e03ba-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="e03ba-193">La valeur par défaut de `step` est 1.</span><span class="sxs-lookup"><span data-stu-id="e03ba-193">The default value of `step` is 1.</span></span>

### <a name="counter-argument"></a><a name="BKMK_Counter"></a><span data-ttu-id="e03ba-194">Argument de compteur</span><span class="sxs-lookup"><span data-stu-id="e03ba-194">Counter Argument</span></span>

<span data-ttu-id="e03ba-195">Le tableau suivant indique si `counter` définit une nouvelle variable locale dont la portée est limitée à la totalité de la `For…Next` boucle.</span><span class="sxs-lookup"><span data-stu-id="e03ba-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="e03ba-196">Cette détermination varie selon que `datatype` est présent et si `counter` est déjà défini.</span><span class="sxs-lookup"><span data-stu-id="e03ba-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="e03ba-197">Est `datatype` présent ?</span><span class="sxs-lookup"><span data-stu-id="e03ba-197">Is `datatype` present?</span></span>|<span data-ttu-id="e03ba-198">Est `counter` déjà défini ?</span><span class="sxs-lookup"><span data-stu-id="e03ba-198">Is `counter` already defined?</span></span>|<span data-ttu-id="e03ba-199">Result (indique si `counter` une nouvelle variable locale est étendue à l’ensemble de la `For...Next` boucle)</span><span class="sxs-lookup"><span data-stu-id="e03ba-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="e03ba-200">Non</span><span class="sxs-lookup"><span data-stu-id="e03ba-200">No</span></span>|<span data-ttu-id="e03ba-201">Oui</span><span class="sxs-lookup"><span data-stu-id="e03ba-201">Yes</span></span>|<span data-ttu-id="e03ba-202">Non, car `counter` est déjà défini.</span><span class="sxs-lookup"><span data-stu-id="e03ba-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="e03ba-203">Si la portée de `counter` n’est pas locale à la procédure, un avertissement se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e03ba-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="e03ba-204">Non </span><span class="sxs-lookup"><span data-stu-id="e03ba-204">No</span></span>|<span data-ttu-id="e03ba-205">Non</span><span class="sxs-lookup"><span data-stu-id="e03ba-205">No</span></span>|<span data-ttu-id="e03ba-206">Oui.</span><span class="sxs-lookup"><span data-stu-id="e03ba-206">Yes.</span></span> <span data-ttu-id="e03ba-207">Le type de données est déduit à partir `start` des `end` expressions, et `step` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="e03ba-208">Pour plus d’informations sur l’inférence de type, consultez [instruction Option Infer](option-infer-statement.md) et [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-208">For information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="e03ba-209">Oui</span><span class="sxs-lookup"><span data-stu-id="e03ba-209">Yes</span></span>|<span data-ttu-id="e03ba-210">Oui</span><span class="sxs-lookup"><span data-stu-id="e03ba-210">Yes</span></span>|<span data-ttu-id="e03ba-211">Oui, mais uniquement si la `counter` variable existante est définie à l’extérieur de la procédure.</span><span class="sxs-lookup"><span data-stu-id="e03ba-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="e03ba-212">Cette variable reste séparée.</span><span class="sxs-lookup"><span data-stu-id="e03ba-212">That variable remains separate.</span></span> <span data-ttu-id="e03ba-213">Si la portée de la `counter` variable existante est locale à la procédure, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="e03ba-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="e03ba-214">Oui</span><span class="sxs-lookup"><span data-stu-id="e03ba-214">Yes</span></span>|<span data-ttu-id="e03ba-215">Non</span><span class="sxs-lookup"><span data-stu-id="e03ba-215">No</span></span>|<span data-ttu-id="e03ba-216">Oui.</span><span class="sxs-lookup"><span data-stu-id="e03ba-216">Yes.</span></span>|

<span data-ttu-id="e03ba-217">Le type de données de `counter` détermine le type de l’itération, qui doit être l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="e03ba-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="e03ba-218">, `Byte` ,,, `SByte` `UShort` `Short` `UInteger` , `Integer` , `ULong` ,,, `Long` `Decimal` `Single` , Ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="e03ba-219">Énumération que vous déclarez à l’aide d’une [instruction enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-219">An enumeration that you declare by using an [Enum Statement](enum-statement.md).</span></span>

- <span data-ttu-id="e03ba-220">`Object`.</span><span class="sxs-lookup"><span data-stu-id="e03ba-220">An `Object`.</span></span>

- <span data-ttu-id="e03ba-221">Type `T` qui a les opérateurs suivants, où `B` est un type qui peut être utilisé dans une `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="e03ba-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="e03ba-222">Vous pouvez éventuellement spécifier la `counter` variable dans l' `Next` instruction.</span><span class="sxs-lookup"><span data-stu-id="e03ba-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="e03ba-223">Cette syntaxe améliore la lisibilité de votre programme, en particulier si vous avez des `For` boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e03ba-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="e03ba-224">Vous devez spécifier la variable qui apparaît dans l' `For` instruction correspondante.</span><span class="sxs-lookup"><span data-stu-id="e03ba-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="e03ba-225">Les `start` `end` expressions, et `step` peuvent correspondre à n’importe quel type de données qui s’étend au type de `counter` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="e03ba-226">Si vous utilisez un type défini par l’utilisateur pour `counter` , vous devrez peut-être définir l' `CType` opérateur de conversion pour convertir les types de `start` , `end` ou `step` en type de `counter` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="e03ba-227">Exemple</span><span class="sxs-lookup"><span data-stu-id="e03ba-227">Example</span></span>

<span data-ttu-id="e03ba-228">L’exemple suivant supprime tous les éléments d’une liste générique.</span><span class="sxs-lookup"><span data-stu-id="e03ba-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="e03ba-229">Au lieu d’une variable [for each... Next Statement](for-each-next-statement.md), l’exemple montre une `For` instruction... `Next` qui itère dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="e03ba-229">Instead of a [For Each...Next Statement](for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="e03ba-230">L’exemple utilise cette technique, car la `removeAt` méthode amène les éléments après l’élément supprimé à avoir une valeur d’index inférieure.</span><span class="sxs-lookup"><span data-stu-id="e03ba-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="e03ba-231">Exemple</span><span class="sxs-lookup"><span data-stu-id="e03ba-231">Example</span></span>

<span data-ttu-id="e03ba-232">L’exemple suivant itère au sein d’une énumération déclarée à l’aide d’une [instruction enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e03ba-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="e03ba-233">Exemple</span><span class="sxs-lookup"><span data-stu-id="e03ba-233">Example</span></span>

<span data-ttu-id="e03ba-234">Dans l’exemple suivant, les paramètres d’instruction utilisent une classe qui a des surcharges d’opérateur pour les `+` `-` opérateurs,, `>=` et `<=` .</span><span class="sxs-lookup"><span data-stu-id="e03ba-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="e03ba-235">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e03ba-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="e03ba-236">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="e03ba-236">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="e03ba-237">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="e03ba-237">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="e03ba-238">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="e03ba-238">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="e03ba-239">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="e03ba-239">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="e03ba-240">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="e03ba-240">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="e03ba-241">Regroupements</span><span class="sxs-lookup"><span data-stu-id="e03ba-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
