---
title: Annuler une tâche Asynch ou une liste de tâches
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 932bf46f1e3aee220d0412f1688e961faaef3459
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396699"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>Annuler une tâche Asynch ou une liste de tâches (Visual Basic)

Vous pouvez créer un bouton permettant d’annuler une application asynchrone que vous souhaitez interrompre avant la fin de son exécution. Les exemples de cette rubrique vous montrent comment ajouter un bouton d’annulation à une application qui télécharge du contenu d’un site web ou une liste de sites web.

Les exemples utilisent l’interface utilisateur que décrit pour [ajuster votre application Async (Visual Basic)](fine-tuning-your-async-application.md) .

> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.

## <a name="cancel-a-task"></a><a name="BKMK_CancelaTask"></a> Annuler une tâche

Le premier exemple associe le bouton **Annuler** à une tâche de téléchargement unique. Si vous appuyez sur le bouton pendant que l’application télécharge du contenu, le téléchargement est annulé.

### <a name="downloading-the-example"></a>Téléchargement de l'exemple

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

1. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

2. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.

3. Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningVB.

4. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelATask**, puis choisissez **Définir comme projet de démarrage**.

5. Appuyez sur la touche F5 pour exécuter le projet.

     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.

 Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter les fichiers MainWindow. Xaml. vb à la fin de cette rubrique.

### <a name="building-the-example"></a>Génération de l’exemple

Les modifications suivantes ajoutent un bouton **Annuler** à une application de téléchargement d’un site web. Si vous ne voulez pas télécharger ou générer l’exemple, vous pouvez examiner le produit final dans la section « Exemples complets », à la fin de cette rubrique. Les astérisques signalent les modifications du code.

Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **StarterCode** comme **Projet de démarrage** au lieu de **CancelATask**.

Ajoutez ensuite les modifications suivantes au fichier MainWindow. Xaml. vb de ce projet.

1. Déclarez une variable `CancellationTokenSource`, `cts`, qui se trouve dans la portée de toutes les méthodes qui y accèdent.

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. Ajoutez le gestionnaire d’événements suivant pour le bouton **Annuler**. Le gestionnaire d’événements utilise la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour notifier à `cts` la demande d’annulation de l’utilisateur.

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. Effectuez les modifications suivantes dans le gestionnaire d’événements pour le bouton **Démarrer**, `startButton_Click`.

    - Instanciez le `CancellationTokenSource`, `cts`.

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - Dans l’appel à `AccessTheWebAsync`, qui télécharge le contenu d’un site web spécifié, envoyez la propriété <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> de `cts` comme argument. La propriété `Token` propage le message si l’annulation est demandée. Ajoutez un bloc catch qui affiche un message si l’utilisateur choisit d’annuler l’opération de téléchargement. Le code suivant illustre les modifications.

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. Dans `AccessTheWebAsync`, utilisez la surcharge <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> de la méthode `GetAsync` dans le type <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web. Passez `ct`, le paramètre <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, comme deuxième argument. Le jeton transmet le message si l’utilisateur choisit le bouton **Annuler**.

    Le code suivant illustre les modifications dans `AccessTheWebAsync`.

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. Si vous n’annulez pas le programme, il génère la sortie suivante :

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    Si vous choisissez le bouton **Annuler** avant que le programme n’ait terminé le téléchargement du contenu, le programme génère la sortie suivante :

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><a name="BKMK_CancelaListofTasks"></a> Annuler une liste de tâches

Vous pouvez étendre l’exemple précédent pour annuler de nombreuses tâches à la fois en associant la même instance `CancellationTokenSource` à chaque tâche. Si vous choisissez le bouton **Annuler**, vous annulez toutes les tâches qui ne sont pas encore terminées.

### <a name="downloading-the-example"></a>Téléchargement de l'exemple

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

1. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

2. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.

3. Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningVB.

4. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAListOfTasks**, puis choisissez **Définir comme projet de démarrage**.

5. Appuyez sur la touche F5 pour exécuter le projet.

     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.

 Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter les fichiers MainWindow. Xaml. vb à la fin de cette rubrique.

### <a name="building-the-example"></a>Génération de l’exemple

Pour étendre l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelATask** comme **Projet de démarrage**. Apportez les modifications suivantes au projet. Les astérisques signalent les modifications effectuées dans le programme.

1. Ajoutez une méthode pour créer une liste des adresses web.

    ```vb
    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function
    ```

2. Appelez la méthode dans `AccessTheWebAsync`.

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. Ajoutez la boucle suivante dans `AccessTheWebAsync` pour traiter chaque adresse web dans la liste.

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. Comme `AccessTheWebAsync` affiche les longueurs, la méthode n’a pas besoin de retourner une valeur. Supprimez l’instruction return et changez le type de retour de la méthode de <xref:System.Threading.Tasks.Task> en <xref:System.Threading.Tasks.Task%601>.

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    Appelez la méthode à partir de `startButton_Click` à l’aide d’une instruction au lieu d’une expression.

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. Si vous n’annulez pas le programme, il génère la sortie suivante :

    ```console
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

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><a name="BKMK_CompleteExamples"></a> Exemples complets

Les sections suivantes contiennent le code correspondant à chacun des exemples précédents. Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.

Vous pouvez télécharger les projets à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="cancel-a-task-example"></a>Exemple d’annulation d’une tâche

Le code suivant est le fichier MainWindow. Xaml. vb complet pour l’exemple qui annule une seule tâche.

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a>Exemple d’annulation d’une liste de tâches

Le code suivant est le fichier MainWindow. Xaml. vb complet pour l’exemple qui annule une liste de tâches.

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Programmation asynchrone avec Async et Await (Visual Basic)](index.md)
- [Ajuster une application Async (Visual Basic)](fine-tuning-your-async-application.md)
- [Exemple Async : ajuster une application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
