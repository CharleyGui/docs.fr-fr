---
title: Comment faire plusieurs demandes web en parallèle en utilisant async et attendre (C)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 9f7420113d4af83d7d057b772af307bd8d4bcc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169947"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="fa1fa-102">Comment faire plusieurs demandes web en parallèle en utilisant async et attendre (C)</span><span class="sxs-lookup"><span data-stu-id="fa1fa-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="fa1fa-103">Dans une méthode asynchrone, les tâches sont démarrées quand elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="fa1fa-104">L’opérateur [await](../../../language-reference/operators/await.md) est appliqué à la tâche au point dans la méthode où le traitement ne peut pas se poursuivre tant que la tâche n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="fa1fa-105">Souvent, une tâche est attendue dès sa création, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="fa1fa-106">Toutefois, vous pouvez séparer la création de la tâche de son attente si votre programme doit accomplir d’autres tâches qui ne dépendent pas de l’achèvement de la tâche.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="fa1fa-107">Entre le démarrage d’une tâche et le moment où elle est attendue, vous pouvez démarrer d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="fa1fa-108">Les tâches supplémentaires s’exécutent implicitement en parallèle, mais aucun thread supplémentaire n’est créé.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="fa1fa-109">Le programme suivant démarre trois téléchargements web asynchrones, puis les attend dans l’ordre dans lequel ils sont appelés.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="fa1fa-110">Notez que quand vous exécutez le programme, les tâches ne se terminent pas toujours dans l’ordre dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="fa1fa-111">Elles commencent à s’exécuter quand elles sont créées, et une ou plusieurs d’entre elles peuvent se terminer avant que la méthode n’atteigne les expressions await.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa1fa-112">Pour mener à bien ce projet, Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="fa1fa-113">Pour un autre exemple qui commence plusieurs tâches en même temps, voir [Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="fa1fa-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="fa1fa-114">Vous pouvez télécharger le code de cet exemple à partir des [exemples de code pour développeur](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="fa1fa-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="fa1fa-115">Pour configurer le projet</span><span class="sxs-lookup"><span data-stu-id="fa1fa-115">To set up the project</span></span>  
  
1. <span data-ttu-id="fa1fa-116">Pour configurer une application WPF, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="fa1fa-117">Vous trouverez des instructions détaillées pour ces étapes dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="fa1fa-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="fa1fa-118">Créez une application WPF qui contient une zone de texte et un bouton.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="fa1fa-119">Nommez le bouton `startButton` et la zone de texte `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="fa1fa-120">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="fa1fa-121">Dans le fichier MainWindow.xaml.cs, ajoutez une directive `using` pour `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="fa1fa-122">Pour ajouter le code</span><span class="sxs-lookup"><span data-stu-id="fa1fa-122">To add the code</span></span>  
  
1. <span data-ttu-id="fa1fa-123">Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton pour créer le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="fa1fa-124">Copiez le code suivant et collez-le dans le corps de `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="fa1fa-125">Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, qui pilote l’application.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="fa1fa-126">Ajoutez les méthodes de prise en charge suivantes au projet :</span><span class="sxs-lookup"><span data-stu-id="fa1fa-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="fa1fa-127">`ProcessURLAsync` utilise une méthode <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web sous la forme d’un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="fa1fa-128">La méthode de prise en charge, `ProcessURLAsync`, affiche et retourne ensuite la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="fa1fa-129">`DisplayResults` affiche le nombre d’octets dans le tableau d’octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="fa1fa-130">Cet affichage indique quand le téléchargement de chaque tâche est terminé.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="fa1fa-131">Copiez les méthodes suivantes et collez-les après le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="fa1fa-132">Pour finir, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="fa1fa-133">La méthode déclare un objet `HttpClient`, dont vous avez besoin pour accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dans `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="fa1fa-134">La méthode crée et démarre trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="fa1fa-135">À mesure que chaque tâche se termine, `DisplayResults` affiche son URL et la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="fa1fa-136">Les tâches s’exécutant de façon asynchrone, l’ordre d’affichage des résultats peut différer de celui dans lequel les tâches ont été déclarées.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="fa1fa-137">La méthode attend l’achèvement de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="fa1fa-138">Chaque opérateur `await` suspend l’exécution de `CreateMultipleTasksAsync` jusqu’à la fin de la tâche attendue.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="fa1fa-139">L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="fa1fa-140">Une fois les tâches terminées et les valeurs entières récupérées, la méthode additionne les longueurs des sites web et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="fa1fa-141">Copiez la méthode suivante et collez-la dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="fa1fa-142">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="fa1fa-143">Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminent pas toujours dans le même ordre, et que l’ordre dans lequel elles se terminent n’est pas nécessairement celui dans lequel elles sont créées et attendues.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa1fa-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="fa1fa-144">Example</span></span>  
 <span data-ttu-id="fa1fa-145">Le code suivant contient l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="fa1fa-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa1fa-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa1fa-146">See also</span></span>

- [<span data-ttu-id="fa1fa-147">Procédure pas à pas : accès au web avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="fa1fa-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="fa1fa-148">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="fa1fa-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="fa1fa-149">Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)</span><span class="sxs-lookup"><span data-stu-id="fa1fa-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
