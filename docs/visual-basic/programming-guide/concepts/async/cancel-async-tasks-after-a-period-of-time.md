---
title: Annuler des tâches Asynch après une période spécifique
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 048d4c19d459905ea579ede96c69230e718d55aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396686"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>Annuler des tâches Asynch après une période spécifique (Visual Basic)

Si vous ne souhaitez pas attendre la fin d’une opération asynchrone, vous pouvez l’annuler après une période spécifique à l’aide de la méthode <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>. Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées au terme de la période indiquée par l’expression `CancelAfter`.

Cet exemple s’appuie sur le code développé dans [Annuler une tâche asynchrone ou une liste de tâches (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites web et afficher la longueur du contenu de chacun d’eux.

> [!NOTE]
> Pour exécuter les exemples, Visual Studio 2012 ou ultérieur et .NET Framework 4.5 ou ultérieur doivent être installés sur votre ordinateur.

## <a name="downloading-the-example"></a>Téléchargement de l'exemple

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

1. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

2. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.

3. Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningVB.

4. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterTime**, puis choisissez **Définir comme projet de démarrage**.

5. Appuyez sur la touche F5 pour exécuter le projet.

     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.

6. Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.

 Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.vb à la fin de cette rubrique.

## <a name="building-the-example"></a>Génération de l’exemple

L’exemple de cette rubrique s’appuie sur le projet développé dans [Annuler une tâche asynchrone ou une liste de tâches (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches. Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.

Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**. Ajoutez les changements de cette rubrique à ce projet.

Pour spécifier une durée maximale avant que les tâches ne soient marquées comme annulées, ajoutez un appel à `CancelAfter` à `startButton_Click`, comme l’illustre l’exemple suivant. L’ajout est signalé par des astérisques.

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web. La sortie suivante est un exemple :

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Exemple complet

Le code suivant est le texte complet du fichier MainWindow.xaml.vb de l’exemple. Des astérisques marquent les éléments ajoutés pour cet exemple.

Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.

Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' Add a method that creates a list of web addresses.
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

' Sample output:

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (Visual Basic)](index.md)
- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Annuler une tâche Asynch ou une liste de tâches (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)
- [Ajuster une application Async (Visual Basic)](fine-tuning-your-async-application.md)
- [Exemple Async : ajuster une application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
