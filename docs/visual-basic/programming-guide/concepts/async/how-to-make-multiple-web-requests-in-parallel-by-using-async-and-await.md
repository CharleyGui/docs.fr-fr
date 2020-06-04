---
title: 'Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 40bab392af94ba941c2562e885a8d2e08aeea5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396582"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="d4c94-102">Guide pratique : effectuer plusieurs requêtes web en parallèle avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c94-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="d4c94-103">Dans une méthode asynchrone, les tâches sont démarrées quand elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="d4c94-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="d4c94-104">L’opérateur [await](../../../language-reference/operators/await-operator.md) est appliqué à la tâche au point de la méthode où le traitement ne peut pas se poursuivre tant que la tâche n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="d4c94-104">The [Await](../../../language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="d4c94-105">Souvent, une tâche est attendue dès sa création, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d4c94-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="d4c94-106">Toutefois, vous pouvez séparer la création de la tâche de son attente si votre programme doit accomplir d’autres tâches qui ne dépendent pas de l’achèvement de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d4c94-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

<span data-ttu-id="d4c94-107">Entre le démarrage d’une tâche et le moment où elle est attendue, vous pouvez démarrer d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="d4c94-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="d4c94-108">Les tâches supplémentaires s’exécutent implicitement en parallèle, mais aucun thread supplémentaire n’est créé.</span><span class="sxs-lookup"><span data-stu-id="d4c94-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="d4c94-109">Le programme suivant démarre trois téléchargements web asynchrones, puis les attend dans l’ordre dans lequel ils sont appelés.</span><span class="sxs-lookup"><span data-stu-id="d4c94-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="d4c94-110">Notez que quand vous exécutez le programme, les tâches ne se terminent pas toujours dans l’ordre dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="d4c94-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="d4c94-111">Elles commencent à s’exécuter quand elles sont créées, et une ou plusieurs d’entre elles peuvent se terminer avant que la méthode n’atteigne les expressions await.</span><span class="sxs-lookup"><span data-stu-id="d4c94-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="d4c94-112">Pour mener à bien ce projet, Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d4c94-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="d4c94-113">Pour obtenir un autre exemple qui démarre plusieurs tâches en même temps, consultez [Comment : étendre la procédure pas à pas Async à l’aide de Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d4c94-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="d4c94-114">Vous pouvez télécharger le code de cet exemple à partir des [exemples de code pour développeur](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="d4c94-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="d4c94-115">Pour configurer le projet</span><span class="sxs-lookup"><span data-stu-id="d4c94-115">To set up the project</span></span>

1. <span data-ttu-id="d4c94-116">Pour configurer une application WPF, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="d4c94-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="d4c94-117">Vous trouverez des instructions détaillées pour ces étapes dans [procédure pas à pas : accès au Web à l’aide de Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d4c94-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="d4c94-118">Créez une application WPF qui contient une zone de texte et un bouton.</span><span class="sxs-lookup"><span data-stu-id="d4c94-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="d4c94-119">Nommez le bouton `startButton` et la zone de texte `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="d4c94-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="d4c94-120">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="d4c94-120">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="d4c94-121">Dans le fichier MainWindow. Xaml. vb, ajoutez une `Imports` instruction pour `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="d4c94-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="d4c94-122">Pour ajouter le code</span><span class="sxs-lookup"><span data-stu-id="d4c94-122">To add the code</span></span>

1. <span data-ttu-id="d4c94-123">Dans la fenêtre de conception, MainWindow. xaml, double-cliquez sur le bouton pour créer le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="d4c94-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="d4c94-124">Copiez le code suivant et collez-le dans le corps de `startButton_Click` dans MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="d4c94-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="d4c94-125">Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, qui pilote l’application.</span><span class="sxs-lookup"><span data-stu-id="d4c94-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="d4c94-126">Ajoutez les méthodes de prise en charge suivantes au projet :</span><span class="sxs-lookup"><span data-stu-id="d4c94-126">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="d4c94-127">`ProcessURLAsync` utilise une méthode <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web sous la forme d’un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="d4c94-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="d4c94-128">La méthode de prise en charge, `ProcessURLAsync`, affiche et retourne ensuite la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="d4c94-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="d4c94-129">`DisplayResults` affiche le nombre d’octets dans le tableau d’octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="d4c94-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="d4c94-130">Cet affichage indique quand le téléchargement de chaque tâche est terminé.</span><span class="sxs-lookup"><span data-stu-id="d4c94-130">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="d4c94-131">Copiez les méthodes suivantes, puis collez-les après le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="d4c94-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. <span data-ttu-id="d4c94-132">Pour finir, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="d4c94-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="d4c94-133">La méthode déclare un objet `HttpClient`, dont vous avez besoin pour accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dans `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="d4c94-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="d4c94-134">La méthode crée et démarre trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="d4c94-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="d4c94-135">À mesure que chaque tâche se termine, `DisplayResults` affiche son URL et la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="d4c94-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="d4c94-136">Les tâches s’exécutant de façon asynchrone, l’ordre d’affichage des résultats peut différer de celui dans lequel les tâches ont été déclarées.</span><span class="sxs-lookup"><span data-stu-id="d4c94-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="d4c94-137">La méthode attend l’achèvement de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="d4c94-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="d4c94-138">Chaque opérateur `Await` suspend l’exécution de `CreateMultipleTasksAsync` jusqu’à la fin de la tâche attendue.</span><span class="sxs-lookup"><span data-stu-id="d4c94-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="d4c94-139">L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.</span><span class="sxs-lookup"><span data-stu-id="d4c94-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="d4c94-140">Une fois les tâches terminées et les valeurs entières récupérées, la méthode additionne les longueurs des sites web et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="d4c94-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="d4c94-141">Copiez la méthode suivante et collez-la dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="d4c94-141">Copy the following method, and paste it into your solution.</span></span>

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. <span data-ttu-id="d4c94-142">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d4c94-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="d4c94-143">Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminent pas toujours dans le même ordre, et que l’ordre dans lequel elles se terminent n’est pas nécessairement celui dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="d4c94-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="d4c94-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="d4c94-144">Example</span></span>

<span data-ttu-id="d4c94-145">Le code suivant contient l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="d4c94-145">The following code contains the full example.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="d4c94-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4c94-146">See also</span></span>

- [<span data-ttu-id="d4c94-147">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c94-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="d4c94-148">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c94-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d4c94-149">Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c94-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
