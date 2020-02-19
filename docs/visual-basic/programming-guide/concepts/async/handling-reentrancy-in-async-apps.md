---
title: Gestion de la réentrance dans Async Apps
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 44c2cdbadd02aef6b2bbb32bde8bcb9b19f8360d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452576"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Gestion de la réentrance dans les applications Async (Visual Basic)

Quand vous incluez du code asynchrone dans votre application, vous devez prendre en compte et éventuellement empêcher la réentrance, qui fait référence à une nouvelle entrée d'une opération asynchrone avant qu'elle soit terminée. Si vous n'identifiez pas et ne gérez pas les possibilités de réentrance, les résultats peuvent être inattendus.

> [!NOTE]
> Pour exécuter l’exemple, vous devez avoir Visual Studio version 2012 ou ultérieure et .NET Framework version 4.5 ou ultérieure installés sur votre ordinateur.

> [!NOTE]
> La version 1,2 de TLS (Transport Layer Security) est désormais la version minimale à utiliser dans le développement de votre application. Si votre application cible une version de .NET Framework antérieure à 4,7, reportez-vous à l’article suivant pour [les meilleures pratiques de Transport Layer Security (TLS) avec le .NET Framework](../../../../framework/network-programming/tls.md).

## <a name="BKMK_RecognizingReentrancy"></a> Identification de la réentrance

Dans l’exemple de cette rubrique, les utilisateurs choisissent un bouton **Démarrer** pour lancer une application asynchrone qui télécharge une série de sites web et calcule le nombre total d’octets téléchargés. Une version synchrone de l’exemple répondrait de la même façon quel que soit le nombre de fois où un utilisateur clique sur le bouton car, après la première fois, le thread d’interface utilisateur ignore ces événements jusqu’à ce que l’application arrête de s’exécuter. Dans une application asynchrone, en revanche, le thread d'interface utilisateur continue de répondre et vous pouvez entrer à nouveau l'opération asynchrone avant qu'elle soit terminée.

L’exemple suivant illustre la sortie attendue si l’utilisateur choisit le bouton **Démarrer** une seule fois. La liste des sites web téléchargés apparaît avec la taille, en octets, de chaque site. Le nombre total d'octets apparaît à la fin.

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Toutefois, si l'utilisateur choisit le bouton plusieurs fois, le gestionnaire d'événements est appelé à plusieurs reprises et le processus de téléchargement est à nouveau entré à chaque fois. Ainsi, plusieurs opérations asynchrones s'exécutent en même temps, la sortie entrelace les résultats et le nombre total d'octets est source de confusion.

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Vous pouvez passer en revue le code qui produit cette sortie en accédant à la fin de cette rubrique. Vous pouvez faire des essais avec le code en téléchargeant la solution sur votre ordinateur local, puis en exécutant le projet WebsiteDownload ou en utilisant le code donné à la fin de cette rubrique pour créer votre propre projet. Pour plus d’informations et d’instructions, consultez [Examen et exécution de l’exemple d’application](#BKMD_SettingUpTheExample).

## <a name="BKMK_HandlingReentrancy"></a> Gestion de la réentrance

Vous pouvez gérer la réentrance de différentes façons, selon ce que vous voulez que votre application fasse. Cette rubrique présente les exemples suivants :

- [Désactiver le bouton Démarrer](#BKMK_DisableTheStartButton)

  Désactivez le bouton **Démarrer** pendant que l’opération est en cours d’exécution afin que l’utilisateur ne puisse pas l’interrompre.

- [Annuler et redémarrer l’opération](#BKMK_CancelAndRestart)

  Annulez toute opération encore en cours d’exécution quand l’utilisateur choisit le bouton **Démarrer** à nouveau, puis laissez l’opération demandée le plus récemment continuer.

- [Exécuter plusieurs opérations et mettre la sortie en file d’attente](#BKMK_RunMultipleOperations)

  Autorisez toutes les opérations demandées à s'exécuter de façon asynchrone, mais coordonnez l'affichage de la sortie de sorte que les résultats de chaque opération apparaissent ensemble et dans l'ordre.

### <a name="BKMK_DisableTheStartButton"></a> Désactiver le bouton Démarrer

Vous pouvez bloquer le bouton **Démarrer** pendant l’exécution d’une opération en désactivant le bouton en haut du gestionnaire d’événements `StartButton_Click`. Ensuite, vous pouvez réactiver le bouton depuis un bloc `Finally` quand l'opération se termine pour que les utilisateurs puissent exécuter à nouveau l'application.

Le code suivant illustre ces modifications, marquées par des astérisques. Vous pouvez ajouter les modifications apportées au code à la fin de cette rubrique, ou vous pouvez télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Le nom du projet est DisableStartButton.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' This line is commented out to make the results clearer in the output.
    'ResultsTextBox.Text = ""

    ' ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = False

    Try
        Await AccessTheWebAsync()

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    ' ***Enable the Start button in case you want to run the program again.
    Finally
        StartButton.IsEnabled = True

    End Try
End Sub
```

Suite aux modifications, le bouton ne répond pas pendant que `AccessTheWebAsync` télécharge les sites Web, donc le processus ne peut pas être entré de nouveau.

### <a name="BKMK_CancelAndRestart"></a> Annuler et redémarrer l’opération

Au lieu de désactiver le bouton **Démarrer**, vous pouvez garder le bouton actif. Toutefois, si l’utilisateur choisit de nouveau ce bouton, annulez l’opération qui est déjà en cours d’exécution et laissez continuer l’opération le plus récemment démarrée.

Pour plus d’informations sur l’annulation, consultez [réglage de votre application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).

Pour configurer ce scénario, apportez les modifications suivantes au code de base fourni dans [Examen et exécution de l’exemple d’application](#BKMD_SettingUpTheExample). Vous pouvez également télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Le nom de ce projet est CancelAndRestart.

1. Déclarez une variable <xref:System.Threading.CancellationTokenSource>, `cts`, qui est dans la portée de toutes les méthodes.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. Dans `StartButton_Click`, déterminez si une opération est déjà en cours d'exécution. Si la valeur de `cts` est `Nothing`, aucune opération n’est déjà active. Si la valeur n’est pas `Nothing`, l’opération qui est déjà en cours d’exécution est annulée.

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. Définissez `cts` sur une autre valeur qui représente le processus en cours.

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. À la fin de `StartButton_Click`, le processus actuel est terminé, donc réaffectez la valeur de `cts` à `Nothing`.

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Le code suivant illustre toutes les modifications dans `StartButton_Click` : Les ajouts sont marqués par des astérisques.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

    ' This line is commented out to make the results clearer.
    'ResultsTextBox.Text = ""

    ' *** If a download process is underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If

    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS

    Try
        ' *** Send a token to carry the message if the operation is canceled.
        Await AccessTheWebAsync(cts.Token)

    Catch ex As OperationCanceledException
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    End Try

    ' *** When the process is complete, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
End Sub
```

Dans `AccessTheWebAsync`, apportez les modifications suivantes.

- Ajoutez un paramètre pour accepter le jeton d'annulation en provenance de `StartButton_Click`.

- Utilisez la méthode <xref:System.Net.Http.HttpClient.GetAsync%2A> pour télécharger les sites Web car `GetAsync` accepte un argument <xref:System.Threading.CancellationToken>.

- Avant d'appeler `DisplayResults` pour afficher les résultats de chaque site Web téléchargé, vérifiez `ct` pour vous assurer que l'opération en cours n'a pas été annulée.

 Le code suivant illustre ces modifications, marquées par des astérisques.

```vb
' *** Provide a parameter for the CancellationToken from StartButton_Click.
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task

    ' Declare an HttpClient object.
    Dim client = New HttpClient()

    ' Make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()

    Dim total = 0
    Dim position = 0

    For Each url In urlList
        ' *** Use the HttpClient.GetAsync method because it accepts a
        ' cancellation token.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' *** Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' *** Check for cancellations before displaying information about the
        ' latest site.
        ct.ThrowIfCancellationRequested()

        position += 1
        DisplayResults(url, urlContents, position)

        ' Update the total.
        total += urlContents.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

Si vous choisissez le bouton **Démarrer** plusieurs fois pendant l’exécution de cette application, elle doit produire des résultats qui ressemblent à la sortie suivante :

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Pour éliminer les listes partielles, supprimez les commentaires de la première ligne de code dans `StartButton_Click` pour effacer la zone de texte chaque fois que l'utilisateur redémarre l'opération.

### <a name="BKMK_RunMultipleOperations"></a> Exécuter plusieurs opérations et mettre la sortie en file d’attente

Ce troisième exemple est le plus compliqué, car l’application démarre une autre opération asynchrone chaque fois que l’utilisateur choisit le bouton **Démarrer**, et toutes les opérations s’exécutent jusqu’à leur achèvement. Toutes les opérations demandées téléchargent des sites web de la liste de façon asynchrone, mais la sortie des opérations est présentée séquentiellement. Autrement dit, l’activité de téléchargement réelle est entrelacée, comme le montre la sortie dans [Identification de la réentrance](#BKMK_RecognizingReentrancy), mais la liste des résultats de chaque groupe est présentée séparément.

Les opérations partagent un <xref:System.Threading.Tasks.Task> global, `pendingWork`, qui sert d'opérateur de contrôle d'appels pour le processus d'affichage.

Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](#BKMK_BuildingTheApp), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](#BKMK_DownloadingTheApp) pour télécharger l’exemple, puis exécuter le projet QueueResults.

La sortie suivante montre le résultat obtenu si l’utilisateur choisit le bouton **Démarrer** une seule fois. L’étiquette A indique que le résultat part de la première fois que le bouton **Démarrer** est choisi. Les numéros indiquent l'ordre des URL dans la liste des cibles de téléchargement.

```console
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

Si l’utilisateur choisit le bouton **Démarrer** trois fois, l’application produit une sortie semblable aux lignes suivantes. Les lignes d'information qui commencent par un signe dièse (#) suivent la progression de l'application.

```console
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

Les groupes B et C démarrent avant que le groupe A ait terminé, mais la sortie de chaque groupe apparaît séparément. Toute la sortie du groupe A apparaît en premier, suivie de toute la sortie du groupe B, puis de toute la sortie du groupe C. L’application affiche toujours les groupes dans l’ordre et, pour chaque groupe, elle affiche toujours les informations sur les sites web, dans l’ordre où les URL apparaissent dans la liste des URL.

Toutefois, vous ne pouvez pas prévoir l'ordre dans lequel les téléchargements se produisent réellement. Après le démarrage de plusieurs groupes, les tâches de téléchargement qu'ils génèrent sont toutes actives. Vous ne pouvez pas supposer que A-1 sera téléchargé avant B-1 ni que A-1 sera téléchargé avant A-2.

#### <a name="global-definitions"></a>Définitions globales

L'exemple de code contient les deux déclarations globales suivantes qui sont visibles à partir de toutes les méthodes.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

La variable `Task`, `pendingWork`, supervise le processus d'affichage et empêche tout groupe d'interrompre l'opération d'affichage d'un autre groupe. La variable de caractère `group`, étiquette la sortie de différents groupes pour vérifier que les résultats apparaissent dans l'ordre attendu.

#### <a name="the-click-event-handler"></a>Gestionnaire d'événements Click

Le gestionnaire d’événements, `StartButton_Click`, incrémente la lettre du groupe chaque fois que l’utilisateur choisit le bouton **Démarrer**. Ensuite, le gestionnaire appelle `AccessTheWebAsync` pour exécuter l'opération de téléchargement.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' ***Verify that each group's results are displayed together, and that
    ' the groups display in order, by marking each group with a letter.
    group = ChrW(AscW(group) + 1)
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)

    Try
        ' *** Pass the group value to AccessTheWebAsync.
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)

        ' The following line verifies a successful return from the download and
        ' display procedures.
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."

    End Try
End Sub
```

#### <a name="the-accessthewebasync-method"></a>Méthode AccessTheWebAsync

Cet exemple fractionne `AccessTheWebAsync` en deux méthodes. La première méthode, `AccessTheWebAsync`, démarre toutes les tâches de téléchargement d'un groupe et configure `pendingWork` pour contrôler le processus d'affichage. La méthode utilise une requête LINQ (Language Integrated Query) et <xref:System.Linq.Enumerable.ToArray%2A> pour démarrer toutes les tâches de téléchargement en même temps.

`AccessTheWebAsync` appelle ensuite `FinishOneGroupAsync` pour attendre la fin de chaque téléchargement et en afficher la longueur.

`FinishOneGroupAsync` retourne une tâche assignée à `pendingWork` dans `AccessTheWebAsync`. Cette valeur empêche toute interruption par une autre opération avant que la tâche ne soit terminée.

```vb
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)

    Dim client = New HttpClient()

    ' Make a list of the web addresses to download.
    Dim urlList As List(Of String) = SetUpURLList()

    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Dim getContentTasks As Task(Of Byte())() =
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()

    ' ***Call the method that awaits the downloads and displays the results.
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)

    ResultsTextBox.Text &=
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)

    ' ***This task is complete when a group has finished downloading and displaying.
    Await pendingWork

    ' You can do other work here or just return.
    Return grp
End Function
```

#### <a name="the-finishonegroupasync-method"></a>Méthode FinishOneGroupAsync

Cette méthode parcourt les tâches de téléchargement dans un groupe, en attendant chacune d’elles, en affichant la longueur du site web téléchargé et en ajoutant la longueur au total.

La première instruction dans `FinishOneGroupAsync` utilise `pendingWork` pour vérifier que l’entrée de la méthode n’interfère pas avec une opération qui est déjà dans le processus d’affichage ou qui est déjà en train d’attendre. Si une telle opération est en cours, l'opération d'entrée doit attendre son tour.

```vb
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task

    ' Wait for the previous group to finish displaying results.
    If pendingWork IsNot Nothing Then
        Await pendingWork
    End If

    Dim total = 0

    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    For i As Integer = 0 To contentTasks.Length - 1
        ' Await the download of a particular URL, and then display the URL and
        ' its length.
        Dim content As Byte() = Await contentTasks(i)
        DisplayResults(urls(i), content, i, grp)
        total += content.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](#BKMK_BuildingTheApp), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](#BKMK_DownloadingTheApp) pour télécharger l’exemple, puis exécuter le projet QueueResults.

#### <a name="points-of-interest"></a>Points d'intérêt

Les lignes d'information qui commencent par un signe dièse (#) dans la sortie clarifient le fonctionnement de cet exemple.

La sortie affiche les modèles suivants.

- Un groupe peut être démarré pendant qu'un groupe précédent affiche sa sortie, mais l'affichage de la sortie du groupe précédent n'est pas interrompu.

  ```console
  #Starting group A.
  #Task assigned for group A. Download tasks are active.

  A-1. msdn.microsoft.com/library/hh191443.aspx                87389
  A-2. msdn.microsoft.com/library/aa578028.aspx               207089
  A-3. msdn.microsoft.com/library/jj155761.aspx                30870
  A-4. msdn.microsoft.com/library/hh290140.aspx               119037
  A-5. msdn.microsoft.com/library/hh524395.aspx                71260

  #Starting group B.
  #Task assigned for group B. Download tasks are active.

  A-6. msdn.microsoft.com/library/ms404677.aspx               199186
  A-7. msdn.microsoft.com                                            53078
  A-8. msdn.microsoft.com/library/ff730837.aspx               148010

  TOTAL bytes returned:  915919

  B-1. msdn.microsoft.com/library/hh191443.aspx                87388
  B-2. msdn.microsoft.com/library/aa578028.aspx               207089
  B-3. msdn.microsoft.com/library/jj155761.aspx                30870

  #Group A is complete.

  B-4. msdn.microsoft.com/library/hh290140.aspx               119027
  B-5. msdn.microsoft.com/library/hh524395.aspx                71260
  B-6. msdn.microsoft.com/library/ms404677.aspx               199186
  B-7. msdn.microsoft.com                                            53078
  B-8. msdn.microsoft.com/library/ff730837.aspx               148010

  TOTAL bytes returned:  915908
  ```

- La tâche `pendingWork` est `Nothing` au début de `FinishOneGroupAsync` uniquement pour le groupe A, qui a démarré en premier. Le groupe A n'a pas encore terminé une expression await quand il atteint `FinishOneGroupAsync`. Par conséquent, le contrôle n'a pas retourné à `AccessTheWebAsync`, et la première assignation à `pendingWork` ne s'est pas produite.

- Les deux lignes suivantes apparaissent toujours ensemble dans la sortie. Le code n'est jamais interrompu entre le démarrage d'une opération de groupe dans `StartButton_Click` et l'affectation d'une tâche pour le groupe à `pendingWork`.

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Une fois qu'un groupe entre `StartButton_Click`, l'opération ne termine pas une expression await tant que l'opération n'entre pas `FinishOneGroupAsync`. Par conséquent, aucune autre opération ne peut obtenir le contrôle au cours de ce segment de code.

## <a name="BKMD_SettingUpTheExample"></a> Examen et exécution de l’exemple d’application

Pour mieux comprendre l’exemple d’application, vous pouvez le télécharger, le créer vous-même ou passer en revue le code à la fin de cette rubrique sans implémenter l’application.

> [!NOTE]
> Pour exécuter l’exemple comme une application de bureau WPF, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.

### <a name="BKMK_DownloadingTheApp"></a> Téléchargement de l’application

1. Téléchargez le fichier compressé dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.

3. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.

4. Accédez au dossier qui contient l’exemple de code décompressé, puis ouvrez le fichier solution (.sln).

5. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet à modifier, puis choisissez **Définir comme StartUpProject**.

6. Appuyez sur les touches CTRL+F5 pour générer et exécuter le projet.

### <a name="BKMK_BuildingTheApp"></a> Génération de l’application

La section suivante fournit le code pour générer l’exemple comme une application WPF.

##### <a name="to-build-a-wpf-app"></a>Pour générer une application WPF

1. Démarrez Visual Studio.

2. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **modèles installés** , développez **Visual Basic**, puis développez **Windows**.

4. Dans la liste des types de projets, choisissez **Application WPF**.

5. Nommez le projet `WebsiteDownloadWPF`, choisissez .NET Framework version 4,6 ou ultérieure, puis cliquez sur le bouton **OK** .

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

6. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

     Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.

7. Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.

    ```xaml
    <Window x:Class="MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.

8. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références** , puis sélectionnez **Ajouter une référence**.

     Ajoutez une référence pour <xref:System.Net.Http>, si elle n’est pas déjà sélectionnée.

9. Dans **Explorateur de solutions**, ouvrez le menu contextuel de MainWindow. Xaml. vb, puis choisissez **afficher le code**.

10. Dans MainWindow. Xaml. vb, remplacez le code par le code suivant.

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

            ' This line is commented out to make the results clearer in the output.
            'ResultsTextBox.Text = ""

            Try
                Await AccessTheWebAsync()

            Catch ex As Exception
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."

            End Try
        End Sub

        Private Async Function AccessTheWebAsync() As Task

            ' Declare an HttpClient object.
            Dim client = New HttpClient()

            ' Make a list of web addresses.
            Dim urlList As List(Of String) = SetUpURLList()

            Dim total = 0
            Dim position = 0

            For Each url In urlList
                ' GetByteArrayAsync returns a task. At completion, the task
                ' produces a byte array.
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

                position += 1
                DisplayResults(url, urlContents, position)

                ' Update the total.
                total += urlContents.Length
            Next

            ' Display the total count for all of the websites.
            ResultsTextBox.Text &=
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
        End Function

        Private Function SetUpURLList() As List(Of String)
            Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. Appuyez sur les touches CTRL+F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** plusieurs fois.

12. Apportez les modifications indiquées dans [Désactiver le bouton Démarrer](#BKMK_DisableTheStartButton), [Annuler et redémarrer l’opération](#BKMK_CancelAndRestart) ou [Exécuter plusieurs opérations et mettre la sortie en file d’attente](#BKMK_RunMultipleOperations) pour gérer la réentrance.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
