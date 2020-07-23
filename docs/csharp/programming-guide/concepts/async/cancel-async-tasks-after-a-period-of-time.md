---
title: Annuler des tâches asynchrones après une période spécifique (C#)
description: Utilisez la méthode CancellationTokenSource. CancelAfter en C# pour planifier l’annulation des tâches associées qui ne sont pas terminées au cours d’un certain laps de temps dans cet exemple.
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: f32af1d893c60ac17648f60fa3aa90adaa0383e8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925290"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="dc971-103">Annuler des tâches async après une période spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="dc971-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="dc971-104">Si vous ne souhaitez pas attendre la fin d’une opération asynchrone, vous pouvez l’annuler après une période spécifique à l’aide de la méthode <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc971-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="dc971-105">Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées au terme de la période indiquée par l’expression `CancelAfter`.</span><span class="sxs-lookup"><span data-stu-id="dc971-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="dc971-106">Cet exemple s’appuie sur le code développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites web et afficher la longueur du contenu de chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="dc971-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="dc971-107">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dc971-107">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="dc971-108">Télécharger l'exemple</span><span class="sxs-lookup"><span data-stu-id="dc971-108">Download the example</span></span>

<span data-ttu-id="dc971-109">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="dc971-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="dc971-110">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc971-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="dc971-111">Dans la barre de menus, choisissez **fichier**  >  **ouvrir**un  >  **projet/une solution**.</span><span class="sxs-lookup"><span data-stu-id="dc971-111">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="dc971-112">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="dc971-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="dc971-113">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterTime**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="dc971-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="dc971-114">Appuyez sur la touche **F5** pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="dc971-114">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="dc971-115">(Ou appuyez sur **CTRL** + **F5** pour exécuter le projet sans le déboguer).</span><span class="sxs-lookup"><span data-stu-id="dc971-115">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="dc971-116">Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.</span><span class="sxs-lookup"><span data-stu-id="dc971-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="dc971-117">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="dc971-117">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="dc971-118">Générer l’exemple</span><span class="sxs-lookup"><span data-stu-id="dc971-118">Build the example</span></span>

<span data-ttu-id="dc971-119">L’exemple de cette rubrique s’appuie sur le projet développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="dc971-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="dc971-120">Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.</span><span class="sxs-lookup"><span data-stu-id="dc971-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="dc971-121">Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="dc971-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="dc971-122">Ajoutez les changements de cette rubrique à ce projet.</span><span class="sxs-lookup"><span data-stu-id="dc971-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="dc971-123">Pour spécifier une durée maximale avant que les tâches ne soient marquées comme annulées, ajoutez un appel à `CancelAfter` à `startButton_Click`, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dc971-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="dc971-124">L’ajout est signalé par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="dc971-124">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 <span data-ttu-id="dc971-125">Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.</span><span class="sxs-lookup"><span data-stu-id="dc971-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="dc971-126">La sortie suivante est un exemple.</span><span class="sxs-lookup"><span data-stu-id="dc971-126">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="dc971-127">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="dc971-127">Complete example</span></span>

<span data-ttu-id="dc971-128">Le code suivant est le texte complet du fichier MainWindow.xaml.cs de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="dc971-128">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="dc971-129">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="dc971-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="dc971-130">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="dc971-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="dc971-131">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="dc971-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="dc971-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc971-132">See also</span></span>

- [<span data-ttu-id="dc971-133">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="dc971-133">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="dc971-134">Procédure pas à pas : accès au web avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="dc971-134">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="dc971-135">Annuler une tâche asynchrone ou une liste de tâches (C#)</span><span class="sxs-lookup"><span data-stu-id="dc971-135">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="dc971-136">Réglage de votre application asynchrone (C#)</span><span class="sxs-lookup"><span data-stu-id="dc971-136">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="dc971-137">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="dc971-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
