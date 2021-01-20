---
title: Annuler les tâches Asynch restantes quand l’une d’elles est terminée
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: a0a04c62378ddf70ab3dee9a522e490b0a73b83e
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615956"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="33216-102">Annuler les tâches Asynch restantes lorsque l’une d’elles est terminée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33216-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="33216-103">Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> avec un <xref:System.Threading.CancellationToken> pour annuler toutes les tâches restantes quand une tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="33216-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="33216-104">La méthode `WhenAny` accepte un argument qui est une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="33216-105">La méthode démarre toutes les tâches et retourne une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="33216-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="33216-106">Cette dernière est terminée une fois que toutes les tâches de la collection sont terminées.</span><span class="sxs-lookup"><span data-stu-id="33216-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="33216-107">Cet exemple montre comment utiliser un jeton d’annulation avec `WhenAny` pour attendre la fin de la première tâche de la collection et annuler les tâches restantes.</span><span class="sxs-lookup"><span data-stu-id="33216-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="33216-108">Chaque tâche télécharge le contenu d’un site web.</span><span class="sxs-lookup"><span data-stu-id="33216-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="33216-109">L’exemple affiche la longueur du contenu du premier téléchargement terminé et annule les autres téléchargements.</span><span class="sxs-lookup"><span data-stu-id="33216-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="33216-110">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="33216-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="33216-111">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="33216-111">Downloading the Example</span></span>

<span data-ttu-id="33216-112">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="33216-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="33216-113">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="33216-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="33216-114">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="33216-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="33216-115">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="33216-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="33216-116">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterOneTask**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="33216-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="33216-117">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="33216-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="33216-118">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="33216-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="33216-119">Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.</span><span class="sxs-lookup"><span data-stu-id="33216-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="33216-120">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="33216-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="33216-121">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="33216-121">Building the Example</span></span>

<span data-ttu-id="33216-122">L’exemple de cette rubrique ajoute au projet développé dans [annuler une tâche asynchrone ou une liste de tâches](cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="33216-123">Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.</span><span class="sxs-lookup"><span data-stu-id="33216-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="33216-124">Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="33216-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="33216-125">Ajoutez les changements de cette rubrique à ce projet.</span><span class="sxs-lookup"><span data-stu-id="33216-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="33216-126">Dans le fichier MainWindow. Xaml. vb du projet **CancelAListOfTasks** , commencez la transition en déplaçant les étapes de traitement de chaque site Web de la boucle dans `AccessTheWebAsync` vers la méthode Async suivante.</span><span class="sxs-lookup"><span data-stu-id="33216-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

```vb
' **_Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

<span data-ttu-id="33216-127">Dans `AccessTheWebAsync`, cet exemple utilise une requête, la méthode <xref:System.Linq.Enumerable.ToArray%2A> et la méthode `WhenAny` pour créer et démarrer un tableau de tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="33216-128">L’application de `WhenAny` au tableau retourne une tâche unique qui, quand elle est attendue, prend la valeur de la première tâche terminée dans le tableau de tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="33216-129">Dans `AccessTheWebAsync`, effectuez les changements suivants.</span><span class="sxs-lookup"><span data-stu-id="33216-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="33216-130">Les astérisques signalent les changements dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="33216-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="33216-131">Commentez ou supprimez la boucle.</span><span class="sxs-lookup"><span data-stu-id="33216-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="33216-132">Créer une requête qui, une fois exécutée, génère une collection de tâches génériques.</span><span class="sxs-lookup"><span data-stu-id="33216-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="33216-133">Chaque appel à `ProcessURLAsync` retourne un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="33216-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' _*_Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="33216-134">Appelez `ToArray` pour exécuter la requête et démarrer les tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="33216-135">L’application de la méthode `WhenAny` à l’étape suivante exécute la requête et démarre les tâches sans utiliser `ToArray`, mais il se peut que d’autres méthodes n’y parviennent pas.</span><span class="sxs-lookup"><span data-stu-id="33216-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="33216-136">L’approche la plus sûre consiste à forcer l’exécution de la requête de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="33216-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' _*_Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="33216-137">Appelez `WhenAny` sur la collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="33216-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="33216-138">`WhenAny` retourne `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="33216-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="33216-139">Autrement dit, `WhenAny` retourne une tâche qui prend la valeur d’un `Task(Of Integer)` ou `Task<int>` unique quand elle est attendue.</span><span class="sxs-lookup"><span data-stu-id="33216-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="33216-140">Cette tâche unique est la première tâche de la collection à se terminer.</span><span class="sxs-lookup"><span data-stu-id="33216-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="33216-141">La tâche terminée en premier est assignée à `finishedTask`.</span><span class="sxs-lookup"><span data-stu-id="33216-141">The task that finished first is assigned to `finishedTask`.</span></span> <span data-ttu-id="33216-142">Le type de `finishedTask` est <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier car il s’agit du type de retour de `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="33216-142">The type of `finishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' _*_Call WhenAny and then await the result. The task that finishes
    ' first is assigned to finishedTask.
    Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="33216-143">Dans cet exemple, vous vous intéressez uniquement à la tâche qui se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="33216-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="33216-144">Par conséquent, utilisez <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour annuler les tâches restantes.</span><span class="sxs-lookup"><span data-stu-id="33216-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' _*_Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="33216-145">Enfin, attendez `finishedTask` pour récupérer la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="33216-145">Finally, await `finishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await finishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="33216-146">Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.</span><span class="sxs-lookup"><span data-stu-id="33216-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="33216-147">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="33216-147">Complete Example</span></span>

<span data-ttu-id="33216-148">Le code suivant est le fichier MainWindow. Xaml. vb ou MainWindow.xaml.cs complet pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="33216-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="33216-149">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="33216-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="33216-150">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="33216-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="33216-151">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="33216-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' _*_Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' _*_Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' _*_Call WhenAny and then await the result. The task that finishes
        ' first is assigned to finishedTask.
        Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' _*_Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' _*_Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await finishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' _**Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a><span data-ttu-id="33216-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33216-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="33216-153">Ajuster une application Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33216-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="33216-154">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33216-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="33216-155">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="33216-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
