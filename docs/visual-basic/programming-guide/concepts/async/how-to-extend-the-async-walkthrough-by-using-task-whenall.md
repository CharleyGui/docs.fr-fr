---
title: "Comment : étendre la procédure pas à pas Async à l'aide de Task.WhenAll"
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fb323852c83b1edf51396a0b800c2d54a833d0c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396621"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)

Vous pouvez améliorer les performances de la solution Async dans [procédure pas à pas : accès au Web avec Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) à l’aide de la <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> méthode. Cette méthode attend de manière asynchrone plusieurs opérations, qui sont représentées sous la forme d’une collection de tâches.

Vous aurez peut-être remarqué dans la procédure pas à pas que les sites web se téléchargent à différentes vitesses. L’un des sites web est parfois très lent, ce qui retarde tous les autres téléchargements. Quand vous exécutez les solutions asynchrones que vous générez dans la procédure pas à pas, vous pouvez quitter le programme facilement si vous ne souhaitez pas attendre, mais une meilleure option consiste à démarrer tous les téléchargements en même temps et à laisser les plus rapides se poursuivre sans attendre celui qui est retardé.

Vous appliquez la méthode `Task.WhenAll` à une collection de tâches. L’application de `WhenAll` retourne une tâche unique qui n’est pas terminée tant que toutes les tâches de la collection ne sont pas terminées. Les tâches s’exécutent en parallèle, mais aucun thread supplémentaire n’est créé. Les tâches peuvent se terminer dans n’importe quel ordre.

> [!IMPORTANT]
> Les procédures suivantes décrivent les extensions des applications Async développées dans [procédure pas à pas : accès au Web à l’aide de Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez développer les applications soit en appliquant la procédure pas à pas, soit en téléchargeant le code à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Pour exécuter l’exemple, Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Pour ajouter Task.WhenAll à votre solution GetURLContentsAsync

1. Ajoutez la `ProcessURLAsync` méthode à la première application développée dans [procédure pas à pas : accès au Web à l’aide de Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Si vous avez téléchargé le code à partir des [exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough, puis ajoutez- `ProcessURLAsync` le au fichier MainWindow. Xaml. vb.

    - Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui inclut la méthode `GetURLContentsAsync`. Le fichier MainWindow. Xaml. vb pour cette application est le premier exemple de la section « Exemples de code complets de la procédure pas à pas ».

     La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `For Each` dans `SumPageSizesAsync` dans la procédure d’origine. La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Commentez ou supprimez la boucle `For Each` dans `SumPageSizesAsync`, comme illustré dans le code suivant.

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. Créez une collection de tâches. Le code suivant définit une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web. Les tâches sont démarrées quand la requête est évaluée.

     Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `urlList`.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.

     Dans l’exemple suivant, l’expression `Await` attend l’achèvement de la tâche unique retournée par `WhenAll`. L’expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des longueurs de tous les sites web. Ajoutez la ligne suivante à `SumPageSizesAsync`.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Pour ajouter Task.WhenAll à la solution HttpClient.GetByteArrayAsync

1. Ajoutez la version suivante de `ProcessURLAsync` à la deuxième application développée dans [procédure pas à pas : accès au Web à l’aide de Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Si vous avez téléchargé le code à partir des [exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), ouvrez le projet AsyncWalkthrough_HttpClient, puis ajoutez- `ProcessURLAsync` le au fichier MainWindow. Xaml. vb.

    - Si vous avez développé le code en appliquant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui utilise la méthode `HttpClient.GetByteArrayAsync`. Le fichier MainWindow. Xaml. vb pour cette application est le deuxième exemple de la section « Exemples de code complets de la procédure pas à pas ».

     La méthode `ProcessURLAsync` consolide les actions dans le corps de la boucle `For Each` dans `SumPageSizesAsync` dans la procédure d’origine. La méthode télécharge de façon asynchrone le contenu d’un site web spécifié sous forme de tableau d’octets, puis affiche et retourne la longueur du tableau d’octets.

     La seule différence par rapport à la méthode `ProcessURLAsync` de la procédure précédente est l’utilisation de l’instance <xref:System.Net.Http.HttpClient>, `client`.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Commentez ou supprimez la boucle `For Each` dans `SumPageSizesAsync`, comme illustré dans le code suivant.

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. Définissez une [requête](../linq/index.md) qui, quand elle est exécutée par la méthode <xref:System.Linq.Enumerable.ToArray%2A>, crée une collection de tâches qui téléchargent le contenu de chaque site web. Les tâches sont démarrées quand la requête est évaluée.

     Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `client` et `urlList`.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Ensuite, appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll` retourne une tâche unique qui se termine quand toutes les tâches de la collection de tâches sont terminées.

     Dans l’exemple suivant, l’expression `Await` attend l’achèvement de la tâche unique retournée par `WhenAll`. Une fois cette tâche achevée, l’expression `Await` correspond à un tableau d’entiers, où chaque entier est la longueur d’un site web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code ajouté à l’étape précédente.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Enfin, utilisez la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir la somme des longueurs de tous les sites web. Ajoutez la ligne suivante à `SumPageSizesAsync`.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Pour tester les solutions Task.WhenAll

Pour l’une ou l’autre solution, appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** . La sortie doit ressembler à la sortie des solutions Async dans [procédure pas à pas : accès au Web avec Async et await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md). Toutefois, notez que les sites web apparaissent à chaque fois dans un ordre différent.

## <a name="example"></a>Exemple

Le code suivant montre les extensions du projet qui utilise la méthode `GetURLContentsAsync` pour télécharger du contenu à partir du web.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                ' CopyToAsync returns a Task, not a Task<T>.
                Await responseStream.CopyToAsync(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

## <a name="example"></a>Exemple

Le code suivant montre les extensions du projet qui utilise la méthode `HttpClient.GetByteArrayAsync` pour télécharger du contenu à partir du web.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
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

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
