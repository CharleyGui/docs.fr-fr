---
title: Expressions lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406701"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="8d8d0-102">Expressions lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="8d8d0-103">Une *expression lambda* est une fonction ou une sous-routine sans nom qui peut être utilisée partout où un délégué est valide.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="8d8d0-104">Les expressions lambda peuvent être des fonctions ou des sous-routines et peuvent être sur une ou plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="8d8d0-105">Vous pouvez passer des valeurs de la portée actuelle à une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="8d8d0-106">L' `RemoveHandler` instruction est une exception.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="8d8d0-107">Vous ne pouvez pas passer une expression lambda dans pour le paramètre de délégué de `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="8d8d0-108">Vous créez des expressions lambda à l’aide du `Function` `Sub` mot clé ou, de la même façon que vous créez une fonction ou une sous-routine standard.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="8d8d0-109">Toutefois, les expressions lambda sont incluses dans une instruction.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="8d8d0-110">L’exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="8d8d0-111">L’exemple montre la syntaxe d’expression lambda sur une seule ligne et sur plusieurs lignes pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="8d8d0-112">L’exemple suivant est une expression lambda qui écrit une valeur dans la console.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="8d8d0-113">L’exemple montre la syntaxe de l’expression lambda sur une seule ligne et sur plusieurs lignes pour une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="8d8d0-114">Notez que dans les exemples précédents, les expressions lambda sont assignées à un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="8d8d0-115">Chaque fois que vous faites référence à la variable, vous appelez l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="8d8d0-116">Vous pouvez également déclarer et appeler une expression lambda en même temps, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="8d8d0-117">Une expression lambda peut être retournée en tant que valeur d’un appel de fonction (comme indiqué dans l’exemple de la section [Context](#context) plus loin dans cette rubrique) ou passée comme argument à un paramètre qui accepte un type délégué, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="8d8d0-118">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="8d8d0-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="8d8d0-119">La syntaxe d’une expression lambda ressemble à celle d’une fonction ou d’une sous-routine standard.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="8d8d0-120">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d8d0-120">The differences are as follows:</span></span>

- <span data-ttu-id="8d8d0-121">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="8d8d0-122">Les expressions lambda ne peuvent pas avoir de modificateurs, tels que `Overloads` ou `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="8d8d0-123">Les fonctions lambda sur une seule ligne n’utilisent pas `As` de clause pour désigner le type de retour.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="8d8d0-124">Au lieu de cela, le type est déduit de la valeur à laquelle le corps de l’expression lambda correspond.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="8d8d0-125">Par exemple, si le corps de l’expression lambda est `cust.City = "London"` , son type de retour est `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="8d8d0-126">Dans les fonctions lambda sur plusieurs lignes, vous pouvez spécifier un type de retour à l’aide d’une `As` clause, ou omettre la `As` clause afin que le type de retour soit déduit.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="8d8d0-127">Lorsque la `As` clause est omise pour une fonction lambda multiligne, le type de retour est déduit comme étant le type dominant de toutes les `Return` instructions dans la fonction lambda multiligne.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="8d8d0-128">Le *type dominant* est un type unique auquel tous les autres types peuvent s’étendre.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="8d8d0-129">Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types du tableau peuvent se limiter.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="8d8d0-130">Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="8d8d0-131">Dans ce cas, si `Option Strict` a la valeur `On` , une erreur de compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="8d8d0-132">Par exemple, si les expressions fournies à l' `Return` instruction contiennent des valeurs de type `Integer` , `Long` et `Double` , le tableau résultant est de type `Double` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="8d8d0-133">`Integer`Et `Long` s’étendent à `Double` et à uniquement `Double` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="8d8d0-134">Par conséquent, `Double` est le type dominant.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="8d8d0-135">Pour plus d’informations, consultez [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d0-135">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="8d8d0-136">Le corps d’une fonction sur une seule ligne doit être une expression qui retourne une valeur, et non une instruction.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="8d8d0-137">Il n’existe aucune `Return` instruction pour les fonctions à ligne unique.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="8d8d0-138">La valeur retournée par la fonction sur une seule ligne est la valeur de l’expression dans le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="8d8d0-139">Le corps d’une sous-routine sur une seule ligne doit être une instruction sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="8d8d0-140">Les fonctions et sous-routines sur une seule ligne n’incluent pas d' `End Function` `End Sub` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="8d8d0-141">Vous pouvez spécifier le type de données d’un paramètre d’expression lambda à l’aide du `As` mot clé, ou le type de données du paramètre peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="8d8d0-142">Tous les paramètres doivent avoir des types de données spécifiés ou tous doivent être déduits.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="8d8d0-143">`Optional`les `Paramarray` paramètres et ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="8d8d0-144">Les paramètres génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="8d8d0-145">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="8d8d0-145">Async Lambdas</span></span>

<span data-ttu-id="8d8d0-146">Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l’aide des mots clés [Async](../../../language-reference/modifiers/async.md) et await de l' [opérateur](../../../language-reference/operators/await-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../language-reference/modifiers/async.md) and [Await Operator](../../../language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="8d8d0-147">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="8d8d0-148">Vous pouvez ajouter le même gestionnaire d’événements en utilisant une expression lambda asynchrone dans une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d0-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="8d8d0-149">Pour ajouter ce gestionnaire, ajoutez un modificateur `Async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="8d8d0-150">Pour plus d’informations sur la création et l’utilisation des méthodes Async, consultez [programmation asynchrone avec Async et await](../../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d0-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="8d8d0-151">Context</span><span class="sxs-lookup"><span data-stu-id="8d8d0-151">Context</span></span>

<span data-ttu-id="8d8d0-152">Une expression lambda partage son contexte avec la portée dans laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="8d8d0-153">Il possède les mêmes droits d’accès que tout code écrit dans l’étendue contenante.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="8d8d0-154">Cela comprend l’accès aux variables membres, aux fonctions, aux Subs, `Me` , et aux paramètres et variables locales dans l’étendue contenante.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="8d8d0-155">L’accès aux variables locales et aux paramètres dans l’étendue contenante peut s’étendre au-delà de la durée de vie de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="8d8d0-156">Tant qu’un délégué qui fait référence à une expression lambda n’est pas disponible pour garbage collection, l’accès aux variables dans l’environnement d’origine est conservé.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="8d8d0-157">Dans l’exemple suivant, la variable `target` est locale à `makeTheGame` , la méthode dans laquelle l’expression lambda `playTheGame` est définie.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="8d8d0-158">Notez que l’expression lambda retournée, assignée à `takeAGuess` dans `Main` , a toujours accès à la variable locale `target` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="8d8d0-159">L’exemple suivant illustre la large gamme de droits d’accès de l’expression lambda imbriquée.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="8d8d0-160">Lorsque l’expression lambda retournée est exécutée à partir de `Main` sous `aDel` , elle accède à ces éléments :</span><span class="sxs-lookup"><span data-stu-id="8d8d0-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="8d8d0-161">Champ de la classe dans laquelle il est défini :`aField`</span><span class="sxs-lookup"><span data-stu-id="8d8d0-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="8d8d0-162">Une propriété de la classe dans laquelle elle est définie :`aProp`</span><span class="sxs-lookup"><span data-stu-id="8d8d0-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="8d8d0-163">Paramètre de la méthode `functionWithNestedLambda` , dans lequel elle est définie :`level1`</span><span class="sxs-lookup"><span data-stu-id="8d8d0-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="8d8d0-164">Une variable locale `functionWithNestedLambda` :`localVar`</span><span class="sxs-lookup"><span data-stu-id="8d8d0-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="8d8d0-165">Paramètre de l’expression lambda dans laquelle il est imbriqué :`level2`</span><span class="sxs-lookup"><span data-stu-id="8d8d0-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="8d8d0-166">Convertir en un type délégué</span><span class="sxs-lookup"><span data-stu-id="8d8d0-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="8d8d0-167">Une expression lambda peut être implicitement convertie en un type délégué compatible.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="8d8d0-168">Pour plus d’informations sur les exigences générales en matière de compatibilité, consultez la section [conversion souple des délégués](../delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d0-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="8d8d0-169">Par exemple, l’exemple de code suivant montre une expression lambda qui convertit implicitement en `Func(Of Integer, Boolean)` ou une signature de délégué correspondante.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="8d8d0-170">L’exemple de code suivant montre une expression lambda qui convertit implicitement en `Sub(Of Double, String, Double)` ou une signature de délégué correspondante.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="8d8d0-171">Quand vous assignez des expressions lambda à des délégués ou les passez comme arguments à des procédures, vous pouvez spécifier les noms des paramètres, mais omettre leurs types de données, ce qui permet aux types d’être extraits du délégué.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="8d8d0-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="8d8d0-172">Examples</span></span>

- <span data-ttu-id="8d8d0-173">L’exemple suivant définit une expression lambda qui retourne `True` si l’argument de type valeur Nullable a une valeur assignée, et `False` si sa valeur est `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8d8d0-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="8d8d0-174">L’exemple suivant définit une expression lambda qui retourne l’index du dernier élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="8d8d0-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d8d0-175">See also</span></span>

- [<span data-ttu-id="8d8d0-176">Procédures</span><span class="sxs-lookup"><span data-stu-id="8d8d0-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8d8d0-177">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d8d0-177">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="8d8d0-178">Délégués</span><span class="sxs-lookup"><span data-stu-id="8d8d0-178">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="8d8d0-179">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-179">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="8d8d0-180">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-180">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="8d8d0-181">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="8d8d0-181">Nullable Value Types</span></span>](../data-types/nullable-value-types.md)
- [<span data-ttu-id="8d8d0-182">Comment : passer des procédures à une autre procédure en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d8d0-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="8d8d0-183">Comment : créer une expression lambda</span><span class="sxs-lookup"><span data-stu-id="8d8d0-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="8d8d0-184">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="8d8d0-184">Relaxed Delegate Conversion</span></span>](../delegates/relaxed-delegate-conversion.md)
