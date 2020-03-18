---
title: 'Procédure pas à pas : accès au web avec Async et Await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281781"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Procédure pas à pas : accès au web avec Async et Await (C#)

Vous pouvez écrire des programmes asynchrones plus facilement et intuitivement en utilisant les fonctionnalités async/await. Vous pouvez écrire du code asynchrone qui ressemble au code synchrone et laisser le compilateur gérer les difficiles fonctions de rappel et continuations qu’implique généralement le code asynchrone.

Pour plus d’informations sur la fonctionnalité Async, consultez [Programmation asynchrone avec Async et Await (C#)](./index.md).

Cette procédure pas à pas commence avec une application Windows Presentation Foundation (WPF) synchrone qui additionne le nombre d’octets figurant dans une liste de sites web. La procédure pas à pas convertit ensuite l’application en solution asynchrone en utilisant les nouvelles fonctionnalités.

Si vous ne souhaitez pas générer les applications vous-même, vous pouvez télécharger [Exemple Async : accès à la procédure web (C# et Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.

## <a name="create-a-wpf-application"></a>Créer une application WPF

1. Démarrez Visual Studio.

2. Sur la barre de menu, choisissez **File** > **New** > **Project**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **Modèles installés**, choisissez Visual C#, puis **Application WPF** dans la liste des types de projets.

4. Dans la zone de texte **Nom**, entrez `AsyncExampleWPF`, puis choisissez le bouton **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

## <a name="design-a-simple-wpf-mainwindow"></a>Concevoir une simple fenêtre MainWindow WPF

1. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

2. Si la fenêtre **Boîte à outils** n’est pas visible, ouvrez le menu **Affichage**, puis choisissez **Boîte à outils**.

3. Ajoutez un contrôle **Button** et un contrôle **TextBox** à la fenêtre **MainWindow**.

4. Mettez en surbrillance le contrôle **TextBox** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :

    - Affectez la valeur `resultsTextBox` à la propriété **Name**.

    - Affectez la valeur 250 à la propriété **Height**.

    - Affectez la valeur 500 à la propriété **Width**.

    - Sous l’onglet **Texte**, spécifiez une police à espacement fixe, comme Lucida Console ou Global Monospace.

5. Mettez en surbrillance le contrôle **Button** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :

    - Affectez la valeur `startButton` à la propriété **Name**.

    - Remplacez la valeur **Button** de la propriété **Content** par **Démarrer**.

6. Placez la zone de texte et le bouton de manière à ce qu’ils apparaissent tous les deux dans la fenêtre **MainWindow**.

     Pour plus d’informations sur le concepteur XAML WPF, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Ajouter une référence

1. Dans l’**Explorateur de solutions**, mettez en surbrillance le nom de votre projet.

2. Sur la barre de menu, choisissez **Project** > **Add Reference**.

     La boîte de dialogue **Gestionnaire de références** s’affiche.

3. En haut de la boîte de dialogue, vérifiez que votre projet cible .NET Framework 4.5 ou version ultérieure.

4. Dans la catégorie **Assemblys**, choisissez **Framework** s’il n’est pas déjà sélectionné.

5. Dans la liste de noms, cochez la case **System.Net.Http**.

6. Choisissez le bouton **OK** pour fermer la boîte de dialogue.

## <a name="add-necessary-using-directives"></a>Ajouter les directives using nécessaires

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.

2. Ajoutez les directives `using` suivantes en haut du fichier de code, si elles ne sont pas déjà présentes.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Créer une application synchrone

1. Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton **Démarrer** pour créer le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.

2. Dans MainWindow.xaml.cs, copiez le code suivant dans le corps de `startButton_Click` :

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Le code appelle la méthode qui pilote l'application, `SumPageSizes`, et affiche un message quand le contrôle redevient `startButton_Click`.

3. Le code de la solution synchrone contient les quatre méthodes suivantes :

    - `SumPageSizes`, qui obtient la liste des URL des pages web à partir de `SetUpURLList`, puis qui appelle `GetURLContents` et `DisplayResults` pour traiter chaque URL.

    - `SetUpURLList`, qui dresse et retourne la liste des adresses web.

    - `GetURLContents`, qui télécharge le contenu de chaque site web et retourne le contenu sous la forme d'un tableau d'octets.

    - `DisplayResults`, qui affiche le nombre d'octets dans le tableau d'octets pour chaque URL.

    Copiez les quatre méthodes suivantes, puis collez-les sous le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs :

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
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
    ```

## <a name="test-the-synchronous-solution"></a>Tester la solution synchrone

Appuyez sur la touche **F5** pour exécuter le programme, puis choisissez le bouton **Démarrer**.

Une sortie semblable à la liste suivante doit apparaître :

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

Notez que quelques secondes suffisent pour afficher les nombres. Pendant ce temps, le thread d'interface utilisateur est bloqué alors qu'il attend que les ressources demandées se téléchargent. Par conséquent, vous ne pouvez pas déplacer, agrandir, réduire ni même fermer la fenêtre d’affichage une fois que vous avez choisi le bouton **Démarrer**. Ces efforts échouent jusqu'à ce que les nombres d'octets commencent à apparaître. Si un site web ne répond pas, vous n'avez aucune indication précise sur le site en question qui a échoué. Il est même difficile d'arrêter l'attente et de fermer le programme.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Convertir GetURLContents en méthode asynchrone

1. Pour convertir la solution synchrone en solution asynchrone, `GetURLContents` est le meilleur point de départ, car les appels à la méthode <xref:System.Net.HttpWebRequest><xref:System.Net.HttpWebRequest.GetResponse%2A> et à la méthode <xref:System.IO.Stream><xref:System.IO.Stream.CopyTo%2A> se trouvent là où l’application accède au web. Le .NET Framework facilite la conversion en fournissant des versions asynchrones des deux méthodes.

     Pour plus d'informations sur les méthodes utilisées dans `GetURLContents`, consultez <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Quand vous suivez les étapes décrites dans cette procédure pas à pas, plusieurs erreurs de compilation apparaissent. Vous pouvez les ignorer et poursuivre la procédure.

     Remplacez la méthode appelée à la troisième ligne de `GetURLContents` dont la valeur est `GetResponse` par la méthode <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchrone basée sur les tâches.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync` retourne un <xref:System.Threading.Tasks.Task%601>. Dans ce cas, la `TResult`variable de <xref:System.Net.WebResponse>retour *de tâche*, , a type . La tâche est une promesse de produire un objet `WebResponse` réel une fois que les données demandées ont été téléchargées et que la tâche s'est exécutée entièrement.

     Pour récupérer la valeur `WebResponse` de la tâche, appliquez un opérateur [await](../../../language-reference/operators/await.md) à l’appel à `GetResponseAsync`, comme le montre le code suivant.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     L’opérateur `await` suspend l’exécution de la méthode actuelle, `GetURLContents`, jusqu’à ce que la tâche attendue soit terminée. Entre-temps, le contrôle retourne à l'appelant de la méthode actuelle. Dans cet exemple, la méthode actuelle est `GetURLContents` et l'appelant est `SumPageSizes`. Quand la tâche est terminée, l'objet `WebResponse` promis est produit sous forme de valeur de la tâche attendue et assigné à la variable `response`.

     L'instruction précédente peut être divisée en deux instructions suivantes pour clarifier ce qui se passe.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     L'appel à `webReq.GetResponseAsync` retourne un `Task(Of WebResponse)` ou `Task<WebResponse>`. Un opérateur await est alors appliqué à la tâche pour récupérer la valeur `WebResponse`.

     Si votre méthode async a un travail à effectuer qui ne dépend pas de la complétion de la tâche, elle peut poursuivre ce travail entre ces deux instructions, après l’appel à la méthode async et avant l’application de l’opérateur `await`. Pour des exemples, voir [Comment faire plusieurs demandes web en parallèle en utilisant async et attendre (C)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) et Comment [étendre la procédure pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Comme vous avez ajouté l’opérateur `await` à l’étape précédente, une erreur de compilation se produit. L’opérateur peut être utilisé uniquement dans les méthodes marquées avec le modificateur [async](../../../language-reference/keywords/async.md). Ignorez l'erreur quand que vous répétez les étapes de conversion pour remplacer l'appel à `CopyTo` par un appel à `CopyToAsync`.

    - Remplacez le nom de la méthode appelée par <xref:System.IO.Stream.CopyToAsync%2A>.

    - La méthode `CopyTo` ou `CopyToAsync` copie les octets dans son argument, `content`, et ne retourne pas de valeur significative. Dans la version synchrone, l'appel à `CopyTo` est une simple instruction qui ne retourne aucune valeur. La version asynchrone, `CopyToAsync`, retourne un <xref:System.Threading.Tasks.Task>. La tâche fonctionne comme Task(void) et permet à la méthode d'être attendue. Appliquez `Await` ou `await` à l'appel à `CopyToAsync`, comme le montre le code suivant.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         L'instruction précédente abrège les deux lignes de code suivantes.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. Tout ce qui reste à faire dans `GetURLContents` consiste à adapter la signature de la méthode. L’opérateur `await` peut être utilisé uniquement dans les méthodes marquées avec le modificateur [async](../../../language-reference/keywords/async.md). Ajoutez le modificateur pour marquer la méthode en tant que *méthode async*, comme le montre le code suivant.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Le type de retour d’une méthode async peut uniquement être <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `void` en C#. En règle générale, le type de retour `void` est utilisé uniquement dans un gestionnaire d’événements asynchrones, où `void` est obligatoire. Dans d’autres cas, vous utilisez `Task(T)` si la méthode exécutée comporte une instruction [return](../../../language-reference/keywords/return.md) qui retourne une valeur de type T et vous utilisez `Task` si la méthode exécutée ne retourne aucune valeur significative. Vous pouvez considérer que le type de retour `Task` signifie Task(void).

     Pour plus d’informations, consultez [Types de retour Async (C#)](./async-return-types.md).

     La méthode `GetURLContents` comporte une instruction return et l'instruction retourne un tableau d'octets. Ainsi, le type de retour de la version asynchrone est Task(T), où T est un tableau d'octets. Apportez les modifications suivantes dans la signature de la méthode :

    - Remplacez le type de retour par `Task<byte[]>`.

    - Par convention, les méthodes asynchrones portent des noms qui se terminent par « Async ». Renommez alors la méthode `GetURLContentsAsync`.

     Le code suivant illustre ces modifications.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Avec ces quelques modifications, la conversion de `GetURLContents` en méthode asynchrone est terminée.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Convertir SumPageSizes en méthode asynchrone

1. Répétez les étapes de la procédure précédente pour `SumPageSizes`. Tout d'abord, modifiez l'appel à `GetURLContents` en appel asynchrone.

    - Remplacez le nom de la méthode appelée `GetURLContents` par `GetURLContentsAsync`, si vous ne l'avez pas déjà fait.

    - Appliquez `await` à la tâche que `GetURLContentsAsync` retourne pour obtenir la valeur du tableau d’octets.

     Le code suivant illustre ces modifications.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     L'instruction précédente abrège les deux lignes de code suivantes.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. Apportez les modifications suivantes dans la signature de la méthode :

    - Marquez la méthode avec le modificateur `async`.

    - Ajoutez « Async » au nom de la méthode.

    - Il n’y a pas de `SumPageSizesAsync` variable de retour de tâches, T, `return` cette fois parce que ne retourne pas une valeur pour T. (La méthode n’a pas de déclaration.) Cependant, la méthode `Task` doit retourner un pour être attendable. Par conséquent, remplacez le type de retour de la méthode `void` par `Task`.

    Le code suivant illustre ces modifications.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     La conversion de `SumPageSizes` en `SumPageSizesAsync` est terminée.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Convertir startButton_Click en méthode asynchrone

1. Dans le gestionnaire d'événements, remplacez le nom de la méthode appelée `SumPageSizes` par `SumPageSizesAsync`, si vous ne l'avez pas déjà fait.

2. Étant donné que `SumPageSizesAsync` est une méthode async, modifiez le code dans le gestionnaire d'événements de sorte à attendre le résultat.

     L'appel à `SumPageSizesAsync` reflète l'appel à `CopyToAsync` dans `GetURLContentsAsync`. L'appel retourne un `Task`, et non un `Task(T)`.

     Comme dans les procédures précédentes, vous pouvez convertir l'appel à l'aide d'une ou deux instructions. Le code suivant illustre ces modifications.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. Pour empêcher une nouvelle entrée accidentelle de l’opération, ajoutez l’instruction suivante en haut de `startButton_Click` pour désactiver le bouton **Démarrer**.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Vous pouvez réactiver le bouton à la fin du gestionnaire d'événements.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Pour plus d’informations sur la réentrance, consultez [Gestion de la réentrance dans les applications asynchrones (C#)](./handling-reentrancy-in-async-apps.md).

4. Enfin, ajoutez le modificateur `async` à la déclaration pour que le gestionnaire d’événements puisse attendre `SumPagSizesAsync`.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     En règle générale, les noms des gestionnaires d'événements ne sont pas modifiés. Le type de retour n’est pas remplacé par `Task`, car les gestionnaires d’événements doivent retourner `void`.

     La conversion du projet depuis un traitement synchrone vers un traitement asynchrone est terminée.

## <a name="test-the-asynchronous-solution"></a>Tester la solution asynchrone

1. Appuyez sur la touche **F5** pour exécuter le programme, puis choisissez le bouton **Démarrer**.

2. Une sortie semblable à la sortie de la solution synchrone doit apparaître. En revanche, observez les différences ci-après.

    - Les résultats ne se produisent pas tous en même temps, une fois le traitement terminé. Par exemple, les deux programmes contiennent une ligne dans `startButton_Click` qui efface la zone de texte. L’objectif est d’effacer la zone de texte entre les exécutions si vous choisissez le bouton **Démarrer** une deuxième fois, une fois qu’un jeu de résultats est apparu. Dans la version synchrone, la zone de texte s’efface juste avant que les nombres n’apparaissent pour la deuxième fois, quand les téléchargements sont terminés et que le thread d’interface utilisateur est libre d’effectuer autre chose. Dans la version asynchrone, la zone de texte s’efface immédiatement après avoir choisi le bouton **Démarrer**.

    - Plus important encore, le thread d'interface utilisateur n'est pas bloqué pendant les téléchargements. Vous pouvez déplacer ou redimensionner la fenêtre pendant le téléchargement, la comptabilisation et l'affichage des ressources web. Si l’un des sites web est lent ou ne répond pas, vous pouvez annuler l’opération en choisissant le bouton **Fermer** (le x dans le champ rouge situé dans le coin supérieur droit).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Remplacer la méthode GetURLContentsAsync par une méthode .NET Framework

1. Le .NET Framework 4.5 propose de nombreuses méthodes async que vous pouvez utiliser. L'une d'entre elles, la méthode <xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, convient parfaitement à cette procédure pas à pas. Vous pouvez l'utiliser à la place de la méthode `GetURLContentsAsync` que vous avez créée précédemment.

     La première étape consiste à créer un objet `HttpClient` dans la méthode `SumPageSizesAsync`. Ajoutez la déclaration suivante au début de la méthode.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. Dans `SumPageSizesAsync,`, remplacez l'appel à votre méthode `GetURLContentsAsync` par un appel à la méthode `HttpClient`.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Supprimez ou commentez la méthode `GetURLContentsAsync` que vous avez écrite.

4. Appuyez sur la touche **F5** pour exécuter le programme, puis choisissez le bouton **Démarrer**.

     Le comportement de cette version du projet doit correspondre à celui décrit par la procédure « Pour tester la solution asynchrone » mais avec encore moins d'efforts de votre part.

## <a name="example-code"></a>Exemple de code

Le code suivant inclut l'exemple complet de la conversion d'une solution synchrone en solution asynchrone à l'aide de la méthode `GetURLContentsAsync` asynchrone que vous avez écrite. Remarquez qu’il ressemble fortement à la solution synchrone d’origine.

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
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

Le code suivant inclut l'exemple complet de la solution qui utilise la méthode `HttpClient`, `GetByteArrayAsync`.

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
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

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

- [Exemple Async : Accès à la procédure web (C# et Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [Async](../../../language-reference/keywords/async.md)
- [Attendent](../../../language-reference/operators/await.md)
- [Programmation asynchrone avec Async et Await (C#)](./index.md)
- [Types de retour async (C#)](./async-return-types.md)
- [Programmation asynchrone basée sur les tâches (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Comment étendre la procédure pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Comment faire plusieurs demandes web en parallèle en utilisant async et attendre (C)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
