---
title: Démarrer plusieurs tâches Asynch et les traiter une fois terminées
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b14171196a95e9a6a12f6b13f6f17d3cfe352bce
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266844"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="2dc5f-102">Démarrer plusieurs tâches Asynch et les traiter une fois terminées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dc5f-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="2dc5f-103">En utilisant <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une, une fois qu’elles sont terminées, au lieu de les traiter dans l’ordre dans lequel elles ont démarré.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="2dc5f-104">L’exemple suivant utilise une requête pour créer une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="2dc5f-105">Chaque tâche télécharge le contenu d’un site web spécifié.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="2dc5f-106">À chaque itération d’une boucle while, un appel attendu à `WhenAny` retourne la tâche de la collection de tâches dont le téléchargement se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="2dc5f-107">Cette tâche est supprimée de la collection et traitée.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="2dc5f-108">La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2dc5f-109">Pour exécuter les exemples, Visual Studio 2012 ou version ultérieure et .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="2dc5f-110">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="2dc5f-110">Downloading the Example</span></span>  
 <span data-ttu-id="2dc5f-111">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="2dc5f-112">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="2dc5f-113">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="2dc5f-114">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="2dc5f-115">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le projet **ProcessTasksAsTheyFinish**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="2dc5f-116">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="2dc5f-117">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="2dc5f-118">Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="2dc5f-119">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="2dc5f-120">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="2dc5f-120">Building the Example</span></span>  
 <span data-ttu-id="2dc5f-121">Cet exemple s’ajoute au code développé dans [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) et utilise la même interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="2dc5f-122">Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelAfterOneTask** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="2dc5f-123">Ajoutez les modifications de cette rubrique à la méthode `AccessTheWebAsync` dans ce projet.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="2dc5f-124">Les modifications sont marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="2dc5f-125">Le projet **CancelAfterOneTask** inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="2dc5f-126">Chaque appel à `ProcessURLAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="2dc5f-127">Dans le fichier MainWindow.xaml.vb du projet, apporter `AccessTheWebAsync` les modifications suivantes à la méthode.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-127">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="2dc5f-128">Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> au lieu de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="2dc5f-129">Ajoutez une boucle while qui effectue les étapes suivantes pour chaque tâche dans la collection.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="2dc5f-130">Elle attend un appel à `WhenAny` pour identifier la première tâche dans la collection afin de terminer son téléchargement.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="2dc5f-131">Elle supprime cette tâche de la collection.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-131">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. <span data-ttu-id="2dc5f-132">Elle attend `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="2dc5f-133">La variable `firstFinishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TReturn` est un entier.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="2dc5f-134">La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="2dc5f-135">Vous devez exécuter le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2dc5f-136">Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="2dc5f-137">Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="2dc5f-138">Pour plus d’informations et d’exemples, consultez l’article relatif au [traitement des tâches une fois terminées](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="2dc5f-138">For more information and examples, see [Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="2dc5f-139">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="2dc5f-139">Complete Example</span></span>  
 <span data-ttu-id="2dc5f-140">Le code suivant est le texte complet du fichier MainWindow.xaml.vb de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-140">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="2dc5f-141">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="2dc5f-142">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="2dc5f-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="2dc5f-143">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="2dc5f-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dc5f-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dc5f-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="2dc5f-145">Ajuster une application Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dc5f-145">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="2dc5f-146">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dc5f-146">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="2dc5f-147">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="2dc5f-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
