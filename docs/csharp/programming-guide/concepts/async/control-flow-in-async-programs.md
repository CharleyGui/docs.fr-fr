---
title: Flux de contrôle dans les programmes Async (C#)
description: En savoir plus sur le workflow de contrôle dans un simple programme C# Async pour comprendre comment écrire et gérer des programmes asynchrones à l’aide des mots clés Async et await.
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 3946db958466a9f9914a5fa7b37c0db3a64d4b3d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925369"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="86763-103">Flux de contrôle dans les programmes asynchrones (C#)</span><span class="sxs-lookup"><span data-stu-id="86763-103">Control flow in async programs (C#)</span></span>

<span data-ttu-id="86763-104">Vous pouvez écrire et tenir à jour des programmes asynchrones plus facilement à l’aide des mots clés `async` et `await`.</span><span class="sxs-lookup"><span data-stu-id="86763-104">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="86763-105">Toutefois, les résultats peuvent vous étonner si vous ne comprenez pas le fonctionnement de votre programme.</span><span class="sxs-lookup"><span data-stu-id="86763-105">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="86763-106">Cette rubrique suit le flux de contrôle par le biais d’un programme asynchrone simple pour vous montrer quand le contrôle se déplace d’une méthode à une autre et quelles informations sont transférées à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="86763-106">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="86763-107">En général, vous marquez les méthodes qui contiennent du code asynchrone avec le modificateur [async (C#)](../../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="86763-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="86763-108">Dans une méthode marquée avec un modificateur async, vous pouvez utiliser un opérateur [await (C#)](../../../language-reference/operators/await.md) pour spécifier où la méthode s’interrompt afin d’attendre qu’un processus asynchrone appelé s’exécute.</span><span class="sxs-lookup"><span data-stu-id="86763-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="86763-109">Pour plus d’informations, consultez [Programmation asynchrone avec async et await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="86763-109">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="86763-110">L’exemple suivant utilise des méthodes async pour télécharger le contenu d’un site web spécifié sous forme de chaîne et afficher la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="86763-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="86763-111">Il contient les deux méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="86763-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="86763-112">`startButton_Click`, qui appelle `AccessTheWebAsync` et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="86763-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="86763-113">`AccessTheWebAsync`, qui télécharge le contenu d’un site web sous forme de chaîne et retourne la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="86763-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="86763-114">`AccessTheWebAsync` utilise une méthode asynchrone <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pour télécharger le contenu.</span><span class="sxs-lookup"><span data-stu-id="86763-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="86763-115">Des lignes numérotées apparaissent à des points stratégiques du programme pour vous aider à comprendre comment le programme s’exécute et expliquer ce qui se produit à chaque point marqué.</span><span class="sxs-lookup"><span data-stu-id="86763-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="86763-116">Les lignes sont étiquetées de "ONE" à "SIX".</span><span class="sxs-lookup"><span data-stu-id="86763-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="86763-117">Les étiquettes représentent l’ordre dans lequel le programme atteint ces lignes de code.</span><span class="sxs-lookup"><span data-stu-id="86763-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="86763-118">Le code suivant illustre un plan du programme.</span><span class="sxs-lookup"><span data-stu-id="86763-118">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="86763-119">Chacun des emplacements étiquetés de "ONE" à "SIX" affiche des informations sur l’état actuel du programme.</span><span class="sxs-lookup"><span data-stu-id="86763-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="86763-120">La sortie suivante est produite :</span><span class="sxs-lookup"><span data-stu-id="86763-120">The following output is produced:</span></span>

```output
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="86763-121">Configurer le programme</span><span class="sxs-lookup"><span data-stu-id="86763-121">Set up the program</span></span>

<span data-ttu-id="86763-122">Vous pouvez télécharger le code que cette rubrique utilise à partir de MSDN, ou vous pouvez le créer vous-même.</span><span class="sxs-lookup"><span data-stu-id="86763-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="86763-123">Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86763-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="86763-124">Télécharger le programme</span><span class="sxs-lookup"><span data-stu-id="86763-124">Download the program</span></span>

<span data-ttu-id="86763-125">Vous pouvez télécharger l’application utilisée dans cette rubrique à partir de l’[exemple Async : Flux de contrôle dans les programmes Async](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="86763-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="86763-126">Les étapes suivantes ouvrent et exécutent le programme.</span><span class="sxs-lookup"><span data-stu-id="86763-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="86763-127">Décompressez le fichier téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86763-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="86763-128">Dans la barre de menus, choisissez **fichier**  >  **ouvrir**un  >  **projet/une solution**.</span><span class="sxs-lookup"><span data-stu-id="86763-128">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="86763-129">Accédez au dossier qui contient l’exemple de code décompressé, ouvrez le fichier solution (.sln), puis choisissez la touche **F5** pour générer et exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="86763-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="86763-130">Créer le programme vous-même</span><span class="sxs-lookup"><span data-stu-id="86763-130">Create the program Yourself</span></span>

<span data-ttu-id="86763-131">Le projet Windows Presentation Foundation (WPF) suivant contient l’exemple de code utilisé pour cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="86763-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="86763-132">Pour exécuter le projet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="86763-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="86763-133">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86763-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="86763-134">Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.</span><span class="sxs-lookup"><span data-stu-id="86763-134">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="86763-135">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="86763-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="86763-136">Choisissez la catégorie **installé**du  >  Bureau Windows**Visual C#**  >  **Windows Desktop** , puis choisissez **application WPF** dans la liste des modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="86763-136">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="86763-137">Entrez `AsyncTracer` comme nom du projet, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="86763-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="86763-138">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="86763-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="86763-139">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="86763-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="86763-140">Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="86763-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="86763-141">Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="86763-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="86763-142">Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="86763-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="86763-143">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="86763-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="86763-144">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="86763-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="86763-145">Dans MainWindow.xaml.cs, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="86763-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="86763-146">Appuyez sur la touche **F5** pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="86763-146">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="86763-147">Vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="86763-147">The following output appears:</span></span>

    ```output
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="86763-148">Tracer le programme</span><span class="sxs-lookup"><span data-stu-id="86763-148">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="86763-149">Étapes UN et DEUX</span><span class="sxs-lookup"><span data-stu-id="86763-149">Steps ONE and TWO</span></span>

<span data-ttu-id="86763-150">Les deux premières lignes d’affichage suivent le chemin quand `startButton_Click` appelle `AccessTheWebAsync` et `AccessTheWebAsync` appelle la méthode asynchrone <xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="86763-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="86763-151">L’image suivante montre les appels de méthode à méthode.</span><span class="sxs-lookup"><span data-stu-id="86763-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="86763-152">![Étapes UN et DEUX](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="86763-152">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="86763-153">Le type de retour de `AccessTheWebAsync` et de `client.GetStringAsync` est <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="86763-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="86763-154">Pour `AccessTheWebAsync`, TResult est un entier.</span><span class="sxs-lookup"><span data-stu-id="86763-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="86763-155">Pour `GetStringAsync`, TResult est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="86763-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="86763-156">Pour plus d’informations sur les types de retour de méthode asynchrone, consultez [Types de retour Async (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="86763-156">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="86763-157">Une méthode async retournant une tâche retourne une instance de tâche quand le contrôle revient vers l’appelant.</span><span class="sxs-lookup"><span data-stu-id="86763-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="86763-158">Le contrôle retourne d’une méthode async à son appelant quand un opérateur `await` est rencontré dans la méthode appelée ou quand la méthode appelée se termine.</span><span class="sxs-lookup"><span data-stu-id="86763-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="86763-159">Les lignes qui sont étiquetées "THREE" à "SIX" suivent cette partie du processus.</span><span class="sxs-lookup"><span data-stu-id="86763-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="86763-160">Étape TROIS</span><span class="sxs-lookup"><span data-stu-id="86763-160">Step THREE</span></span>

<span data-ttu-id="86763-161">Dans `AccessTheWebAsync`, la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> est appelée pour télécharger le contenu de la page web cible.</span><span class="sxs-lookup"><span data-stu-id="86763-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="86763-162">Le contrôle retourne de `client.GetStringAsync` à `AccessTheWebAsync` quand `client.GetStringAsync` retourne une sortie.</span><span class="sxs-lookup"><span data-stu-id="86763-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="86763-163">La méthode `client.GetStringAsync` retourne une tâche de la chaîne assignée à la variable `getStringTask` dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="86763-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="86763-164">La ligne suivante de l’exemple de programme illustre l’appel à `client.GetStringAsync` et l’assignation.</span><span class="sxs-lookup"><span data-stu-id="86763-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="86763-165">Vous pouvez considérer la tâche comme une promesse faite par `client.GetStringAsync` de produire au final une chaîne réelle.</span><span class="sxs-lookup"><span data-stu-id="86763-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="86763-166">Pour le moment, si `AccessTheWebAsync` a du travail à effectuer qui ne dépend pas de la chaîne promise de `client.GetStringAsync`, ce travail peut se poursuivre pendant que `client.GetStringAsync` attend.</span><span class="sxs-lookup"><span data-stu-id="86763-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="86763-167">Dans l’exemple, les lignes de sortie suivantes, qui sont étiquetées « THREE », représentent la possibilité d’effectuer un travail indépendant</span><span class="sxs-lookup"><span data-stu-id="86763-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="86763-168">L’instruction suivante interrompt la progression dans `AccessTheWebAsync` quand `getStringTask` est attendu.</span><span class="sxs-lookup"><span data-stu-id="86763-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="86763-169">L’illustration suivante montre le flux de contrôle entre `client.GetStringAsync` et l’assignation à `getStringTask`, puis entre la création de `getStringTask` et l’application d’un opérateur await.</span><span class="sxs-lookup"><span data-stu-id="86763-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="86763-170">![Étape 3](./media/asynctrace-three.png "AsyncTrace-trois")</span><span class="sxs-lookup"><span data-stu-id="86763-170">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="86763-171">L’expression await suspend `AccessTheWebAsync` jusqu’à ce que `client.GetStringAsync` retourne une sortie.</span><span class="sxs-lookup"><span data-stu-id="86763-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="86763-172">Dans le même temps, le contrôle retourne à l’appelant de `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="86763-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="86763-173">En général, vous attendez immédiatement l’appel à une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="86763-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="86763-174">Par exemple, l’assignation suivante peut substituer le code précédent qui crée, puis attend `getStringTask` : `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="86763-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="86763-175">Dans cette rubrique, l’opérateur await est appliqué ultérieurement pour s’adapter aux lignes de sortie qui marquent le flux de contrôle dans le programme.</span><span class="sxs-lookup"><span data-stu-id="86763-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="86763-176">Étape FOUR</span><span class="sxs-lookup"><span data-stu-id="86763-176">Step FOUR</span></span>

<span data-ttu-id="86763-177">Le type de retour déclaré de `AccessTheWebAsync` est `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="86763-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="86763-178">Par conséquent, quand la méthode `AccessTheWebAsync` est suspendue, elle retourne une tâche d’entier à `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="86763-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="86763-179">Vous devez comprendre que la tâche retournée n’est pas `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="86763-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="86763-180">Il s’agit d’une tâche d’entier qui représente ce qu’il reste à effectuer dans la méthode interrompue, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="86763-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="86763-181">La tâche est une promesse de `AccessTheWebAsync` de produire un entier quand la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="86763-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="86763-182">L’instruction suivante assigne cette tâche à la variable `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="86763-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="86763-183">Comme dans `AccessTheWebAsync`, `startButton_Click` peut continuer le travail qui ne dépend pas des résultats de la tâche asynchrone (`getLengthTask`) jusqu’à ce que la tâche soit attendue.</span><span class="sxs-lookup"><span data-stu-id="86763-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="86763-184">Les lignes de sortie suivantes représentent ce travail.</span><span class="sxs-lookup"><span data-stu-id="86763-184">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="86763-185">La progression dans `startButton_Click` est suspendue quand `getLengthTask` est attendu.</span><span class="sxs-lookup"><span data-stu-id="86763-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="86763-186">L’instruction d’assignation suivante interrompt `startButton_Click` jusqu’à ce que la méthode `AccessTheWebAsync` soit terminée.</span><span class="sxs-lookup"><span data-stu-id="86763-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="86763-187">Dans l’illustration suivante, les flèches indiquent le flux de contrôle entre l’expression await dans `AccessTheWebAsync` et l’assignation d’une valeur à `getLengthTask`, suivie du traitement normal dans `startButton_Click` jusqu’à ce que `getLengthTask` soit attendu.</span><span class="sxs-lookup"><span data-stu-id="86763-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="86763-188">![Étape 4](./media/asynctrace-four.png "AsyncTrace-quatre")</span><span class="sxs-lookup"><span data-stu-id="86763-188">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="86763-189">Étape FIVE</span><span class="sxs-lookup"><span data-stu-id="86763-189">Step FIVE</span></span>

<span data-ttu-id="86763-190">Quand `client.GetStringAsync` signale que son exécution est terminée, le traitement dans `AccessTheWebAsync` est libéré de la suspension et peut continuer après l’instruction await.</span><span class="sxs-lookup"><span data-stu-id="86763-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="86763-191">Les lignes de sortie suivantes représentent la reprise du traitement.</span><span class="sxs-lookup"><span data-stu-id="86763-191">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="86763-192">L’opérande de l’instruction return, `urlContents.Length`, est stocké dans la tâche que `AccessTheWebAsync` retourne.</span><span class="sxs-lookup"><span data-stu-id="86763-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="86763-193">L’expression await récupère cette valeur à partir de `getLengthTask` dans `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="86763-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="86763-194">L’illustration suivante présente le transfert du contrôle après l’exécution de `client.GetStringAsync` (et de `getStringTask`).</span><span class="sxs-lookup"><span data-stu-id="86763-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="86763-195">![Étape FIVE](./media/asynctrace-five.png "AsyncTrace-cinq")</span><span class="sxs-lookup"><span data-stu-id="86763-195">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="86763-196">`AccessTheWebAsync` s’exécute jusqu’à la fin et le contrôle retourne à `startButton_Click`, qui attend que son exécution soit terminée.</span><span class="sxs-lookup"><span data-stu-id="86763-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="86763-197">Étape SIX</span><span class="sxs-lookup"><span data-stu-id="86763-197">Step SIX</span></span>

<span data-ttu-id="86763-198">Quand `AccessTheWebAsync` signale que son exécution est terminée, le traitement peut continuer après l’instruction await dans `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="86763-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="86763-199">En fait, le programme n’a plus rien d’autre à faire.</span><span class="sxs-lookup"><span data-stu-id="86763-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="86763-200">Les lignes de sortie suivantes représentent la reprise du traitement dans `startButton_Async` :</span><span class="sxs-lookup"><span data-stu-id="86763-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="86763-201">L’expression await récupère de `getLengthTask` la valeur entière qui est l’opérande de l’instruction return dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="86763-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="86763-202">L’instruction suivante assigne cette valeur à la variable `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="86763-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="86763-203">L’illustration suivante montre le retour du contrôle de `AccessTheWebAsync` à `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="86763-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="86763-204">![Étape SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="86763-204">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="86763-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86763-205">See also</span></span>

- [<span data-ttu-id="86763-206">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="86763-206">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="86763-207">Types de retour async (C#)</span><span class="sxs-lookup"><span data-stu-id="86763-207">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="86763-208">Procédure pas à pas : accès au web avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="86763-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="86763-209">Exemple Async : Flux de contrôle dans les programmes Async (C# et Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86763-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
