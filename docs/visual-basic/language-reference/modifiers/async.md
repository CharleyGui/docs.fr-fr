---
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 35df7a464937647c6d110142a3e2801cebbea505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373152"
---
# <a name="async-visual-basic"></a><span data-ttu-id="b6318-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6318-102">Async (Visual Basic)</span></span>

<span data-ttu-id="b6318-103">Le `Async` modificateur indique que la méthode ou l' [expression lambda](../../programming-guide/language-features/procedures/lambda-expressions.md) qu’il modifie est asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b6318-103">The `Async` modifier indicates that the method or [lambda expression](../../programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="b6318-104">Ces méthodes sont appelées *méthodes Async*.</span><span class="sxs-lookup"><span data-stu-id="b6318-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="b6318-105">Une méthode async offre un moyen pratique d'exécuter un travail potentiellement long sans bloquer le thread de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b6318-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="b6318-106">L’appelant d’une méthode Async peut reprendre son travail sans attendre la fin de la méthode Async.</span><span class="sxs-lookup"><span data-stu-id="b6318-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="b6318-107">Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="b6318-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="b6318-108">Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="b6318-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="b6318-109">L’exemple suivant illustre la structure d’une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="b6318-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="b6318-110">Par Convention, les noms de méthodes Async se terminent par « Async ».</span><span class="sxs-lookup"><span data-stu-id="b6318-110">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="b6318-111">En règle générale, une méthode modifiée par le `Async` mot clé contient au moins une expression ou une instruction [await](async.md) .</span><span class="sxs-lookup"><span data-stu-id="b6318-111">Typically, a method modified by the `Async` keyword contains at least one [Await](async.md) expression or statement.</span></span> <span data-ttu-id="b6318-112">La méthode s’exécute de façon synchrone jusqu’à ce qu’elle atteigne le premier `Await` , point où elle s’interrompt jusqu’à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="b6318-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="b6318-113">Dans le même temps, le contrôle est retourné à l’appelant de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b6318-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="b6318-114">Si la méthode ne contient pas une `Await` expression ou une instruction, la méthode n’est pas suspendue et s’exécute en tant que méthode synchrone.</span><span class="sxs-lookup"><span data-stu-id="b6318-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="b6318-115">Un avertissement du compilateur vous signale toutes les méthodes Async qui ne contiennent pas `Await` , car cette situation peut indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="b6318-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="b6318-116">Pour plus d’informations, consultez l' [Erreur du compilateur](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="b6318-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="b6318-117">Le `Async` mot clé est un mot clé non réservé.</span><span class="sxs-lookup"><span data-stu-id="b6318-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="b6318-118">Il s’agit d’un mot clé lorsqu’il modifie une méthode ou une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="b6318-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="b6318-119">Dans tous les autres contextes, il est interprété comme un identificateur.</span><span class="sxs-lookup"><span data-stu-id="b6318-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="b6318-120">Types de retour</span><span class="sxs-lookup"><span data-stu-id="b6318-120">Return Types</span></span>

<span data-ttu-id="b6318-121">Une méthode Async est soit une [sous](../../programming-guide/language-features/procedures/sub-procedures.md) -procédure, soit une procédure de [fonction](../../programming-guide/language-features/procedures/function-procedures.md) qui a un type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="b6318-121">An async method is either a [Sub](../../programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b6318-122">La méthode ne peut pas déclarer de paramètres [ByRef](byref.md) .</span><span class="sxs-lookup"><span data-stu-id="b6318-122">The method cannot declare any [ByRef](byref.md) parameters.</span></span>

<span data-ttu-id="b6318-123">Vous spécifiez `Task(Of TResult)` pour le type de retour d’une méthode Async si l’instruction [Return](../statements/return-statement.md) de la méthode a un opérande de type TResult.</span><span class="sxs-lookup"><span data-stu-id="b6318-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="b6318-124">Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.</span><span class="sxs-lookup"><span data-stu-id="b6318-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="b6318-125">Autrement dit, un appel à la méthode retourne `Task` , mais lorsque la `Task` est terminée, toute `Await` instruction qui attend le `Task` ne produit pas de valeur de résultat.</span><span class="sxs-lookup"><span data-stu-id="b6318-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="b6318-126">Les sous-routines Async sont principalement utilisées pour définir des gestionnaires d’événements dans lesquels une `Sub` procédure est requise.</span><span class="sxs-lookup"><span data-stu-id="b6318-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="b6318-127">L’appelant d’une sous-routine Async ne peut pas l’attendre et ne peut pas intercepter les exceptions levées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="b6318-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="b6318-128">Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6318-128">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6318-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6318-129">Example</span></span>

<span data-ttu-id="b6318-130">Les exemples suivants illustrent un gestionnaire d’événements asynchrones, une expression lambda Async et une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="b6318-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="b6318-131">Pour obtenir un exemple complet qui utilise ces éléments, consultez [procédure pas à pas : accès au Web avec Async et await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b6318-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="b6318-132">Vous pouvez télécharger le code de procédure à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="b6318-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="b6318-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6318-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="b6318-134">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="b6318-134">Await Operator</span></span>](../operators/await-operator.md)
- [<span data-ttu-id="b6318-135">Programmation asynchrone avec Async et await</span><span class="sxs-lookup"><span data-stu-id="b6318-135">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="b6318-136">Procédure pas à pas : accès au Web avec Async et await</span><span class="sxs-lookup"><span data-stu-id="b6318-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
