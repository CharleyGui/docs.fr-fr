---
title: 'Procédure pas à pas : accès au Web avec Async et Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 41ededd4d4335b78b8d7a33e8fe387c7d632cbee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400743"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Procédure pas à pas : accès au web avec Async et Await (Visual Basic)

Vous pouvez écrire des programmes asynchrones plus facilement et intuitivement en utilisant les fonctionnalités async/await. Vous pouvez écrire du code asynchrone qui ressemble au code synchrone et laisser le compilateur gérer les difficiles fonctions de rappel et continuations qu’implique généralement le code asynchrone.

Pour plus d’informations sur la fonctionnalité Async, consultez [programmation asynchrone avec Async et await (Visual Basic)](index.md).

Cette procédure pas à pas commence avec une application Windows Presentation Foundation (WPF) synchrone qui additionne le nombre d’octets figurant dans une liste de sites web. La procédure pas à pas convertit ensuite l’application en solution asynchrone en utilisant les nouvelles fonctionnalités.

Si vous ne souhaitez pas générer les applications vous-même, vous pouvez télécharger « Exemple Async : Accès à la procédure web (C# et Visual Basic) » à partir des [exemples de code de développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

Dans cette procédure pas à pas, vous effectuez les tâches suivantes :

> [!div class="checklist"]
>
> - [Créer une application WPF](#create-a-wpf-application)
> - [Concevoir une simple fenêtre MainWindow WPF](#design-a-simple-wpf-mainwindow)
> - [Ajouter une référence](#add-a-reference)
> - [Ajouter les instructions Imports nécessaires](#add-necessary-imports-statements)
> - [Créer une application synchrone](#create-a-synchronous-application)
> - [Tester la solution synchrone](#test-the-synchronous-solution)
> - [Convertir GetURLContents en méthode asynchrone](#convert-geturlcontents-to-an-asynchronous-method)
> - [Convertir SumPageSizes en méthode asynchrone](#convert-sumpagesizes-to-an-asynchronous-method)
> - [Convertir startButton_Click en méthode asynchrone](#convert-startbutton_click-to-an-asynchronous-method)
> - [Tester la solution asynchrone](#test-the-asynchronous-solution)
> - [Remplacer la méthode GetURLContentsAsync par une méthode .NET Framework](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

Consultez la section [exemple](#example) pour obtenir un exemple asynchrone complet.

## <a name="prerequisites"></a>Prérequis

Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur. Pour plus d’informations, consultez la page [téléchargements](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) Visual Studio.

## <a name="create-a-wpf-application"></a>Créer une application WPF

1. Démarrez Visual Studio.

2. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.

    La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **modèles installés** , choisissez Visual Basic, puis choisissez **application WPF** dans la liste des types de projets.

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

2. Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.

    La boîte de dialogue **Gestionnaire de références** s’affiche.

3. En haut de la boîte de dialogue, vérifiez que votre projet cible .NET Framework 4.5 ou version ultérieure.

4. Dans la zone **Assemblys**, choisissez **Framework** s’il n’est pas déjà sélectionné.

5. Dans la liste de noms, cochez la case **System.Net.Http**.

6. Choisissez le bouton **OK** pour fermer la boîte de dialogue.

## <a name="add-necessary-imports-statements"></a>Ajouter les instructions Imports nécessaires

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel de MainWindow. Xaml. vb, puis choisissez **afficher le code**.

2. Ajoutez les `Imports` instructions suivantes en haut du fichier de code, si elles ne sont pas déjà présentes.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Créer une application synchrone

1. Dans la fenêtre de conception, MainWindow. xaml, double-cliquez sur le bouton **Démarrer** pour créer le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb.

2. Dans MainWindow. Xaml. vb, copiez le code suivant dans le corps de `startButton_Click` :

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    Le code appelle la méthode qui pilote l'application, `SumPageSizes`, et affiche un message quand le contrôle redevient `startButton_Click`.

3. Le code de la solution synchrone contient les quatre méthodes suivantes :

    - `SumPageSizes`, qui obtient la liste des URL des pages web à partir de `SetUpURLList`, puis qui appelle `GetURLContents` et `DisplayResults` pour traiter chaque URL.

    - `SetUpURLList`, qui dresse et retourne la liste des adresses web.

    - `GetURLContents`, qui télécharge le contenu de chaque site web et retourne le contenu sous la forme d'un tableau d'octets.

    - `DisplayResults`, qui affiche le nombre d'octets dans le tableau d'octets pour chaque URL.

    Copiez les quatre méthodes suivantes, puis collez-les sous le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb :

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
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
    ```

## <a name="test-the-synchronous-solution"></a>Tester la solution synchrone

1. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

    Une sortie semblable à la liste suivante doit apparaître :

    ```console
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

1. Pour convertir la solution synchrone en solution asynchrone, le meilleur point de départ est de faire en sorte `GetURLContents` que les appels à la <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> méthode et à la <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> méthode se trouvent là où l’application accède au Web. Le .NET Framework facilite la conversion en fournissant des versions asynchrones des deux méthodes.

    Pour plus d'informations sur les méthodes utilisées dans `GetURLContents`, consultez <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Quand vous suivez les étapes décrites dans cette procédure pas à pas, plusieurs erreurs de compilation apparaissent. Vous pouvez les ignorer et poursuivre la procédure.

    Remplacez la méthode appelée à la troisième ligne de `GetURLContents` dont la valeur est `GetResponse` par la méthode <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchrone basée sur les tâches.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` retourne un <xref:System.Threading.Tasks.Task%601>. Dans ce cas, la *variable de retour de tâche*, `TResult` , est de type <xref:System.Net.WebResponse> . La tâche est une promesse de produire un objet `WebResponse` réel une fois que les données demandées ont été téléchargées et que la tâche s'est exécutée entièrement.

    Pour récupérer la `WebResponse` valeur de la tâche, appliquez un opérateur [await](../../../language-reference/operators/await-operator.md) à l’appel à `GetResponseAsync` , comme le montre le code suivant.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    L’opérateur `Await` suspend l’exécution de la méthode actuelle, `GetURLContents`, jusqu’à ce que la tâche attendue soit terminée. Entre-temps, le contrôle retourne à l'appelant de la méthode actuelle. Dans cet exemple, la méthode actuelle est `GetURLContents` et l'appelant est `SumPageSizes`. Quand la tâche est terminée, l'objet `WebResponse` promis est produit sous forme de valeur de la tâche attendue et assigné à la variable `response`.

    L'instruction précédente peut être divisée en deux instructions suivantes pour clarifier ce qui se passe.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    L'appel à `webReq.GetResponseAsync` retourne un `Task(Of WebResponse)` ou `Task<WebResponse>`. Un `Await` opérateur est ensuite appliqué à la tâche pour récupérer la `WebResponse` valeur.

    Si votre méthode async a un travail à effectuer qui ne dépend pas de l'achèvement de la tâche, elle peut poursuivre ce travail entre ces deux instructions, après l'appel à la méthode async et avant l'application de l'opérateur await. Pour obtenir des exemples, consultez [Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) et [Comment : étendre la procédure pas à pas Async à l’aide de Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Comme vous avez ajouté l’opérateur `Await` à l’étape précédente, une erreur de compilation se produit. L’opérateur peut être utilisé uniquement dans les méthodes marquées avec le modificateur [Async](../../../language-reference/modifiers/async.md) . Ignorez l'erreur quand que vous répétez les étapes de conversion pour remplacer l'appel à `CopyTo` par un appel à `CopyToAsync`.

    - Remplacez le nom de la méthode appelée par <xref:System.IO.Stream.CopyToAsync%2A>.

    - La méthode `CopyTo` ou `CopyToAsync` copie les octets dans son argument, `content`, et ne retourne pas de valeur significative. Dans la version synchrone, l'appel à `CopyTo` est une simple instruction qui ne retourne aucune valeur. La version asynchrone, `CopyToAsync`, retourne un <xref:System.Threading.Tasks.Task>. La tâche fonctionne comme Task(void) et permet à la méthode d'être attendue. Appliquez `Await` ou `await` à l'appel à `CopyToAsync`, comme le montre le code suivant.

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         L'instruction précédente abrège les deux lignes de code suivantes.

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. Tout ce qui reste à faire dans `GetURLContents` consiste à adapter la signature de la méthode. Vous pouvez utiliser l' `Await` opérateur uniquement dans les méthodes marquées avec le modificateur [Async](../../../language-reference/modifiers/async.md) . Ajoutez le modificateur pour marquer la méthode en tant que *méthode async*, comme le montre le code suivant.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. Le type de retour d’une méthode Async peut uniquement être <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> . En Visual Basic, la méthode doit être un `Function` qui retourne un `Task` ou `Task(Of T)`, ou la méthode doit être un `Sub`. En règle générale, une `Sub` méthode est utilisée uniquement dans un gestionnaire d’événements Async, où `Sub` est requis. Dans d’autres cas, vous utilisez `Task(T)` si la méthode terminée a une instruction [Return](../../../language-reference/statements/return-statement.md) qui retourne une valeur de type T et que vous utilisez `Task` si la méthode terminée ne retourne pas de valeur significative.

    Pour plus d’informations, consultez [types de retour Async (Visual Basic)](async-return-types.md).

    La méthode `GetURLContents` comporte une instruction return et l'instruction retourne un tableau d'octets. Ainsi, le type de retour de la version asynchrone est Task(T), où T est un tableau d'octets. Apportez les modifications suivantes dans la signature de la méthode :

    - Remplacez le type de retour par `Task(Of Byte())`.

    - Par convention, les méthodes asynchrones portent des noms qui se terminent par « Async ». Renommez alors la méthode `GetURLContentsAsync`.

    Le code suivant illustre ces modifications.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    Avec ces quelques modifications, la conversion de `GetURLContents` en méthode asynchrone est terminée.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Convertir SumPageSizes en méthode asynchrone

1. Répétez les étapes de la procédure précédente pour `SumPageSizes`. Tout d'abord, modifiez l'appel à `GetURLContents` en appel asynchrone.

    - Remplacez le nom de la méthode appelée `GetURLContents` par `GetURLContentsAsync`, si vous ne l'avez pas déjà fait.

    - Appliquez `Await` à la tâche que `GetURLContentsAsync` retourne pour obtenir la valeur du tableau d’octets.

    Le code suivant illustre ces modifications.

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    L'instruction précédente abrège les deux lignes de code suivantes.

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. Apportez les modifications suivantes dans la signature de la méthode :

    - Marquez la méthode avec le modificateur `Async`.

    - Ajoutez « Async » au nom de la méthode.

    - Il n’existe aucune variable de retour de tâche, T, cette fois, car `SumPageSizesAsync` ne retourne pas de valeur pour t. (la méthode n’a aucune `Return` instruction.) Toutefois, la méthode doit retourner un `Task` pour pouvoir être attendu. Par conséquent, remplacez le type de méthode par `Sub` `Function` . Le type de retour de la fonction est `Task`.

    Le code suivant illustre ces modifications.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    La conversion de `SumPageSizes` en `SumPageSizesAsync` est terminée.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Convertir startButton_Click en méthode asynchrone

1. Dans le gestionnaire d'événements, remplacez le nom de la méthode appelée `SumPageSizes` par `SumPageSizesAsync`, si vous ne l'avez pas déjà fait.

2. Étant donné que `SumPageSizesAsync` est une méthode async, modifiez le code dans le gestionnaire d'événements de sorte à attendre le résultat.

    L'appel à `SumPageSizesAsync` reflète l'appel à `CopyToAsync` dans `GetURLContentsAsync`. L'appel retourne un `Task`, et non un `Task(T)`.

    Comme dans les procédures précédentes, vous pouvez convertir l'appel à l'aide d'une ou deux instructions. Le code suivant illustre ces modifications.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. Pour empêcher une nouvelle entrée accidentelle de l’opération, ajoutez l’instruction suivante en haut de `startButton_Click` pour désactiver le bouton **Démarrer**.

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    Vous pouvez réactiver le bouton à la fin du gestionnaire d'événements.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    Pour plus d’informations sur la réentrance, consultez [gestion de la réentrance dans les applications Async (Visual Basic)](handling-reentrancy-in-async-apps.md).

4. Enfin, ajoutez le modificateur `Async` à la déclaration pour que le gestionnaire d’événements puisse attendre `SumPagSizesAsync`.

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    En règle générale, les noms des gestionnaires d'événements ne sont pas modifiés. Le type de retour n’est pas remplacé par `Task` car les gestionnaires d’événements doivent être `Sub` des procédures dans Visual Basic.

    La conversion du projet depuis un traitement synchrone vers un traitement asynchrone est terminée.

## <a name="test-the-asynchronous-solution"></a>Tester la solution asynchrone

1. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

2. Une sortie semblable à la sortie de la solution synchrone doit apparaître. En revanche, observez les différences ci-après.

    - Les résultats ne se produisent pas tous en même temps, une fois le traitement terminé. Par exemple, les deux programmes contiennent une ligne dans `startButton_Click` qui efface la zone de texte. L’objectif est d’effacer la zone de texte entre les exécutions si vous choisissez le bouton **Démarrer** une deuxième fois, une fois qu’un jeu de résultats est apparu. Dans la version synchrone, la zone de texte s’efface juste avant que les nombres n’apparaissent pour la deuxième fois, quand les téléchargements sont terminés et que le thread d’interface utilisateur est libre d’effectuer autre chose. Dans la version asynchrone, la zone de texte s’efface immédiatement après avoir choisi le bouton **Démarrer**.

    - Plus important encore, le thread d'interface utilisateur n'est pas bloqué pendant les téléchargements. Vous pouvez déplacer ou redimensionner la fenêtre pendant le téléchargement, la comptabilisation et l'affichage des ressources web. Si l’un des sites web est lent ou ne répond pas, vous pouvez annuler l’opération en choisissant le bouton **Fermer** (le x dans le champ rouge situé dans le coin supérieur droit).

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>Remplacer la méthode GetURLContentsAsync par une méthode .NET Framework

1. Le .NET Framework fournit de nombreuses méthodes Async que vous pouvez utiliser. L’une d’entre elles, la <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> méthode, fait exactement ce dont vous avez besoin pour cette procédure pas à pas. Vous pouvez l'utiliser à la place de la méthode `GetURLContentsAsync` que vous avez créée précédemment.

    La première étape consiste à créer un <xref:System.Net.Http.HttpClient> objet dans la `SumPageSizesAsync` méthode. Ajoutez la déclaration suivante au début de la méthode.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. Dans `SumPageSizesAsync,`, remplacez l'appel à votre méthode `GetURLContentsAsync` par un appel à la méthode `HttpClient`.

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Supprimez ou commentez la méthode `GetURLContentsAsync` que vous avez écrite.

4. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

    Le comportement de cette version du projet doit correspondre à celui décrit par la procédure « Pour tester la solution asynchrone » mais avec encore moins d'efforts de votre part.

## <a name="example"></a>Exemple

Voici l’exemple complet de la solution asynchrone convertie qui utilise la `GetURLContentsAsync` méthode asynchrone. Remarquez qu’il ressemble fortement à la solution synchrone d’origine.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
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

Le code suivant inclut l'exemple complet de la solution qui utilise la méthode `HttpClient`, `GetByteArrayAsync`.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
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

- [Exemple Async : Accès à la procédure web (C# et Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await (opérateur)](../../../language-reference/operators/await-operator.md)
- [Asynchrone](../../../language-reference/modifiers/async.md)
- [Programmation asynchrone avec Async et Await (Visual Basic)](index.md)
- [Types de retour Async (Visual Basic)](async-return-types.md)
- [Programmation asynchrone basée sur les tâches (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Guide pratique : effectuer plusieurs requêtes web en parallèle avec Async et Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
