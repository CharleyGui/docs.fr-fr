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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Comment faire plusieurs demandes web en parallèle en utilisant async et attendre (C)
Dans une méthode asynchrone, les tâches sont démarrées quand elles sont créées. L’opérateur [await](../../../language-reference/operators/await.md) est appliqué à la tâche au point dans la méthode où le traitement ne peut pas se poursuivre tant que la tâche n’est pas terminée. Souvent, une tâche est attendue dès sa création, comme le montre l’exemple suivant.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Toutefois, vous pouvez séparer la création de la tâche de son attente si votre programme doit accomplir d’autres tâches qui ne dépendent pas de l’achèvement de la tâche.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Entre le démarrage d’une tâche et le moment où elle est attendue, vous pouvez démarrer d’autres tâches. Les tâches supplémentaires s’exécutent implicitement en parallèle, mais aucun thread supplémentaire n’est créé.  
  
 Le programme suivant démarre trois téléchargements web asynchrones, puis les attend dans l’ordre dans lequel ils sont appelés. Notez que quand vous exécutez le programme, les tâches ne se terminent pas toujours dans l’ordre dans lequel elles sont créées et attendues. Elles commencent à s’exécuter quand elles sont créées, et une ou plusieurs d’entre elles peuvent se terminer avant que la méthode n’atteigne les expressions await.  
  
> [!NOTE]
> Pour mener à bien ce projet, Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.  
  
 Pour un autre exemple qui commence plusieurs tâches en même temps, voir [Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Vous pouvez télécharger le code de cet exemple à partir des [exemples de code pour développeur](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Pour configurer le projet  
  
1. Pour configurer une application WPF, effectuez les étapes suivantes. Vous trouverez des instructions détaillées pour ces étapes dans [Procédure pas à pas : accès au web avec Async et Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Créez une application WPF qui contient une zone de texte et un bouton. Nommez le bouton `startButton` et la zone de texte `resultsTextBox`.  
  
    - Ajoutez une référence pour <xref:System.Net.Http>.  
  
    - Dans le fichier MainWindow.xaml.cs, ajoutez une directive `using` pour `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Pour ajouter le code  
  
1. Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton pour créer le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.  
  
2. Copiez le code suivant et collez-le dans le corps de `startButton_Click` dans MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, qui pilote l’application.  
  
3. Ajoutez les méthodes de prise en charge suivantes au projet :  
  
    - `ProcessURLAsync` utilise une méthode <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web sous la forme d’un tableau d’octets. La méthode de prise en charge, `ProcessURLAsync`, affiche et retourne ensuite la longueur du tableau.  
  
    - `DisplayResults` affiche le nombre d’octets dans le tableau d’octets pour chaque URL. Cet affichage indique quand le téléchargement de chaque tâche est terminé.  
  
     Copiez les méthodes suivantes et collez-les après le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.  
  
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
  
4. Pour finir, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.  
  
    - La méthode déclare un objet `HttpClient`, dont vous avez besoin pour accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dans `ProcessURLAsync`.  
  
    - La méthode crée et démarre trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier. À mesure que chaque tâche se termine, `DisplayResults` affiche son URL et la longueur du contenu téléchargé. Les tâches s’exécutant de façon asynchrone, l’ordre d’affichage des résultats peut différer de celui dans lequel les tâches ont été déclarées.  
  
    - La méthode attend l’achèvement de chaque tâche. Chaque opérateur `await` suspend l’exécution de `CreateMultipleTasksAsync` jusqu’à la fin de la tâche attendue. L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.  
  
    - Une fois les tâches terminées et les valeurs entières récupérées, la méthode additionne les longueurs des sites web et affiche le résultat.  
  
     Copiez la méthode suivante et collez-la dans votre solution.  
  
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
  
5. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.  
  
     Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminent pas toujours dans le même ordre, et que l’ordre dans lequel elles se terminent n’est pas nécessairement celui dans lequel elles sont créées et attendues.  
  
## <a name="example"></a> Exemple  
 Le code suivant contient l’exemple complet.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programmation asynchrone avec Async et Await (C#)](./index.md)
- [Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
