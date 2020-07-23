---
title: Comment effectuer plusieurs requêtes Web en parallèle en utilisant Async et await (C#)
description: Découvrez comment séparer la création d’une tâche à l’aide de l’opérateur await en C#, au lieu de l’appliquer lors de la création d’une tâche.
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 899dfd9165d199a67a5178bb351081ee544b231f
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925161"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="4ea60-103">Comment effectuer plusieurs requêtes Web en parallèle en utilisant Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea60-103">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="4ea60-104">Dans une méthode Async, les tâches sont démarrées quand elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="4ea60-104">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="4ea60-105">L’opérateur [await](../../../language-reference/operators/await.md) est appliqué à la tâche au point de la méthode où le traitement ne peut pas se poursuivre tant que la tâche n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="4ea60-105">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="4ea60-106">Souvent, une tâche est attendue dès qu’elle est créée, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4ea60-106">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="4ea60-107">Toutefois, vous pouvez séparer la création de la tâche en attendant la tâche si votre programme a d’autres tâches à effectuer qui ne dépendent pas de la fin de la tâche.</span><span class="sxs-lookup"><span data-stu-id="4ea60-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="4ea60-108">Entre le démarrage d’une tâche et le moment où elle est attendue, vous pouvez démarrer d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="4ea60-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="4ea60-109">Les tâches supplémentaires s’exécutent implicitement en parallèle, mais aucun thread supplémentaire n’est créé.</span><span class="sxs-lookup"><span data-stu-id="4ea60-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="4ea60-110">Le programme suivant démarre trois téléchargements Web asynchrones, puis les attend dans l’ordre dans lequel ils sont appelés.</span><span class="sxs-lookup"><span data-stu-id="4ea60-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="4ea60-111">Notez que lorsque vous exécutez le programme, les tâches ne se terminent pas toujours dans l’ordre dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="4ea60-111">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="4ea60-112">Elles commencent à s’exécuter lorsqu’elles sont créées, et une ou plusieurs tâches peuvent se terminer avant que la méthode n’atteigne les expressions await.</span><span class="sxs-lookup"><span data-stu-id="4ea60-112">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ea60-113">Pour mener à bien ce projet, Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4ea60-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="4ea60-114">Pour obtenir un autre exemple qui démarre plusieurs tâches en même temps, consultez [comment étendre la procédure pas à pas Async à l’aide de Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="4ea60-114">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="4ea60-115">Vous pouvez télécharger le code de cet exemple à partir des [exemples de code pour développeur](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="4ea60-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="4ea60-116">Pour configurer le projet</span><span class="sxs-lookup"><span data-stu-id="4ea60-116">To set up the project</span></span>  
  
1. <span data-ttu-id="4ea60-117">Pour configurer une application WPF, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4ea60-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="4ea60-118">Vous trouverez des instructions détaillées pour ces étapes dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4ea60-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="4ea60-119">Créez une application WPF qui contient une zone de texte et un bouton.</span><span class="sxs-lookup"><span data-stu-id="4ea60-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="4ea60-120">Nommez le bouton `startButton` et la zone de texte `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="4ea60-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="4ea60-121">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="4ea60-121">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="4ea60-122">Dans le fichier MainWindow.xaml.cs, ajoutez une directive `using` pour `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="4ea60-122">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="4ea60-123">Pour ajouter le code</span><span class="sxs-lookup"><span data-stu-id="4ea60-123">To add the code</span></span>  
  
1. <span data-ttu-id="4ea60-124">Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton pour créer le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4ea60-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="4ea60-125">Copiez le code suivant et collez-le dans le corps de `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4ea60-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="4ea60-126">Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, qui pilote l’application.</span><span class="sxs-lookup"><span data-stu-id="4ea60-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="4ea60-127">Ajoutez les méthodes de prise en charge suivantes au projet :</span><span class="sxs-lookup"><span data-stu-id="4ea60-127">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="4ea60-128">`ProcessURLAsync` utilise une méthode <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web sous la forme d’un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="4ea60-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="4ea60-129">La méthode de prise en charge, `ProcessURLAsync`, affiche et retourne ensuite la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="4ea60-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="4ea60-130">`DisplayResults` affiche le nombre d’octets dans le tableau d’octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="4ea60-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="4ea60-131">Cet affichage indique quand le téléchargement de chaque tâche est terminé.</span><span class="sxs-lookup"><span data-stu-id="4ea60-131">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="4ea60-132">Copiez les méthodes suivantes et collez-les après le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4ea60-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
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
    ```  
  
4. <span data-ttu-id="4ea60-133">Pour finir, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4ea60-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="4ea60-134">La méthode déclare un objet `HttpClient`, dont vous avez besoin pour accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dans `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="4ea60-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="4ea60-135">La méthode crée et démarre trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="4ea60-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="4ea60-136">À mesure que chaque tâche se termine, `DisplayResults` affiche son URL et la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="4ea60-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="4ea60-137">Les tâches s’exécutant de façon asynchrone, l’ordre d’affichage des résultats peut différer de celui dans lequel les tâches ont été déclarées.</span><span class="sxs-lookup"><span data-stu-id="4ea60-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="4ea60-138">La méthode attend l’achèvement de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="4ea60-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="4ea60-139">Chaque opérateur `await` suspend l’exécution de `CreateMultipleTasksAsync` jusqu’à la fin de la tâche attendue.</span><span class="sxs-lookup"><span data-stu-id="4ea60-139">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="4ea60-140">L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.</span><span class="sxs-lookup"><span data-stu-id="4ea60-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="4ea60-141">Une fois les tâches terminées et les valeurs entières récupérées, la méthode additionne les longueurs des sites web et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="4ea60-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="4ea60-142">Copiez la méthode suivante et collez-la dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="4ea60-142">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults
        // displays its length.  
        Task<int> download1 =
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="4ea60-143">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="4ea60-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="4ea60-144">Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminent pas toujours dans le même ordre et que l’ordre dans lequel elles se terminent n’est pas nécessairement l’ordre dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="4ea60-144">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea60-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ea60-145">Example</span></span>  
 <span data-ttu-id="4ea60-146">Le code suivant contient l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="4ea60-146">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
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
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults
            // displays its length.  
            Task<int> download1 =
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
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
  
## <a name="see-also"></a><span data-ttu-id="4ea60-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ea60-147">See also</span></span>

- [<span data-ttu-id="4ea60-148">Procédure pas à pas : accès au web avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea60-148">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="4ea60-149">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea60-149">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="4ea60-150">Comment étendre la procédure pas à pas Async à l’aide de Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea60-150">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
