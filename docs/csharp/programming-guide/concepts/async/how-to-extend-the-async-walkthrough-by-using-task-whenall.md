---
title: Comment étendre la procédure pas à pas Async à l’aide de Task. WhenAll (C#)
description: Découvrez comment améliorer les performances de la solution Async en C# à l’aide de Task. WhenAll. Cette méthode attend de façon asynchrone plusieurs opérations asynchrones.
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 275f4aeca854f8938642dbea40bf7fd9dc5362d9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925213"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Comment étendre la procédure pas à pas Async à l’aide de Task. WhenAll (C#)

Vous pouvez améliorer les performances de la solution async fournie dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) à l’aide de la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Cette méthode attend de manière asynchrone plusieurs opérations, qui sont représentées sous la forme d’une collection de tâches.

Vous aurez peut-être remarqué dans la procédure pas à pas que les sites web se téléchargent à différentes vitesses. L’un des sites web est parfois très lent, ce qui retarde tous les autres téléchargements. Quand vous exécutez les solutions asynchrones que vous générez dans la procédure pas à pas, vous pouvez quitter le programme facilement si vous ne souhaitez pas attendre, mais une meilleure option consiste à démarrer tous les téléchargements en même temps et à laisser les plus rapides se poursuivre sans attendre celui qui est retardé.

Vous appliquez la méthode `Task.WhenAll` à une collection de tâches. L’application de `WhenAll` retourne une tâche unique qui n’est pas terminée tant que toutes les tâches de la collection ne sont pas terminées. Les tâches s’exécutent en parallèle, mais aucun thread supplémentaire n’est créé. Les tâches peuvent se terminer dans n’importe quel ordre.

> [!IMPORTANT]
> Les procédures suivantes décrivent des extensions pour les applications asynchrones qui sont développées dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez développer les applications soit en appliquant la procédure pas à pas, soit en téléchargeant le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Pour exécuter l’exemple, Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Pour ajouter Task.WhenAll à votre solution GetURLContentsAsync

1. Ajoutez la méthode `ProcessURLAsync` à la première application développée dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Si vous avez téléchargé le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.cs.

    - Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui inclut la méthode `GetURLContentsAsync`. Le fichier MainWindow.xaml.cs pour cette application est le premier exemple dans la section « Exemples de code complets de la procédure pas à pas ».

    La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `foreach` dans `SumPageSizesAsync` dans la procédure d’origine. La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Commentez ou supprimez la boucle `foreach` dans `SumPageSizesAsync`, comme illustré dans le code suivant.

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

3. Créez une collection de tâches. Le code suivant définit une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web. Les tâches sont démarrées quand la requête est évaluée.

    Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `urlList`.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.

    Dans l’exemple suivant, l’expression `await` attend l’achèvement de la tâche unique retournée par `WhenAll`. L’expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des longueurs de tous les sites web. Ajoutez la ligne suivante à `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Pour ajouter Task.WhenAll à la solution HttpClient.GetByteArrayAsync

1. Ajoutez la version suivante de `ProcessURLAsync` à la deuxième application développée dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Si vous avez téléchargé le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough_HttpClient, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.cs.

    - Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui utilise la méthode `HttpClient.GetByteArrayAsync`. Le fichier MainWindow.xaml.cs pour cette application est le deuxième exemple dans la section « Exemples de code complets de la procédure pas à pas ».

    La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `foreach` dans `SumPageSizesAsync` dans la procédure d’origine. La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.

    La seule différence par rapport à la méthode `ProcessURLAsync` de la procédure précédente est l’utilisation de l’instance <xref:System.Net.Http.HttpClient>, `client`.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Commentez ou supprimez la boucle `For Each` ou `foreach` dans `SumPageSizesAsync`, comme illustré dans le code suivant.

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

3. Définissez une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web. Les tâches sont démarrées quand la requête est évaluée.

    Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `client` et `urlList`.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Ensuite, appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.

    Dans l’exemple suivant, l’expression `await` attend l’achèvement de la tâche unique retournée par `WhenAll`. Une fois cette tâche achevée, l’expression `await` correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir la somme des longueurs de tous les sites web. Ajoutez la ligne suivante à `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Pour tester les solutions Task.WhenAll

- Pour l’une ou l’autre solution, appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** . La sortie doit ressembler à celle des solutions async fournies dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Toutefois, notez que les sites web apparaissent à chaque fois dans un ordre différent.

## <a name="example"></a>Exemple

Le code suivant montre les extensions du projet qui utilise la méthode `GetURLContentsAsync` pour télécharger du contenu à partir du web.

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

## <a name="example"></a>Exemple

Le code suivant montre les extensions du projet qui utilise la méthode `HttpClient.GetByteArrayAsync` pour télécharger du contenu à partir du web.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
