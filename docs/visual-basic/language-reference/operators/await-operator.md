---
title: Await, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: b5943e509bb850abc6c74e1b97ccd5fb0038f1e0
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964331"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="0fbb5-102">Await, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fbb5-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="0fbb5-103">Vous appliquez l’opérateur `Await` à un opérande dans une méthode asynchrone ou une expression lambda pour interrompre l’exécution de la méthode jusqu’à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="0fbb5-104">La tâche représente un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-104">The task represents ongoing work.</span></span>

<span data-ttu-id="0fbb5-105">La méthode dans laquelle `Await` est utilisé doit avoir un modificateur [Async](../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="0fbb5-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="0fbb5-106">Cette méthode, définie à l’aide du modificateur `Async` et contenant généralement une ou plusieurs expressions `Await`, est appelée *méthode async*.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="0fbb5-107">Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="0fbb5-108">Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fbb5-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="0fbb5-109">En règle générale, la tâche à laquelle vous appliquez l’opérateur `Await` est la valeur de retour d’un appel à une méthode qui implémente le [modèle asynchrone basé sur les tâches](https://www.microsoft.com/download/details.aspx?id=19957), autrement dit, un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="0fbb5-110">Dans le code suivant, la méthode <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retourne `getContentsTask`, un `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="0fbb5-111">La tâche est une promesse de produire le tableau d’octets réel lorsque l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="0fbb5-112">L'opérateur `Await` est appliqué à `getContentsTask` pour suspendre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="0fbb5-113">Entre-temps, le contrôle revient à l'appelant de `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="0fbb5-114">Quand `getContentsTask` est terminé, l'expression `Await` s'évalue en tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="0fbb5-115">Pour obtenir un exemple complet, consultez [Procédure pas à pas : accès au web avec async et await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="0fbb5-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="0fbb5-116">Vous pouvez télécharger l’exemple à partir des [exemples de code pour les développeurs](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) sur le site web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="0fbb5-117">L'exemple est dans le projet AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="0fbb5-118">Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task(Of TResult)`, le type de l’expression d' `Await` est TResult.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="0fbb5-119">Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task`, l’expression de `Await` ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="0fbb5-120">L'exemple suivant illustre la différence.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="0fbb5-121">Une expression ou une instruction `Await` ne bloque pas le thread sur lequel elle s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="0fbb5-122">Au lieu de cela, il force le compilateur à inscrire le reste de la méthode Async, après l’expression `Await`, en tant que continuation sur la tâche attendue.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="0fbb5-123">Le contrôle revient alors à l'appelant de la méthode async.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="0fbb5-124">Quand la tâche est terminée, elle appelle sa continuation et l'exécution de la méthode async reprend là où elle s'était arrêtée.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="0fbb5-125">Une expression `Await` peut se produire uniquement dans le corps d’une méthode immédiatement englobante ou d’une expression lambda qui est marquée par un modificateur de `Async`.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="0fbb5-126">Le terme *await* sert de mot clé uniquement dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="0fbb5-127">Partout ailleurs, il est interprété en tant qu'identificateur.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="0fbb5-128">Au sein de la méthode `Async` ou de l’expression lambda, une expression `Await` ne peut pas se produire dans une expression de requête, dans le bloc `Catch` ou `Finally` d’une méthode [try... Catch... Finally](../statements/try-catch-finally-statement.md), dans l’expression de variable de contrôle de boucle d’une boucle `For` ou `For Each`, ou dans le corps d’une instruction [SyncLock](../statements/synclock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="0fbb5-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="0fbb5-129">Exceptions</span><span class="sxs-lookup"><span data-stu-id="0fbb5-129">Exceptions</span></span>

<span data-ttu-id="0fbb5-130">La plupart des méthodes async retournent un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0fbb5-131">Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="0fbb5-132">L'opérateur `Await` accède à ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="0fbb5-133">Si vous attendez une méthode async retournant des tâches qui lève une exception, l'opérateur `Await` lève de nouveau l'exception.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="0fbb5-134">Si vous attendez une méthode Async retournant des tâches qui est annulée, l’opérateur `Await` lève à nouveau une <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="0fbb5-135">Une tâche qui se trouve dans un état d’erreur peut refléter plusieurs exceptions.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="0fbb5-136">Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0fbb5-137">Quand vous attendez une telle tâche, l’opération await lève à nouveau une seule des exceptions.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="0fbb5-138">Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="0fbb5-139">Pour obtenir des exemples de gestion des erreurs dans les méthodes Async, consultez [try... Catch... Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0fbb5-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="0fbb5-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fbb5-140">Example</span></span>

<span data-ttu-id="0fbb5-141">L'exemple Windows Forms suivant illustre l'utilisation de `Await` dans une méthode async, `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="0fbb5-142">Comparez le comportement de cette méthode avec celui de `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="0fbb5-143">Sans opérateur `Await`, `WaitSynchronously` s’exécute de façon synchrone en dépit de l’utilisation du modificateur `Async` dans sa définition et d’un appel à <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> dans son corps.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="0fbb5-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fbb5-144">See also</span></span>

- [<span data-ttu-id="0fbb5-145">Programmation asynchrone avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="0fbb5-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="0fbb5-146">Procédure pas à pas : accès au web avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="0fbb5-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="0fbb5-147">Async</span><span class="sxs-lookup"><span data-stu-id="0fbb5-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
