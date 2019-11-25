---
title: Flux de contrôle dans les programmes Async
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 94b2c2ea89f729e882229d4ecce7faa169c24267
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347944"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Control Flow in Async Programs (Visual Basic)

Vous pouvez écrire et tenir à jour des programmes asynchrones plus facilement à l’aide des mots clés `Async` et `Await`. Toutefois, les résultats peuvent vous étonner si vous ne comprenez pas le fonctionnement de votre programme. Cette rubrique suit le flux de contrôle par le biais d’un programme asynchrone simple pour vous montrer quand le contrôle se déplace d’une méthode à une autre et quelles informations sont transférées à chaque fois.

> [!NOTE]
> Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012.

In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier. In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete. For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

L’exemple suivant utilise des méthodes async pour télécharger le contenu d’un site web spécifié sous forme de chaîne et afficher la longueur de la chaîne. Il contient les deux méthodes suivantes.

- `startButton_Click`, qui appelle `AccessTheWebAsync` et affiche le résultat.

- `AccessTheWebAsync`, qui télécharge le contenu d’un site web sous forme de chaîne et retourne la longueur de la chaîne. `AccessTheWebAsync` utilise une méthode asynchrone <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pour télécharger le contenu.

Des lignes numérotées apparaissent à des points stratégiques du programme pour vous aider à comprendre comment le programme s’exécute et expliquer ce qui se produit à chaque point marqué. Les lignes sont étiquetées de "ONE" à "SIX". Les étiquettes représentent l’ordre dans lequel le programme atteint ces lignes de code.

Le code suivant illustre un plan du programme.

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

Chacun des emplacements étiquetés de "ONE" à "SIX" affiche des informations sur l’état actuel du programme. La sortie suivante est produite :

```console
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
> To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.

### <a name="download-the-program"></a>Télécharger le programme

Vous pouvez télécharger l’application utilisée dans cette rubrique à partir de l’[exemple Async : Flux de contrôle dans les programmes Async](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Les étapes suivantes ouvrent et exécutent le programme.

1. Décompressez le fichier téléchargé, puis démarrez Visual Studio.

2. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.

3. Accédez au dossier qui contient l’exemple de code décompressé, ouvrez le fichier solution (.sln), puis choisissez la touche F5 pour générer et exécuter le projet.

### <a name="build-the-program-yourself"></a>Générer le programme vous-même

Le projet Windows Presentation Foundation (WPF) suivant contient l’exemple de code utilisé pour cette rubrique.

Pour exécuter le projet, procédez comme suit :

1. Démarrez Visual Studio.

2. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.

    La boîte de dialogue **Nouveau projet** s'affiche.

3. In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.

4. Entrez `AsyncTracer` comme nom de projet, puis cliquez sur le bouton **OK**.

    Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

5. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

    Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.

6. Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.

7. Ajoutez une référence pour <xref:System.Net.Http>.

8. In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.

9. In MainWindow.xaml.vb , replace the code with the following code.

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

    The following output should appear:

    ```console
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

Les deux premières lignes d’affichage suivent le chemin quand `startButton_Click` appelle `AccessTheWebAsync` et `AccessTheWebAsync` appelle la méthode asynchrone <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. L’image suivante montre les appels de méthode à méthode.

![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Le type de retour de `AccessTheWebAsync` et de `client.GetStringAsync` est <xref:System.Threading.Tasks.Task%601>. Pour `AccessTheWebAsync`, TResult est un entier. Pour `GetStringAsync`, TResult est une chaîne. For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

Une méthode async retournant une tâche retourne une instance de tâche quand le contrôle revient vers l’appelant. Le contrôle retourne d’une méthode async à son appelant quand un opérateur `Await` est rencontré dans la méthode appelée ou quand la méthode appelée se termine. Les lignes qui sont étiquetées "THREE" à "SIX" suivent cette partie du processus.

### <a name="step-three"></a>Étape TROIS

Dans `AccessTheWebAsync`, la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> est appelée pour télécharger le contenu de la page web cible. Le contrôle retourne de `client.GetStringAsync` à `AccessTheWebAsync` quand `client.GetStringAsync` retourne une sortie.

La méthode `client.GetStringAsync` retourne une tâche de la chaîne assignée à la variable `getStringTask` dans `AccessTheWebAsync`. La ligne suivante de l’exemple de programme illustre l’appel à `client.GetStringAsync` et l’assignation.

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Vous pouvez considérer la tâche comme une promesse faite par `client.GetStringAsync` de produire au final une chaîne réelle. Pour le moment, si `AccessTheWebAsync` a du travail à effectuer qui ne dépend pas de la chaîne promise de `client.GetStringAsync`, ce travail peut se poursuivre pendant que `client.GetStringAsync` attend. Dans l’exemple, les lignes de sortie suivantes, qui sont étiquetées « THREE », représentent la possibilité d’effectuer un travail indépendant

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 L’instruction suivante interrompt la progression dans `AccessTheWebAsync` quand `getStringTask` est attendu.

```vb
Dim urlContents As String = Await getStringTask
```

The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.

![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")

L’expression await suspend `AccessTheWebAsync` jusqu’à ce que `client.GetStringAsync` retourne une sortie. Dans le même temps, le contrôle retourne à l’appelant de `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> En général, vous attendez immédiatement l’appel à une méthode asynchrone. Par exemple, l’assignation suivante peut substituer le code précédent qui crée, puis attend `getStringTask` : `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> Dans cette rubrique, l’opérateur await est appliqué ultérieurement pour s’adapter aux lignes de sortie qui marquent le flux de contrôle dans le programme.

### <a name="step-four"></a>Étape FOUR

Le type de retour déclaré de `AccessTheWebAsync` est `Task(Of Integer)`. Par conséquent, quand la méthode `AccessTheWebAsync` est suspendue, elle retourne une tâche d’entier à `startButton_Click`. Vous devez comprendre que la tâche retournée n’est pas `getStringTask`. Il s’agit d’une tâche d’entier qui représente ce qu’il reste à effectuer dans la méthode interrompue, `AccessTheWebAsync`. La tâche est une promesse de `AccessTheWebAsync` de produire un entier quand la tâche est terminée.

L’instruction suivante assigne cette tâche à la variable `getLengthTask`.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

Comme dans `AccessTheWebAsync`, `startButton_Click` peut continuer le travail qui ne dépend pas des résultats de la tâche asynchrone (`getLengthTask`) jusqu’à ce que la tâche soit attendue. The following output lines represent that work:

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

La progression dans `startButton_Click` est suspendue quand `getLengthTask` est attendu. L’instruction d’assignation suivante interrompt `startButton_Click` jusqu’à ce que la méthode `AccessTheWebAsync` soit terminée.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Dans l’illustration suivante, les flèches indiquent le flux de contrôle entre l’expression await dans `AccessTheWebAsync` et l’assignation d’une valeur à `getLengthTask`, suivie du traitement normal dans `startButton_Click` jusqu’à ce que `getLengthTask` soit attendu.

![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")

### <a name="step-five"></a>Étape FIVE

Quand `client.GetStringAsync` signale que son exécution est terminée, le traitement dans `AccessTheWebAsync` est libéré de la suspension et peut continuer après l’instruction await. The following lines of output represent the resumption of processing:

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

L’opérande de l’instruction return, `urlContents.Length`, est stocké dans la tâche que `AccessTheWebAsync` retourne. L’expression await récupère cette valeur à partir de `getLengthTask` dans `startButton_Click`.

L’illustration suivante présente le transfert du contrôle après l’exécution de `client.GetStringAsync` (et de `getStringTask`).

![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")

`AccessTheWebAsync` s’exécute jusqu’à la fin et le contrôle retourne à `startButton_Click`, qui attend que son exécution soit terminée.

### <a name="step-six"></a>Étape SIX

Quand `AccessTheWebAsync` signale que son exécution est terminée, le traitement peut continuer après l’instruction await dans `startButton_Async`. En fait, le programme n’a plus rien d’autre à faire.

Les lignes de sortie suivantes représentent la reprise du traitement dans `startButton_Async` :

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

L’expression await récupère de `getLengthTask` la valeur entière qui est l’opérande de l’instruction return dans `AccessTheWebAsync`. L’instruction suivante assigne cette valeur à la variable `contentLength`.

```vb
Dim contentLength As Integer = Await getLengthTask
```

L’illustration suivante montre le retour du contrôle de `AccessTheWebAsync` à `startButton_Click`.

![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")

## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Exemple Async : Flux de contrôle dans les programmes Async (C# et Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
