---
title: 'Comment : créer une expression lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: cc2de38f7375848d104edff6f419656d9caa9cb2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071922"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="7a02a-102">Comment : créer une expression lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a02a-102">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="7a02a-103">Une *expression lambda* est une fonction ou une sous-routine qui n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="7a02a-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="7a02a-104">Une expression lambda peut être utilisée partout où un type délégué est valide.</span><span class="sxs-lookup"><span data-stu-id="7a02a-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="7a02a-105">Pour créer une fonction d’expression lambda sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="7a02a-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="7a02a-106">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function` , comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a02a-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="7a02a-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="7a02a-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="7a02a-108">Entre parenthèses, directement après `Function` , tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="7a02a-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="7a02a-109">Notez que vous ne spécifiez pas de nom après `Function` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="7a02a-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="7a02a-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="7a02a-111">À la suite de la liste de paramètres, tapez une seule expression en tant que corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="7a02a-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="7a02a-112">La valeur évaluée par l’expression est la valeur retournée par la fonction.</span><span class="sxs-lookup"><span data-stu-id="7a02a-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="7a02a-113">Vous n’utilisez pas `As` de clause pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="7a02a-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="7a02a-114">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="7a02a-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="7a02a-115">En guise d’alternative, le même résultat est obtenu par l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a02a-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="7a02a-116">Pour créer une sous-routine d’expression lambda sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="7a02a-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="7a02a-117">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub` , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7a02a-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="7a02a-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="7a02a-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="7a02a-119">Entre parenthèses, directement après `Sub` , tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="7a02a-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="7a02a-120">Notez que vous ne spécifiez pas de nom après `Sub` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="7a02a-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="7a02a-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="7a02a-122">À la suite de la liste de paramètres, tapez une seule instruction en tant que corps de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="7a02a-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="7a02a-123">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7a02a-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="7a02a-124">Pour créer une fonction d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="7a02a-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="7a02a-125">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function` , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7a02a-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="7a02a-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="7a02a-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="7a02a-127">Entre parenthèses, directement après `Function` , tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="7a02a-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="7a02a-128">Notez que vous ne spécifiez pas de nom après `Function` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="7a02a-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="7a02a-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="7a02a-130">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="7a02a-130">Press ENTER.</span></span> <span data-ttu-id="7a02a-131">L' `End Function` instruction est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="7a02a-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="7a02a-132">Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et retourner la valeur.</span><span class="sxs-lookup"><span data-stu-id="7a02a-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="7a02a-133">Vous n’utilisez pas `As` de clause pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="7a02a-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="7a02a-134">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="7a02a-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="7a02a-135">Pour créer une sous-routine d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="7a02a-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="7a02a-136">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a02a-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="7a02a-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="7a02a-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="7a02a-138">Entre parenthèses, directement après `Sub` , tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="7a02a-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="7a02a-139">Notez que vous ne spécifiez pas de nom après `Sub` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="7a02a-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="7a02a-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="7a02a-141">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="7a02a-141">Press ENTER.</span></span> <span data-ttu-id="7a02a-142">L' `End Sub` instruction est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="7a02a-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="7a02a-143">Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous-routine est appelée.</span><span class="sxs-lookup"><span data-stu-id="7a02a-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="7a02a-144">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7a02a-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="7a02a-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a02a-145">Example</span></span>  

 <span data-ttu-id="7a02a-146">Les expressions lambda sont généralement utilisées pour définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="7a02a-147">Dans l’exemple suivant, la <xref:System.Diagnostics.Process.GetProcesses%2A> méthode retourne un tableau des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7a02a-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="7a02a-148">La <xref:System.Linq.Enumerable.Where%2A> méthode de la <xref:System.Linq.Enumerable> classe requiert un `Boolean` délégué comme argument.</span><span class="sxs-lookup"><span data-stu-id="7a02a-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="7a02a-149">L’expression lambda dans l’exemple est utilisée à cette fin.</span><span class="sxs-lookup"><span data-stu-id="7a02a-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="7a02a-150">Elle retourne `True` pour chaque processus qui n’a qu’un seul thread, et ceux-ci sont sélectionnés dans `filteredList` .</span><span class="sxs-lookup"><span data-stu-id="7a02a-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="7a02a-151">L’exemple précédent est équivalent au code suivant, qui est écrit dans la syntaxe LINQ (Language-Integrated Query) :</span><span class="sxs-lookup"><span data-stu-id="7a02a-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7a02a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a02a-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="7a02a-153">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="7a02a-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="7a02a-154">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="7a02a-154">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="7a02a-155">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="7a02a-155">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7a02a-156">Délégués</span><span class="sxs-lookup"><span data-stu-id="7a02a-156">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="7a02a-157">Comment : passer des procédures à une autre procédure en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a02a-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="7a02a-158">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="7a02a-158">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="7a02a-159">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a02a-159">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
