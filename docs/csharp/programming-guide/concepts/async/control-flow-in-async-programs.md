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
# <a name="control-flow-in-async-programs-c"></a>Flux de contrôle dans les programmes asynchrones (C#)

Vous pouvez écrire et tenir à jour des programmes asynchrones plus facilement à l’aide des mots clés `async` et `await`. Toutefois, les résultats peuvent vous étonner si vous ne comprenez pas le fonctionnement de votre programme. Cette rubrique suit le flux de contrôle par le biais d’un programme asynchrone simple pour vous montrer quand le contrôle se déplace d’une méthode à une autre et quelles informations sont transférées à chaque fois.

En général, vous marquez les méthodes qui contiennent du code asynchrone avec le modificateur [async (C#)](../../../language-reference/keywords/async.md). Dans une méthode marquée avec un modificateur async, vous pouvez utiliser un opérateur [await (C#)](../../../language-reference/operators/await.md) pour spécifier où la méthode s’interrompt afin d’attendre qu’un processus asynchrone appelé s’exécute. Pour plus d’informations, consultez [Programmation asynchrone avec async et await (C#)](./index.md).

L’exemple suivant utilise des méthodes async pour télécharger le contenu d’un site web spécifié sous forme de chaîne et afficher la longueur de la chaîne. Il contient les deux méthodes suivantes.

- `startButton_Click`, qui appelle `AccessTheWebAsync` et affiche le résultat.

- `AccessTheWebAsync`, qui télécharge le contenu d’un site web sous forme de chaîne et retourne la longueur de la chaîne. `AccessTheWebAsync` utilise une méthode asynchrone <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pour télécharger le contenu.

Des lignes numérotées apparaissent à des points stratégiques du programme pour vous aider à comprendre comment le programme s’exécute et expliquer ce qui se produit à chaque point marqué. Les lignes sont étiquetées de "ONE" à "SIX". Les étiquettes représentent l’ordre dans lequel le programme atteint ces lignes de code.

Le code suivant illustre un plan du programme.

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

Chacun des emplacements étiquetés de "ONE" à "SIX" affiche des informations sur l’état actuel du programme. La sortie suivante est produite :

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

## <a name="set-up-the-program"></a>Configurer le programme

Vous pouvez télécharger le code que cette rubrique utilise à partir de MSDN, ou vous pouvez le créer vous-même.

> [!NOTE]
> Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.

### <a name="download-the-program"></a>Télécharger le programme

Vous pouvez télécharger l’application utilisée dans cette rubrique à partir de l’[exemple Async : Flux de contrôle dans les programmes Async](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Les étapes suivantes ouvrent et exécutent le programme.

1. Décompressez le fichier téléchargé, puis démarrez Visual Studio.

2. Dans la barre de menus, choisissez **fichier**  >  **ouvrir**un  >  **projet/une solution**.

3. Accédez au dossier qui contient l’exemple de code décompressé, ouvrez le fichier solution (.sln), puis choisissez la touche **F5** pour générer et exécuter le projet.

### <a name="create-the-program-yourself"></a>Créer le programme vous-même

Le projet Windows Presentation Foundation (WPF) suivant contient l’exemple de code utilisé pour cette rubrique.

Pour exécuter le projet, procédez comme suit :

1. Démarrez Visual Studio.

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Choisissez la catégorie **installé**du  >  Bureau Windows**Visual C#**  >  **Windows Desktop** , puis choisissez **application WPF** dans la liste des modèles de projet.

4. Entrez `AsyncTracer` comme nom du projet, puis choisissez le bouton **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

5. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

     Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.

6. Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.

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

     Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.

7. Ajoutez une référence pour <xref:System.Net.Http>.

8. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.

9. Dans MainWindow.xaml.cs, remplacez le code par le code suivant.

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

10. Appuyez sur la touche **F5** pour exécuter le programme, puis choisissez le bouton **Démarrer**.

    Vous obtenez la sortie suivante :

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

## <a name="trace-the-program"></a>Tracer le programme

### <a name="steps-one-and-two"></a>Étapes UN et DEUX

Les deux premières lignes d’affichage suivent le chemin quand `startButton_Click` appelle `AccessTheWebAsync` et `AccessTheWebAsync` appelle la méthode asynchrone <xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. L’image suivante montre les appels de méthode à méthode.

![Étapes UN et DEUX](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Le type de retour de `AccessTheWebAsync` et de `client.GetStringAsync` est <xref:System.Threading.Tasks.Task%601>. Pour `AccessTheWebAsync`, TResult est un entier. Pour `GetStringAsync`, TResult est une chaîne. Pour plus d’informations sur les types de retour de méthode asynchrone, consultez [Types de retour Async (C#)](./async-return-types.md).

Une méthode async retournant une tâche retourne une instance de tâche quand le contrôle revient vers l’appelant. Le contrôle retourne d’une méthode async à son appelant quand un opérateur `await` est rencontré dans la méthode appelée ou quand la méthode appelée se termine. Les lignes qui sont étiquetées "THREE" à "SIX" suivent cette partie du processus.

### <a name="step-three"></a>Étape TROIS

Dans `AccessTheWebAsync`, la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> est appelée pour télécharger le contenu de la page web cible. Le contrôle retourne de `client.GetStringAsync` à `AccessTheWebAsync` quand `client.GetStringAsync` retourne une sortie.

 La méthode `client.GetStringAsync` retourne une tâche de la chaîne assignée à la variable `getStringTask` dans `AccessTheWebAsync`. La ligne suivante de l’exemple de programme illustre l’appel à `client.GetStringAsync` et l’assignation.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Vous pouvez considérer la tâche comme une promesse faite par `client.GetStringAsync` de produire au final une chaîne réelle. Pour le moment, si `AccessTheWebAsync` a du travail à effectuer qui ne dépend pas de la chaîne promise de `client.GetStringAsync`, ce travail peut se poursuivre pendant que `client.GetStringAsync` attend. Dans l’exemple, les lignes de sortie suivantes, qui sont étiquetées « THREE », représentent la possibilité d’effectuer un travail indépendant

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 L’instruction suivante interrompt la progression dans `AccessTheWebAsync` quand `getStringTask` est attendu.

```csharp
string urlContents = await getStringTask;
```

 L’illustration suivante montre le flux de contrôle entre `client.GetStringAsync` et l’assignation à `getStringTask`, puis entre la création de `getStringTask` et l’application d’un opérateur await.

 ![Étape 3](./media/asynctrace-three.png "AsyncTrace-trois")

 L’expression await suspend `AccessTheWebAsync` jusqu’à ce que `client.GetStringAsync` retourne une sortie. Dans le même temps, le contrôle retourne à l’appelant de `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> En général, vous attendez immédiatement l’appel à une méthode asynchrone. Par exemple, l’assignation suivante peut substituer le code précédent qui crée, puis attend `getStringTask` : `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> Dans cette rubrique, l’opérateur await est appliqué ultérieurement pour s’adapter aux lignes de sortie qui marquent le flux de contrôle dans le programme.

### <a name="step-four"></a>Étape FOUR

Le type de retour déclaré de `AccessTheWebAsync` est `Task<int>`. Par conséquent, quand la méthode `AccessTheWebAsync` est suspendue, elle retourne une tâche d’entier à `startButton_Click`. Vous devez comprendre que la tâche retournée n’est pas `getStringTask`. Il s’agit d’une tâche d’entier qui représente ce qu’il reste à effectuer dans la méthode interrompue, `AccessTheWebAsync`. La tâche est une promesse de `AccessTheWebAsync` de produire un entier quand la tâche est terminée.

L’instruction suivante assigne cette tâche à la variable `getLengthTask`.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Comme dans `AccessTheWebAsync`, `startButton_Click` peut continuer le travail qui ne dépend pas des résultats de la tâche asynchrone (`getLengthTask`) jusqu’à ce que la tâche soit attendue. Les lignes de sortie suivantes représentent ce travail.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 La progression dans `startButton_Click` est suspendue quand `getLengthTask` est attendu. L’instruction d’assignation suivante interrompt `startButton_Click` jusqu’à ce que la méthode `AccessTheWebAsync` soit terminée.

```csharp
int contentLength = await getLengthTask;
```

 Dans l’illustration suivante, les flèches indiquent le flux de contrôle entre l’expression await dans `AccessTheWebAsync` et l’assignation d’une valeur à `getLengthTask`, suivie du traitement normal dans `startButton_Click` jusqu’à ce que `getLengthTask` soit attendu.

 ![Étape 4](./media/asynctrace-four.png "AsyncTrace-quatre")

### <a name="step-five"></a>Étape FIVE

Quand `client.GetStringAsync` signale que son exécution est terminée, le traitement dans `AccessTheWebAsync` est libéré de la suspension et peut continuer après l’instruction await. Les lignes de sortie suivantes représentent la reprise du traitement.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 L’opérande de l’instruction return, `urlContents.Length`, est stocké dans la tâche que `AccessTheWebAsync` retourne. L’expression await récupère cette valeur à partir de `getLengthTask` dans `startButton_Click`.

 L’illustration suivante présente le transfert du contrôle après l’exécution de `client.GetStringAsync` (et de `getStringTask`).

 ![Étape FIVE](./media/asynctrace-five.png "AsyncTrace-cinq")

 `AccessTheWebAsync` s’exécute jusqu’à la fin et le contrôle retourne à `startButton_Click`, qui attend que son exécution soit terminée.

### <a name="step-six"></a>Étape SIX

Quand `AccessTheWebAsync` signale que son exécution est terminée, le traitement peut continuer après l’instruction await dans `startButton_Async`. En fait, le programme n’a plus rien d’autre à faire.

Les lignes de sortie suivantes représentent la reprise du traitement dans `startButton_Async` :

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 L’expression await récupère de `getLengthTask` la valeur entière qui est l’opérande de l’instruction return dans `AccessTheWebAsync`. L’instruction suivante assigne cette valeur à la variable `contentLength`.

```csharp
int contentLength = await getLengthTask;
```

 L’illustration suivante montre le retour du contrôle de `AccessTheWebAsync` à `startButton_Click`.

 ![Étape SIX](./media/asynctrace-six.png "AsyncTrace-SIX")

## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (C#)](./index.md)
- [Types de retour async (C#)](./async-return-types.md)
- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Exemple Async : Flux de contrôle dans les programmes Async (C# et Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
