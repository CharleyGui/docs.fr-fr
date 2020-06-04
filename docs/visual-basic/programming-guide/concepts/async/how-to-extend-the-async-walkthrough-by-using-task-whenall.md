---
title: "Comment : étendre la procédure pas à pas Async à l'aide de Task.WhenAll"
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fb323852c83b1edf51396a0b800c2d54a833d0c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396621"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="bc068-102">Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc068-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>

<span data-ttu-id="bc068-103">Vous pouvez améliorer les performances de la solution Async dans [procédure pas à pas : accès au Web avec Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) à l’aide de la <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="bc068-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bc068-104">Cette méthode attend de manière asynchrone plusieurs opérations, qui sont représentées sous la forme d’une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="bc068-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="bc068-105">Vous aurez peut-être remarqué dans la procédure pas à pas que les sites web se téléchargent à différentes vitesses.</span><span class="sxs-lookup"><span data-stu-id="bc068-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="bc068-106">L’un des sites web est parfois très lent, ce qui retarde tous les autres téléchargements.</span><span class="sxs-lookup"><span data-stu-id="bc068-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="bc068-107">Quand vous exécutez les solutions asynchrones que vous générez dans la procédure pas à pas, vous pouvez quitter le programme facilement si vous ne souhaitez pas attendre, mais une meilleure option consiste à démarrer tous les téléchargements en même temps et à laisser les plus rapides se poursuivre sans attendre celui qui est retardé.</span><span class="sxs-lookup"><span data-stu-id="bc068-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="bc068-108">Vous appliquez la méthode `Task.WhenAll` à une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="bc068-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="bc068-109">L’application de `WhenAll` retourne une tâche unique qui n’est pas terminée tant que toutes les tâches de la collection ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="bc068-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="bc068-110">Les tâches s’exécutent en parallèle, mais aucun thread supplémentaire n’est créé.</span><span class="sxs-lookup"><span data-stu-id="bc068-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="bc068-111">Les tâches peuvent se terminer dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="bc068-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc068-112">Les procédures suivantes décrivent les extensions des applications Async développées dans [procédure pas à pas : accès au Web à l’aide de Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="bc068-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="bc068-113">Vous pouvez développer les applications soit en appliquant la procédure pas à pas, soit en téléchargeant le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="bc068-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="bc068-114">Pour exécuter l’exemple, Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bc068-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="bc068-115">Pour ajouter Task.WhenAll à votre solution GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="bc068-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="bc068-116">Ajoutez la `ProcessURLAsync` méthode à la première application développée dans [procédure pas à pas : accès au Web à l’aide de Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="bc068-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="bc068-117">Si vous avez téléchargé le code à partir des [exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough, puis ajoutez- `ProcessURLAsync` le au fichier MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="bc068-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="bc068-118">Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui inclut la méthode `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="bc068-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="bc068-119">Le fichier MainWindow. Xaml. vb pour cette application est le premier exemple de la section « Exemples de code complets de la procédure pas à pas ».</span><span class="sxs-lookup"><span data-stu-id="bc068-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="bc068-120">La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `For Each` dans `SumPageSizesAsync` dans la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="bc068-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="bc068-121">La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="bc068-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="bc068-122">Commentez ou supprimez la boucle `For Each` dans `SumPageSizesAsync`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="bc068-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="bc068-123">Créez une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="bc068-123">Create a collection of tasks.</span></span> <span data-ttu-id="bc068-124">Le code suivant définit une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web.</span><span class="sxs-lookup"><span data-stu-id="bc068-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="bc068-125">Les tâches sont démarrées quand la requête est évaluée.</span><span class="sxs-lookup"><span data-stu-id="bc068-125">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="bc068-126">Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `urlList`.</span><span class="sxs-lookup"><span data-stu-id="bc068-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="bc068-127">Appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="bc068-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="bc068-128">`Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.</span><span class="sxs-lookup"><span data-stu-id="bc068-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="bc068-129">Dans l’exemple suivant, l’expression `Await` attend l’achèvement de la tâche unique retournée par `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="bc068-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="bc068-130">L’expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé.</span><span class="sxs-lookup"><span data-stu-id="bc068-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="bc068-131">Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="bc068-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="bc068-132">Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des longueurs de tous les sites web.</span><span class="sxs-lookup"><span data-stu-id="bc068-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="bc068-133">Ajoutez la ligne suivante à `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="bc068-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="bc068-134">Pour ajouter Task.WhenAll à la solution HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="bc068-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="bc068-135">Ajoutez la version suivante de `ProcessURLAsync` à la deuxième application développée dans [procédure pas à pas : accès au Web à l’aide de Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="bc068-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="bc068-136">Si vous avez téléchargé le code à partir des [exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough_HttpClient, puis ajoutez- `ProcessURLAsync` le au fichier MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="bc068-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="bc068-137">Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui utilise la méthode `HttpClient.GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="bc068-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="bc068-138">Le fichier MainWindow. Xaml. vb pour cette application est le deuxième exemple de la section « Exemples de code complets de la procédure pas à pas ».</span><span class="sxs-lookup"><span data-stu-id="bc068-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="bc068-139">La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `For Each` dans `SumPageSizesAsync` dans la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="bc068-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="bc068-140">La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="bc068-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

     <span data-ttu-id="bc068-141">La seule différence par rapport à la méthode `ProcessURLAsync` de la procédure précédente est l’utilisation de l’instance <xref:System.Net.Http.HttpClient>, `client`.</span><span class="sxs-lookup"><span data-stu-id="bc068-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="bc068-142">Commentez ou supprimez la boucle `For Each` dans `SumPageSizesAsync`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="bc068-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="bc068-143">Définissez une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web.</span><span class="sxs-lookup"><span data-stu-id="bc068-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="bc068-144">Les tâches sont démarrées quand la requête est évaluée.</span><span class="sxs-lookup"><span data-stu-id="bc068-144">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="bc068-145">Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `client` et `urlList`.</span><span class="sxs-lookup"><span data-stu-id="bc068-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="bc068-146">Ensuite, appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="bc068-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="bc068-147">`Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.</span><span class="sxs-lookup"><span data-stu-id="bc068-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="bc068-148">Dans l’exemple suivant, l’expression `Await` attend l’achèvement de la tâche unique retournée par `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="bc068-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="bc068-149">Une fois cette tâche achevée, l’expression `Await` correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé.</span><span class="sxs-lookup"><span data-stu-id="bc068-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="bc068-150">Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="bc068-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="bc068-151">Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir la somme des longueurs de tous les sites web.</span><span class="sxs-lookup"><span data-stu-id="bc068-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="bc068-152">Ajoutez la ligne suivante à `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="bc068-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="bc068-153">Pour tester les solutions Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="bc068-153">To test the Task.WhenAll solutions</span></span>

<span data-ttu-id="bc068-154">Pour l’une ou l’autre solution, appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="bc068-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="bc068-155">La sortie doit ressembler à la sortie des solutions Async dans [procédure pas à pas : accès au Web avec Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="bc068-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="bc068-156">Toutefois, notez que les sites web apparaissent à chaque fois dans un ordre différent.</span><span class="sxs-lookup"><span data-stu-id="bc068-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="bc068-157">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc068-157">Example</span></span>

<span data-ttu-id="bc068-158">Le code suivant montre les extensions du projet qui utilise la méthode `GetURLContentsAsync` pour télécharger du contenu à partir du web.</span><span class="sxs-lookup"><span data-stu-id="bc068-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

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

## <a name="example"></a><span data-ttu-id="bc068-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc068-159">Example</span></span>

<span data-ttu-id="bc068-160">Le code suivant montre les extensions du projet qui utilise la méthode `HttpClient.GetByteArrayAsync` pour télécharger du contenu à partir du web.</span><span class="sxs-lookup"><span data-stu-id="bc068-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
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

## <a name="see-also"></a><span data-ttu-id="bc068-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc068-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc068-162">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc068-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
