---
title: 'Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 616efca79312883f17ba837d17a5ee9c97d15b34
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346150"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)

Dans une méthode asynchrone, les tâches sont démarrées quand elles sont créées. The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes. Souvent, une tâche est attendue dès sa création, comme le montre l’exemple suivant.

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

Toutefois, vous pouvez séparer la création de la tâche de son attente si votre programme doit accomplir d’autres tâches qui ne dépendent pas de l’achèvement de la tâche.

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

Entre le démarrage d’une tâche et le moment où elle est attendue, vous pouvez démarrer d’autres tâches. Les tâches supplémentaires s’exécutent implicitement en parallèle, mais aucun thread supplémentaire n’est créé.

Le programme suivant démarre trois téléchargements web asynchrones, puis les attend dans l’ordre dans lequel ils sont appelés. Notez que quand vous exécutez le programme, les tâches ne se terminent pas toujours dans l’ordre dans lequel elles sont créées et attendues. Elles commencent à s’exécuter quand elles sont créées, et une ou plusieurs d’entre elles peuvent se terminer avant que la méthode n’atteigne les expressions await.

> [!NOTE]
> Pour mener à bien ce projet, Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.

For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

Vous pouvez télécharger le code de cet exemple à partir des [exemples de code pour développeur](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).

### <a name="to-set-up-the-project"></a>Pour configurer le projet

1. Pour configurer une application WPF, effectuez les étapes suivantes. You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Créez une application WPF qui contient une zone de texte et un bouton. Nommez le bouton `startButton` et la zone de texte `resultsTextBox`.

    - Ajoutez une référence pour <xref:System.Net.Http>.

    - In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.

### <a name="to-add-the-code"></a>Pour ajouter le code

1. In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.

2. Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, qui pilote l’application.

3. Ajoutez les méthodes de prise en charge suivantes au projet :

    - `ProcessURLAsync` utilise une méthode <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web sous la forme d’un tableau d’octets. La méthode de prise en charge, `ProcessURLAsync`, affiche et retourne ensuite la longueur du tableau.

    - `DisplayResults` affiche le nombre d’octets dans le tableau d’octets pour chaque URL. Cet affichage indique quand le téléchargement de chaque tâche est terminé.

     Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. Pour finir, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.

    - La méthode déclare un objet `HttpClient`, dont vous avez besoin pour accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dans `ProcessURLAsync`.

    - La méthode crée et démarre trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier. À mesure que chaque tâche se termine, `DisplayResults` affiche son URL et la longueur du contenu téléchargé. Les tâches s’exécutant de façon asynchrone, l’ordre d’affichage des résultats peut différer de celui dans lequel les tâches ont été déclarées.

    - La méthode attend l’achèvement de chaque tâche. Chaque opérateur `Await` suspend l’exécution de `CreateMultipleTasksAsync` jusqu’à la fin de la tâche attendue. L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.

    - Une fois les tâches terminées et les valeurs entières récupérées, la méthode additionne les longueurs des sites web et affiche le résultat.

     Copiez la méthode suivante et collez-la dans votre solution.

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

     Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminent pas toujours dans le même ordre, et que l’ordre dans lequel elles se terminent n’est pas nécessairement celui dans lequel elles sont créées et attendues.

## <a name="example"></a>Exemple

Le code suivant contient l’exemple complet.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
