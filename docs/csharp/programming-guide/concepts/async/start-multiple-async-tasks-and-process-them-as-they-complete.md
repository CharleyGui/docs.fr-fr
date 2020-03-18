---
title: Traiter les tâches asynchrones terminées
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: b618fd6bf80551231d2b285fd0e8aef688d00d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71736729"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="e1462-102">Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)</span><span class="sxs-lookup"><span data-stu-id="e1462-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="e1462-103">En utilisant <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une, une fois qu’elles sont terminées, au lieu de les traiter dans l’ordre dans lequel elles ont démarré.</span><span class="sxs-lookup"><span data-stu-id="e1462-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="e1462-104">L’exemple suivant utilise une requête pour créer une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="e1462-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="e1462-105">Chaque tâche télécharge le contenu d’un site web spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1462-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="e1462-106">À chaque itération d’une boucle while, un appel attendu à `WhenAny` retourne la tâche de la collection de tâches dont le téléchargement se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="e1462-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="e1462-107">Cette tâche est supprimée de la collection et traitée.</span><span class="sxs-lookup"><span data-stu-id="e1462-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="e1462-108">La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.</span><span class="sxs-lookup"><span data-stu-id="e1462-108">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="e1462-109">Pour exécuter les exemples, Visual Studio 2012 ou version ultérieure et .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e1462-109">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="e1462-110">Télécharger un exemple de solution</span><span class="sxs-lookup"><span data-stu-id="e1462-110">Download an example solution</span></span>

<span data-ttu-id="e1462-111">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="e1462-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="e1462-112">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le *fichier MainWindow.xaml.cs* à la fin de ce sujet à la place.</span><span class="sxs-lookup"><span data-stu-id="e1462-112">If you don't want to download the project, you can review the *MainWindow.xaml.cs* file at the end of this topic instead.</span></span>

1. <span data-ttu-id="e1462-113">Extraire les fichiers que vous avez téléchargés à partir du fichier *.zip,* puis démarrer Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1462-113">Extract the files that you downloaded from the *.zip* file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e1462-114">Sur la barre de menu, choisissez **File** > **Open** > **Project/Solution**.</span><span class="sxs-lookup"><span data-stu-id="e1462-114">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e1462-115">Dans la boîte de dialogue **Open Project,** ouvrez le dossier qui contient le code de l’échantillon que vous avez téléchargé, puis ouvrez le fichier de solution (*.sln)* pour *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span><span class="sxs-lookup"><span data-stu-id="e1462-115">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (*.sln*) file for *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span></span>

4. <span data-ttu-id="e1462-116">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le projet **ProcessTasksAsTheyFinish**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="e1462-116">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e1462-117">Choisissez la clé <kbd>F5</kbd> pour exécuter le programme avec débogage ou, appuyez sur les clés <kbd>Ctrl</kbd>+<kbd>F5</kbd> pour exécuter le programme sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="e1462-117">Choose the <kbd>F5</kbd> key to run the program with debugging or, press <kbd>Ctrl</kbd>+<kbd>F5</kbd> keys to run the program without debugging it.</span></span>

6. <span data-ttu-id="e1462-118">Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="e1462-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="e1462-119">Créer le programme vous-même</span><span class="sxs-lookup"><span data-stu-id="e1462-119">Create the program yourself</span></span>

<span data-ttu-id="e1462-120">Cet exemple ajoute le code développé dans [Annuler les tâches Async restantes lorsque l’une d’elles est terminée (C#)](cancel-remaining-async-tasks-after-one-is-complete.md) et utilise la même interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1462-120">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="e1462-121">Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section [Téléchargement de l’exemple](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example), mais choisissez **CancelAfterOneTask** comme projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="e1462-121">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="e1462-122">Ajoutez les modifications de cette rubrique à la méthode `AccessTheWebAsync` dans ce projet.</span><span class="sxs-lookup"><span data-stu-id="e1462-122">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="e1462-123">Les modifications sont marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="e1462-123">The changes are marked with asterisks.</span></span>

<span data-ttu-id="e1462-124">Le projet **CancelAfterOneTask** inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="e1462-124">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="e1462-125">Chaque appel à `ProcessURLAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier :</span><span class="sxs-lookup"><span data-stu-id="e1462-125">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="e1462-126">Dans le *dossier MainWindow.xaml.cs* du projet, apporter les `AccessTheWebAsync` modifications suivantes à la méthode :</span><span class="sxs-lookup"><span data-stu-id="e1462-126">In the *MainWindow.xaml.cs* file of the project, make the following changes to the `AccessTheWebAsync` method:</span></span>

- <span data-ttu-id="e1462-127">Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> au lieu de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1462-127">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- <span data-ttu-id="e1462-128">Ajoutez une boucle `while` qui effectue les étapes suivantes pour chaque tâche dans la collection :</span><span class="sxs-lookup"><span data-stu-id="e1462-128">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1. <span data-ttu-id="e1462-129">Elle attend un appel à `WhenAny` pour identifier la première tâche dans la collection afin de terminer son téléchargement.</span><span class="sxs-lookup"><span data-stu-id="e1462-129">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. <span data-ttu-id="e1462-130">Elle supprime cette tâche de la collection.</span><span class="sxs-lookup"><span data-stu-id="e1462-130">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. <span data-ttu-id="e1462-131">Elle attend `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="e1462-131">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="e1462-132">La variable `firstFinishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TReturn` est un entier.</span><span class="sxs-lookup"><span data-stu-id="e1462-132">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="e1462-133">La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e1462-133">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="e1462-134">Si la tâche est `await` reprochée, jettera la `AggregateException`première exception `Result` d’enfant `AggregateException`stockée dans le , contrairement à la lecture de la propriété qui jetterait le .</span><span class="sxs-lookup"><span data-stu-id="e1462-134">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the `Result` property which would throw the `AggregateException`.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="e1462-135">Exécutez le programme plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="e1462-135">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="e1462-136">Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches.</span><span class="sxs-lookup"><span data-stu-id="e1462-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="e1462-137">Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter.</span><span class="sxs-lookup"><span data-stu-id="e1462-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="e1462-138">Pour plus d’informations et d’exemples, voir [les tâches de traitement comme elles complètent](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="e1462-138">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="e1462-139">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="e1462-139">Complete example</span></span>

<span data-ttu-id="e1462-140">Le code suivant est le texte complet du *fichier MainWindow.xaml.cs* pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="e1462-140">The following code is the complete text of the *MainWindow.xaml.cs* file for the example.</span></span> <span data-ttu-id="e1462-141">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="e1462-141">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="e1462-142">Notez aussi que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e1462-142">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="e1462-143">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e1462-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace ProcessTasksAsTheyFinish
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
            resultsTextBox.Clear();

            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            try
            {
                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Create a query that, when executed, returns a collection of tasks.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURL(url, client, ct);

            // ***Use ToList to execute the query and start the tasks.
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

            // ***Add a loop to process the tasks one at a time until none remain.
            while (downloadTasks.Count > 0)
            {
                    // Identify the first task that completes.
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);

                    // ***Remove the selected task from the list so that you don't
                    // process it more than once.
                    downloadTasks.Remove(firstFinishedTask);

                    // Await the completed task.
                    int length = await firstFinishedTask;
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)
        {
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            return urlContents.Length;
        }
    }
}

// Sample Output:

// Length of the download:  226093
// Length of the download:  412588
// Length of the download:  175490
// Length of the download:  204890
// Length of the download:  158855
// Length of the download:  145790
// Length of the download:  44908
// Downloads complete.
```

## <a name="see-also"></a><span data-ttu-id="e1462-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1462-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="e1462-145">Réglage de votre application asynchrone (C#)</span><span class="sxs-lookup"><span data-stu-id="e1462-145">Fine-Tuning Your Async Application (C#)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="e1462-146">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="e1462-146">Asynchronous Programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="e1462-147">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="e1462-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
