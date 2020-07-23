---
title: Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)
description: Utilisez la méthode Task. WhenAny avec un CancellationToken en C# pour annuler toutes les tâches restantes quand une tâche est terminée dans cet exemple.
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 6de60c8faa93752961e3703a042885a71972cc4a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925278"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="bdee9-103">Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)</span><span class="sxs-lookup"><span data-stu-id="bdee9-103">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="bdee9-104">Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> avec un <xref:System.Threading.CancellationToken> pour annuler toutes les tâches restantes quand une tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="bdee9-104">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="bdee9-105">La méthode `WhenAny` accepte un argument qui est une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-105">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="bdee9-106">La méthode démarre toutes les tâches et retourne une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="bdee9-106">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="bdee9-107">Cette dernière est terminée une fois que toutes les tâches de la collection sont terminées.</span><span class="sxs-lookup"><span data-stu-id="bdee9-107">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="bdee9-108">Cet exemple montre comment utiliser un jeton d’annulation avec `WhenAny` pour attendre la fin de la première tâche de la collection et annuler les tâches restantes.</span><span class="sxs-lookup"><span data-stu-id="bdee9-108">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="bdee9-109">Chaque tâche télécharge le contenu d’un site web.</span><span class="sxs-lookup"><span data-stu-id="bdee9-109">Each task downloads the contents of a website.</span></span> <span data-ttu-id="bdee9-110">L’exemple affiche la longueur du contenu du premier téléchargement terminé et annule les autres téléchargements.</span><span class="sxs-lookup"><span data-stu-id="bdee9-110">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdee9-111">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bdee9-111">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="bdee9-112">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="bdee9-112">Downloading the Example</span></span>  
 <span data-ttu-id="bdee9-113">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="bdee9-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="bdee9-114">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bdee9-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="bdee9-115">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="bdee9-115">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="bdee9-116">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="bdee9-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="bdee9-117">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterOneTask**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="bdee9-117">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="bdee9-118">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="bdee9-118">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="bdee9-119">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="bdee9-119">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="bdee9-120">Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.</span><span class="sxs-lookup"><span data-stu-id="bdee9-120">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="bdee9-121">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bdee9-121">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="bdee9-122">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="bdee9-122">Building the Example</span></span>  
 <span data-ttu-id="bdee9-123">L’exemple de cette rubrique s’appuie sur le projet développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-123">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="bdee9-124">Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.</span><span class="sxs-lookup"><span data-stu-id="bdee9-124">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="bdee9-125">Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="bdee9-125">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="bdee9-126">Ajoutez les changements de cette rubrique à ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdee9-126">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="bdee9-127">Dans le fichier MainWindow.xaml.vb du projet **CancelAListOfTasks**, commencez la transition en déplaçant les étapes de traitement de chaque site web de la boucle dans `AccessTheWebAsync` vers la méthode asynchrone suivante.</span><span class="sxs-lookup"><span data-stu-id="bdee9-127">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="bdee9-128">Dans `AccessTheWebAsync`, cet exemple utilise une requête, la méthode <xref:System.Linq.Enumerable.ToArray%2A> et la méthode `WhenAny` pour créer et démarrer un tableau de tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-128">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="bdee9-129">L’application de `WhenAny` au tableau retourne une tâche unique qui, quand elle est attendue, prend la valeur de la première tâche terminée dans le tableau de tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-129">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="bdee9-130">Dans `AccessTheWebAsync`, effectuez les changements suivants.</span><span class="sxs-lookup"><span data-stu-id="bdee9-130">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="bdee9-131">Les astérisques signalent les changements dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="bdee9-131">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="bdee9-132">Commentez ou supprimez la boucle.</span><span class="sxs-lookup"><span data-stu-id="bdee9-132">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="bdee9-133">Créer une requête qui, une fois exécutée, génère une collection de tâches génériques.</span><span class="sxs-lookup"><span data-stu-id="bdee9-133">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="bdee9-134">Chaque appel à `ProcessURLAsync` retourne un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="bdee9-134">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="bdee9-135">Appelez `ToArray` pour exécuter la requête et démarrer les tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="bdee9-136">L’application de la méthode `WhenAny` à l’étape suivante exécute la requête et démarre les tâches sans utiliser `ToArray`, mais il se peut que d’autres méthodes n’y parviennent pas.</span><span class="sxs-lookup"><span data-stu-id="bdee9-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="bdee9-137">L’approche la plus sûre consiste à forcer l’exécution de la requête de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="bdee9-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="bdee9-138">Appelez `WhenAny` sur la collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="bdee9-138">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="bdee9-139">`WhenAny` retourne `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="bdee9-139">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="bdee9-140">Autrement dit, `WhenAny` retourne une tâche qui prend la valeur d’un `Task(Of Integer)` ou `Task<int>` unique quand elle est attendue.</span><span class="sxs-lookup"><span data-stu-id="bdee9-140">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="bdee9-141">Cette tâche unique est la première tâche de la collection à se terminer.</span><span class="sxs-lookup"><span data-stu-id="bdee9-141">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="bdee9-142">La tâche terminée en premier est assignée à `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="bdee9-142">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="bdee9-143">Le type de `firstFinishedTask` est <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier car il s’agit du type de retour de `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="bdee9-143">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="bdee9-144">Dans cet exemple, vous vous intéressez uniquement à la tâche qui se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="bdee9-144">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="bdee9-145">Par conséquent, utilisez <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour annuler les tâches restantes.</span><span class="sxs-lookup"><span data-stu-id="bdee9-145">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="bdee9-146">Enfin, attendez `firstFinishedTask` pour récupérer la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="bdee9-146">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="bdee9-147">Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.</span><span class="sxs-lookup"><span data-stu-id="bdee9-147">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="bdee9-148">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="bdee9-148">Complete Example</span></span>  
 <span data-ttu-id="bdee9-149">Le code suivant est le fichier MainWindow.xaml.cs complet de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="bdee9-149">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="bdee9-150">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bdee9-150">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="bdee9-151">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="bdee9-151">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="bdee9-152">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="bdee9-152">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.
            //    // Argument ct carries the message if the Cancel button is chosen.
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdee9-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdee9-153">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="bdee9-154">Réglage de votre application asynchrone (C#)</span><span class="sxs-lookup"><span data-stu-id="bdee9-154">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="bdee9-155">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="bdee9-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="bdee9-156">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="bdee9-156">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
