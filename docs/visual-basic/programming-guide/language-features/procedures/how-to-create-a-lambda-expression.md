---
title: 'Comment : créer une expression lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 1c65841e4c124252cfa41bcd4d0c305a426687ee
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632348"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="5fb0d-102">Comment : créer une expression lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fb0d-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="5fb0d-103">Une *expression lambda* est une fonction ou une sous-routine qui n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="5fb0d-104">Une expression lambda peut être utilisée partout où un type délégué est valide.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="5fb0d-105">Pour créer une fonction d’expression lambda sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="5fb0d-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="5fb0d-106">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5fb0d-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="5fb0d-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="5fb0d-108">Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="5fb0d-109">Notez que vous ne spécifiez pas de nom après `Function`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="5fb0d-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="5fb0d-111">À la suite de la liste de paramètres, tapez une seule expression en tant que corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="5fb0d-112">La valeur évaluée par l’expression est la valeur retournée par la fonction.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="5fb0d-113">Vous n’utilisez pas de clause `As` pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="5fb0d-114">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="5fb0d-115">En guise d’alternative, le même résultat est obtenu par l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5fb0d-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="5fb0d-116">Pour créer une sous-routine d’expression lambda sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="5fb0d-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="5fb0d-117">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="5fb0d-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="5fb0d-119">Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="5fb0d-120">Notez que vous ne spécifiez pas de nom après `Sub`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="5fb0d-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="5fb0d-122">À la suite de la liste de paramètres, tapez une seule instruction en tant que corps de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="5fb0d-123">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="5fb0d-124">Pour créer une fonction d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="5fb0d-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="5fb0d-125">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="5fb0d-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="5fb0d-127">Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="5fb0d-128">Notez que vous ne spécifiez pas de nom après `Function`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="5fb0d-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="5fb0d-130">Appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-130">Press ENTER.</span></span> <span data-ttu-id="5fb0d-131">L’instruction `End Function` est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="5fb0d-132">Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et retourner la valeur.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="5fb0d-133">Vous n’utilisez pas de clause `As` pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="5fb0d-134">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="5fb0d-135">Pour créer une sous-routine d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="5fb0d-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="5fb0d-136">Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5fb0d-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="5fb0d-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="5fb0d-138">Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="5fb0d-139">Notez que vous ne spécifiez pas de nom après `Sub`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="5fb0d-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="5fb0d-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="5fb0d-141">Appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-141">Press ENTER.</span></span> <span data-ttu-id="5fb0d-142">L’instruction `End Sub` est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="5fb0d-143">Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous-routine est appelée.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="5fb0d-144">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="5fb0d-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="5fb0d-145">Example</span></span>  
 <span data-ttu-id="5fb0d-146">Les expressions lambda sont généralement utilisées pour définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="5fb0d-147">Dans l’exemple suivant, la méthode <xref:System.Diagnostics.Process.GetProcesses%2A> retourne un tableau des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="5fb0d-148">La méthode <xref:System.Linq.Enumerable.Where%2A> de la classe <xref:System.Linq.Enumerable> requiert un délégué `Boolean` comme argument.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="5fb0d-149">L’expression lambda dans l’exemple est utilisée à cette fin.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="5fb0d-150">Il retourne `True` pour chaque processus qui n’a qu’un seul thread, et ceux-ci sont sélectionnés dans `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="5fb0d-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="5fb0d-151">L’exemple précédent est équivalent au code suivant, qui est écrit dans la syntaxe LINQ (Language-Integrated Query) :</span><span class="sxs-lookup"><span data-stu-id="5fb0d-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="5fb0d-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fb0d-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="5fb0d-153">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="5fb0d-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="5fb0d-154">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="5fb0d-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="5fb0d-155">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="5fb0d-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="5fb0d-156">Délégués</span><span class="sxs-lookup"><span data-stu-id="5fb0d-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="5fb0d-157">Guide pratique : passer des procédures à une autre procédure en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fb0d-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="5fb0d-158">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="5fb0d-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="5fb0d-159">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fb0d-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
