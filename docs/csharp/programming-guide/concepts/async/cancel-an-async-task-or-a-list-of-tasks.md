---
title: Annuler une tâche asynchrone ou une liste de tâches (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595723"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Annuler une tâche async ou une liste de tâches (C#)

Vous pouvez créer un bouton permettant d’annuler une application asynchrone que vous souhaitez interrompre avant la fin de son exécution. Les exemples de cette rubrique vous montrent comment ajouter un bouton d’annulation à une application qui télécharge du contenu d’un site web ou une liste de sites web.

Les exemples utilisent l’interface utilisateur décrite dans [Réglage de votre application Async (C#)](./fine-tuning-your-async-application.md).

> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.

## <a name="cancel-a-task"></a>Annuler une tâche

Le premier exemple associe le bouton **Annuler** à une tâche de téléchargement unique. Si vous appuyez sur le bouton pendant que l’application télécharge du contenu, le téléchargement est annulé.

### <a name="download-the-example"></a>Télécharger l'exemple

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

1. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

2. Sur la barre de menu, choisissez **File** > **Open** > **Project/Solution**.

3. Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningCS.

4. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelATask**, puis choisissez **Définir comme projet de démarrage**.

5. Choisissez la touche **F5** pour exécuter le projet (ou appuyez sur **Ctrl**+**F5** pour exécuter le projet sans le déboguer).

> [!TIP]
> Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue les fichiers MainWindow.xaml.cs à la fin de cette rubrique.

### <a name="build-the-example"></a>Générer l’exemple
 Les modifications suivantes ajoutent un bouton **Annuler** à une application de téléchargement d’un site web. Si vous ne voulez pas télécharger ou générer l’exemple, vous pouvez examiner le produit final dans la section « Exemples complets », à la fin de cette rubrique. Les astérisques signalent les modifications du code.

 Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **StarterCode** comme **Projet de démarrage** au lieu de **CancelATask**.

 Ensuite, apportez les modifications suivantes dans le fichier MainWindow.xaml.cs de ce projet.

1. Déclarez une variable `CancellationTokenSource`, `cts`, qui se trouve dans la portée de toutes les méthodes qui y accèdent.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Ajoutez le gestionnaire d’événements suivant pour le bouton **Annuler**. Le gestionnaire d’événements utilise la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour notifier à `cts` la demande d’annulation de l’utilisateur.

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

3. Effectuez les modifications suivantes dans le gestionnaire d’événements pour le bouton **Démarrer**, `startButton_Click`.

    - Instanciez le `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - Dans l’appel à `AccessTheWebAsync`, qui télécharge le contenu d’un site web spécifié, envoyez la propriété <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> de `cts` comme argument. La propriété `Token` propage le message si l’annulation est demandée. Ajoutez un bloc catch qui affiche un message si l’utilisateur choisit d’annuler l’opération de téléchargement. Le code suivant illustre les modifications.

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

4. Dans `AccessTheWebAsync`, utilisez la surcharge <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> de la méthode `GetAsync` dans le type <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web. Passez `ct`, le paramètre <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, comme deuxième argument. Le jeton transmet le message si l’utilisateur choisit le bouton **Annuler**.

     Le code suivant illustre les modifications dans `AccessTheWebAsync`.

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

5. Si vous n’annulez pas le programme, il génère le résultat suivant.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Si vous choisissez le bouton **Annuler** quand le programme est encore en train de télécharger du contenu, le programme génère le résultat suivant.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Annuler une liste de tâches

Vous pouvez étendre l’exemple précédent pour annuler de nombreuses tâches à la fois en associant la même instance `CancellationTokenSource` à chaque tâche. Si vous choisissez le bouton **Annuler**, vous annulez toutes les tâches qui ne sont pas encore terminées.

### <a name="download-the-example"></a>Télécharger l'exemple

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

1. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

2. Sur la barre de menu, choisissez **File** > **Open** > **Project/Solution**.

3. Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningCS.

4. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAListOfTasks**, puis choisissez **Définir comme projet de démarrage**.

5. Appuyez sur la touche **F5** pour exécuter le projet.

     Choisissez les clés **Ctrl**+**F5** pour exécuter le projet sans le déboguer.

Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue les fichiers MainWindow.xaml.cs à la fin de cette rubrique.

### <a name="build-the-example"></a>Générer l’exemple

Pour étendre l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelATask** comme **Projet de démarrage**. Apportez les modifications suivantes au projet. Les astérisques signalent les modifications effectuées dans le programme.

1. Ajoutez une méthode pour créer une liste des adresses web.

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

2. Appelez la méthode dans `AccessTheWebAsync`.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Ajoutez la boucle suivante dans `AccessTheWebAsync` pour traiter chaque adresse web dans la liste.

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

4. Comme `AccessTheWebAsync` affiche les longueurs, la méthode n’a pas besoin de retourner une valeur. Supprimez l’instruction return et changez le type de retour de la méthode de <xref:System.Threading.Tasks.Task> en <xref:System.Threading.Tasks.Task%601>.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Appelez la méthode à partir de `startButton_Click` à l’aide d’une instruction au lieu d’une expression.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Si vous n’annulez pas le programme, il génère le résultat suivant.

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

     Si vous choisissez le bouton **Annuler** avant la fin des téléchargements, la sortie contient les longueurs des chaînes ayant été téléchargées avant l’annulation.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Exemples complets

Les sections suivantes contiennent le code correspondant à chacun des exemples précédents. Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.

Vous pouvez télécharger les projets à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Exemple - Annuler une tâche

Le code suivant est le fichier MainWindow.xaml.cs complet pour l’exemple qui annule une seule tâche.

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

### <a name="example---cancel-a-list-of-tasks"></a>Exemple - Annuler une liste de tâches

Le code suivant est le fichier MainWindow.xaml.cs complet pour l’exemple qui annule une liste de tâches.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Programmation asynchrone avec Async et Await (C#)](./index.md)
- [Réglage de votre application asynchrone (C#)](./fine-tuning-your-async-application.md)
- [Exemple Async : ajuster une application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
