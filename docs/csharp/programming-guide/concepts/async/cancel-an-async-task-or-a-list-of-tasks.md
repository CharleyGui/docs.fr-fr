---
title: Annuler une tâche asynchrone ou une liste de tâches (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 05ddb2c76a16ed4f79d795510434aa3abb5615d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583372"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="f8721-102">Annuler une tâche async ou une liste de tâches (C#)</span><span class="sxs-lookup"><span data-stu-id="f8721-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="f8721-103">Vous pouvez créer un bouton permettant d’annuler une application asynchrone que vous souhaitez interrompre avant la fin de son exécution.</span><span class="sxs-lookup"><span data-stu-id="f8721-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="f8721-104">Les exemples de cette rubrique vous montrent comment ajouter un bouton d’annulation à une application qui télécharge du contenu d’un site web ou une liste de sites web.</span><span class="sxs-lookup"><span data-stu-id="f8721-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="f8721-105">Les exemples utilisent l’interface utilisateur décrite dans [Réglage de votre application Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="f8721-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="f8721-106">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8721-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="f8721-107">Annuler une tâche</span><span class="sxs-lookup"><span data-stu-id="f8721-107">Cancel a task</span></span>

<span data-ttu-id="f8721-108">Le premier exemple associe le bouton **Annuler** à une tâche de téléchargement unique.</span><span class="sxs-lookup"><span data-stu-id="f8721-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="f8721-109">Si vous appuyez sur le bouton pendant que l’application télécharge du contenu, le téléchargement est annulé.</span><span class="sxs-lookup"><span data-stu-id="f8721-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="f8721-110">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="f8721-110">Download the example</span></span>

<span data-ttu-id="f8721-111">Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Exemple Async  : Réglage précis de votre application), puis suivez ces étapes.</span><span class="sxs-lookup"><span data-stu-id="f8721-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="f8721-112">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8721-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f8721-113">Dans la barre de menus, choisissez **Fichier** > **Ouvrir** > **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f8721-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="f8721-114">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="f8721-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="f8721-115">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelATask**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f8721-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="f8721-116">Choisissez la touche **F5** pour exécuter le projet (ou appuyez sur **Ctrl**+**F5** pour exécuter le projet sans le déboguer).</span><span class="sxs-lookup"><span data-stu-id="f8721-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="f8721-117">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue les fichiers MainWindow.xaml.cs à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f8721-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="f8721-118">Générer l’exemple</span><span class="sxs-lookup"><span data-stu-id="f8721-118">Build the example</span></span>
 <span data-ttu-id="f8721-119">Les modifications suivantes ajoutent un bouton **Annuler** à une application de téléchargement d’un site web.</span><span class="sxs-lookup"><span data-stu-id="f8721-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="f8721-120">Si vous ne voulez pas télécharger ou générer l’exemple, vous pouvez examiner le produit final dans la section « Exemples complets », à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f8721-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="f8721-121">Les astérisques signalent les modifications du code.</span><span class="sxs-lookup"><span data-stu-id="f8721-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="f8721-122">Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **StarterCode** comme **Projet de démarrage** au lieu de **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="f8721-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="f8721-123">Ensuite, apportez les modifications suivantes dans le fichier MainWindow.xaml.cs de ce projet.</span><span class="sxs-lookup"><span data-stu-id="f8721-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="f8721-124">Déclarez une variable `CancellationTokenSource`, `cts`, qui se trouve dans la portée de toutes les méthodes qui y accèdent.</span><span class="sxs-lookup"><span data-stu-id="f8721-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="f8721-125">Ajoutez le gestionnaire d’événements suivant pour le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="f8721-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="f8721-126">Le gestionnaire d’événements utilise la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour notifier à `cts` la demande d’annulation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f8721-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="f8721-127">Effectuez les modifications suivantes dans le gestionnaire d’événements pour le bouton **Démarrer**, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f8721-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="f8721-128">Instanciez le `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="f8721-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="f8721-129">Dans l’appel à `AccessTheWebAsync`, qui télécharge le contenu d’un site web spécifié, envoyez la propriété <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> de `cts` comme argument.</span><span class="sxs-lookup"><span data-stu-id="f8721-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="f8721-130">La propriété `Token` propage le message si l’annulation est demandée.</span><span class="sxs-lookup"><span data-stu-id="f8721-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="f8721-131">Ajoutez un bloc catch qui affiche un message si l’utilisateur choisit d’annuler l’opération de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="f8721-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="f8721-132">Le code suivant illustre les modifications.</span><span class="sxs-lookup"><span data-stu-id="f8721-132">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="f8721-133">Dans `AccessTheWebAsync`, utilisez la surcharge <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> de la méthode `GetAsync` dans le type <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web.</span><span class="sxs-lookup"><span data-stu-id="f8721-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="f8721-134">Passez `ct`, le paramètre <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, comme deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="f8721-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="f8721-135">Le jeton transmet le message si l’utilisateur choisit le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="f8721-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="f8721-136">Le code suivant illustre les modifications dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f8721-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="f8721-137">Si vous n’annulez pas le programme, il génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f8721-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="f8721-138">Si vous choisissez le bouton **Annuler** quand le programme est encore en train de télécharger du contenu, le programme génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f8721-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="f8721-139">Annuler une liste de tâches</span><span class="sxs-lookup"><span data-stu-id="f8721-139">Cancel a list of tasks</span></span>

<span data-ttu-id="f8721-140">Vous pouvez étendre l’exemple précédent pour annuler de nombreuses tâches à la fois en associant la même instance `CancellationTokenSource` à chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="f8721-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="f8721-141">Si vous choisissez le bouton **Annuler**, vous annulez toutes les tâches qui ne sont pas encore terminées.</span><span class="sxs-lookup"><span data-stu-id="f8721-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="f8721-142">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="f8721-142">Download the example</span></span>

<span data-ttu-id="f8721-143">Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Exemple Async  : Réglage précis de votre application), puis suivez ces étapes.</span><span class="sxs-lookup"><span data-stu-id="f8721-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="f8721-144">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8721-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f8721-145">Dans la barre de menus, choisissez **Fichier** > **Ouvrir** > **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f8721-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="f8721-146">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="f8721-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="f8721-147">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAListOfTasks**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f8721-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="f8721-148">Appuyez sur la touche **F5** pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="f8721-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="f8721-149">Appuyez sur les touches **Ctrl**+**F5** pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="f8721-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="f8721-150">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue les fichiers MainWindow.xaml.cs à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f8721-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="f8721-151">Générer l’exemple</span><span class="sxs-lookup"><span data-stu-id="f8721-151">Build the example</span></span>

<span data-ttu-id="f8721-152">Pour étendre l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelATask** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f8721-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="f8721-153">Apportez les modifications suivantes au projet.</span><span class="sxs-lookup"><span data-stu-id="f8721-153">Add the following changes to that project.</span></span> <span data-ttu-id="f8721-154">Les astérisques signalent les modifications effectuées dans le programme.</span><span class="sxs-lookup"><span data-stu-id="f8721-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="f8721-155">Ajoutez une méthode pour créer une liste des adresses web.</span><span class="sxs-lookup"><span data-stu-id="f8721-155">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
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
    ```

2. <span data-ttu-id="f8721-156">Appelez la méthode dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f8721-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="f8721-157">Ajoutez la boucle suivante dans `AccessTheWebAsync` pour traiter chaque adresse web dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f8721-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="f8721-158">Comme `AccessTheWebAsync` affiche les longueurs, la méthode n’a pas besoin de retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="f8721-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="f8721-159">Supprimez l’instruction return et changez le type de retour de la méthode de <xref:System.Threading.Tasks.Task> en <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f8721-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="f8721-160">Appelez la méthode à partir de `startButton_Click` à l’aide d’une instruction au lieu d’une expression.</span><span class="sxs-lookup"><span data-stu-id="f8721-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="f8721-161">Si vous n’annulez pas le programme, il génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f8721-161">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="f8721-162">Si vous choisissez le bouton **Annuler** avant la fin des téléchargements, la sortie contient les longueurs des chaînes ayant été téléchargées avant l’annulation.</span><span class="sxs-lookup"><span data-stu-id="f8721-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="f8721-163">Exemples complets</span><span class="sxs-lookup"><span data-stu-id="f8721-163">Complete examples</span></span>

<span data-ttu-id="f8721-164">Les sections suivantes contiennent le code correspondant à chacun des exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="f8721-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="f8721-165">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f8721-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="f8721-166">Vous pouvez télécharger les projets sur [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Exemple Async : Réglage précis de votre application).</span><span class="sxs-lookup"><span data-stu-id="f8721-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="f8721-167">Exemple - Annuler une tâche</span><span class="sxs-lookup"><span data-stu-id="f8721-167">Example - Cancel a task</span></span>

<span data-ttu-id="f8721-168">Le code suivant est le fichier MainWindow.xaml.cs complet pour l’exemple qui annule une seule tâche.</span><span class="sxs-lookup"><span data-stu-id="f8721-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="f8721-169">Exemple - Annuler une liste de tâches</span><span class="sxs-lookup"><span data-stu-id="f8721-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="f8721-170">Le code suivant est le fichier MainWindow.xaml.cs complet pour l’exemple qui annule une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="f8721-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
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
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
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

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="f8721-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8721-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="f8721-172">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="f8721-172">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f8721-173">Ajuster une application Async (C#)</span><span class="sxs-lookup"><span data-stu-id="f8721-173">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="f8721-174">Exemple Async : Réglage de votre application</span><span class="sxs-lookup"><span data-stu-id="f8721-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
