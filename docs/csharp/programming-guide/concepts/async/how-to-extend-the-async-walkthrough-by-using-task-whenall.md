---
title: Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970035"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="a594d-102">Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)</span><span class="sxs-lookup"><span data-stu-id="a594d-102">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="a594d-103">Vous pouvez améliorer les performances de la solution async fournie dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) à l’aide de la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a594d-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a594d-104">Cette méthode attend de manière asynchrone plusieurs opérations, qui sont représentées sous la forme d’une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="a594d-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="a594d-105">Vous aurez peut-être remarqué dans la procédure pas à pas que les sites web se téléchargent à différentes vitesses.</span><span class="sxs-lookup"><span data-stu-id="a594d-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="a594d-106">L’un des sites web est parfois très lent, ce qui retarde tous les autres téléchargements.</span><span class="sxs-lookup"><span data-stu-id="a594d-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="a594d-107">Quand vous exécutez les solutions asynchrones que vous générez dans la procédure pas à pas, vous pouvez quitter le programme facilement si vous ne souhaitez pas attendre, mais une meilleure option consiste à démarrer tous les téléchargements en même temps et à laisser les plus rapides se poursuivre sans attendre celui qui est retardé.</span><span class="sxs-lookup"><span data-stu-id="a594d-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="a594d-108">Vous appliquez la méthode `Task.WhenAll` à une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="a594d-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="a594d-109">L’application de `WhenAll` retourne une tâche unique qui n’est pas terminée tant que toutes les tâches de la collection ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="a594d-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="a594d-110">Les tâches s’exécutent en parallèle, mais aucun thread supplémentaire n’est créé.</span><span class="sxs-lookup"><span data-stu-id="a594d-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="a594d-111">Les tâches peuvent se terminer dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="a594d-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a594d-112">Les procédures suivantes décrivent des extensions pour les applications asynchrones qui sont développées dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a594d-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="a594d-113">Vous pouvez développer les applications soit en appliquant la procédure pas à pas, soit en téléchargeant le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="a594d-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="a594d-114">Pour exécuter l’exemple, Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a594d-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="a594d-115">Pour ajouter Task.WhenAll à votre solution GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="a594d-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="a594d-116">Ajoutez la méthode `ProcessURLAsync` à la première application développée dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a594d-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="a594d-117">Si vous avez téléchargé le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a594d-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="a594d-118">Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui inclut la méthode `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="a594d-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="a594d-119">Le fichier MainWindow.xaml.cs pour cette application est le premier exemple dans la section « Exemples de code complets de la procédure pas à pas ».</span><span class="sxs-lookup"><span data-stu-id="a594d-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="a594d-120">La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `foreach` dans `SumPageSizesAsync` dans la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="a594d-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="a594d-121">La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="a594d-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="a594d-122">Commentez ou supprimez la boucle `foreach` dans `SumPageSizesAsync`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a594d-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    byte[] urlContents = await GetURLContentsAsync(url);

    //    // The previous line abbreviates the following two assignment statements.
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //    //byte[] urlContents = await getContentsTask;

    //    DisplayResults(url, urlContents);

    //    // Update the total.
    //    total += urlContents.Length;
    //}
    ```

3. <span data-ttu-id="a594d-123">Créez une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="a594d-123">Create a collection of tasks.</span></span> <span data-ttu-id="a594d-124">Le code suivant définit une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web.</span><span class="sxs-lookup"><span data-stu-id="a594d-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="a594d-125">Les tâches sont démarrées quand la requête est évaluée.</span><span class="sxs-lookup"><span data-stu-id="a594d-125">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="a594d-126">Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `urlList`.</span><span class="sxs-lookup"><span data-stu-id="a594d-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="a594d-127">Appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="a594d-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="a594d-128">`Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.</span><span class="sxs-lookup"><span data-stu-id="a594d-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="a594d-129">Dans l’exemple suivant, l’expression `await` attend l’achèvement de la tâche unique retournée par `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="a594d-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="a594d-130">L’expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé.</span><span class="sxs-lookup"><span data-stu-id="a594d-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="a594d-131">Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="a594d-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="a594d-132">Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des longueurs de tous les sites web.</span><span class="sxs-lookup"><span data-stu-id="a594d-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="a594d-133">Ajoutez la ligne suivante à `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a594d-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="a594d-134">Pour ajouter Task.WhenAll à la solution HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="a594d-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="a594d-135">Ajoutez la version suivante de `ProcessURLAsync` à la deuxième application développée dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a594d-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="a594d-136">Si vous avez téléchargé le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough_HttpClient, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a594d-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="a594d-137">Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui utilise la méthode `HttpClient.GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="a594d-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="a594d-138">Le fichier MainWindow.xaml.cs pour cette application est le deuxième exemple dans la section « Exemples de code complets de la procédure pas à pas ».</span><span class="sxs-lookup"><span data-stu-id="a594d-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="a594d-139">La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `foreach` dans `SumPageSizesAsync` dans la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="a594d-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="a594d-140">La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="a594d-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="a594d-141">La seule différence par rapport à la méthode `ProcessURLAsync` de la procédure précédente est l’utilisation de l’instance <xref:System.Net.Http.HttpClient>, `client`.</span><span class="sxs-lookup"><span data-stu-id="a594d-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="a594d-142">Commentez ou supprimez la boucle `For Each` ou `foreach` dans `SumPageSizesAsync`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a594d-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    byte[] urlContent = await client.GetByteArrayAsync(url);

    //    // The previous line abbreviates the following two assignment
    //    // statements.
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
    //    byte[] urlContent = await getContentTask;

    //    DisplayResults(url, urlContent);

    //    // Update the total.
    //    total += urlContent.Length;
    //}
    ```

3. <span data-ttu-id="a594d-143">Définissez une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web.</span><span class="sxs-lookup"><span data-stu-id="a594d-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="a594d-144">Les tâches sont démarrées quand la requête est évaluée.</span><span class="sxs-lookup"><span data-stu-id="a594d-144">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="a594d-145">Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `client` et `urlList`.</span><span class="sxs-lookup"><span data-stu-id="a594d-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="a594d-146">Ensuite, appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="a594d-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="a594d-147">`Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.</span><span class="sxs-lookup"><span data-stu-id="a594d-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="a594d-148">Dans l’exemple suivant, l’expression `await` attend l’achèvement de la tâche unique retournée par `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="a594d-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="a594d-149">Une fois cette tâche achevée, l’expression `await` correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé.</span><span class="sxs-lookup"><span data-stu-id="a594d-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="a594d-150">Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="a594d-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="a594d-151">Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir la somme des longueurs de tous les sites web.</span><span class="sxs-lookup"><span data-stu-id="a594d-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="a594d-152">Ajoutez la ligne suivante à `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a594d-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="a594d-153">Pour tester les solutions Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="a594d-153">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="a594d-154">Pour l’une ou l’autre solution, appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="a594d-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="a594d-155">La sortie doit ressembler à celle des solutions async fournies dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a594d-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="a594d-156">Toutefois, notez que les sites web apparaissent à chaque fois dans un ordre différent.</span><span class="sxs-lookup"><span data-stu-id="a594d-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="a594d-157"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a594d-157">Example</span></span>

<span data-ttu-id="a594d-158">Le code suivant montre les extensions du projet qui utilise la méthode `GetURLContentsAsync` pour télécharger du contenu à partir du web.</span><span class="sxs-lookup"><span data-stu-id="a594d-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Two-step async call.
            Task sumTask = SumPageSizesAsync();
            await sumTask;

            // One-step async call.
            //await SumPageSizesAsync();

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    byte[] urlContents = await GetURLContentsAsync(url);

            //    // The previous line abbreviates the following two assignment statements.
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
            //    //byte[] urlContents = await getContentsTask;

            //    DisplayResults(url, urlContents);

            //    // Update the total.
            //    total += urlContents.Length;
            //}

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        private async Task<int> ProcessURLAsync(string url)
        {
            var byteArray = await GetURLContentsAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    await responseStream.CopyToAsync(content);
                }
            }

            // Return the result as a byte array.
            return content.ToArray();

        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="a594d-159"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a594d-159">Example</span></span>

<span data-ttu-id="a594d-160">Le code suivant montre les extensions du projet qui utilise la méthode `HttpClient.GetByteArrayAsync` pour télécharger du contenu à partir du web.</span><span class="sxs-lookup"><span data-stu-id="a594d-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_HttpClient_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url, client);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    byte[] urlContent = await client.GetByteArrayAsync(url);

            //    // The previous line abbreviates the following two assignment
            //    // statements.
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
            //    byte[] urlContent = await getContentTask;

            //    DisplayResults(url, urlContent);

            //    // Update the total.
            //    total += urlContent.Length;
            //}

            // Display the total count for all of the web addresses.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
        {
            byte[] byteArray = await client.GetByteArrayAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each web site. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a594d-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a594d-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a594d-162">Procédure pas à pas : accès au web avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="a594d-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
