---
title: Dans la mesure où cet appel n'est pas attendu, la méthode actuelle continue de s'exécuter avant la fin de l'appel.
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 5870a9a3a598c67badc9868af1486b52c76a9906
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523910"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Dans la mesure où cet appel n'est pas attendu, la méthode actuelle continue de s'exécuter avant la fin de l'appel.

Cet appel n’étant pas attendu, l’exécution de la méthode actuelle continue avant la fin de l’appel. Envisagez d’appliquer l’opérateur « Await » au résultat de l’appel.

La méthode actuelle appelle une méthode asynchrone qui retourne <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et n’applique pas l’opérateur [Await](../../../visual-basic/language-reference/operators/await-operator.md) au résultat. L'appel à la méthode asynchrone lance une tâche asynchrone. Toutefois, étant donné qu'aucun opérateur `Await` n'est appliqué, le programme se poursuit sans attendre la tâche à exécuter. Dans la plupart des cas, ce comportement est inattendu. En général, les autres aspects de la méthode d'appel dépendent des résultats de l'appel ou, au moins, la méthode appelée est censée se terminer avant le retour de la méthode qui contient l'appel.

Une question tout aussi importante n’est autre que de savoir ce que deviennent les exceptions générées dans la méthode asynchrone appelée. Une exception générée dans une méthode qui retourne <xref:System.Threading.Tasks.Task> ou  <xref:System.Threading.Tasks.Task%601> est stockée dans la tâche renvoyée. Si vous n'attendez pas la tâche ou si vous vérifiez explicitement les exceptions, l'exception est perdue. Si vous attendez la tâche, l'exception est renvoyée.

À titre de recommandation, vous devriez toujours attendre l'appel.

Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID d’erreur :** BC42358

### <a name="to-address-this-warning"></a>Pour traiter cet avertissement

- Envisagez de supprimer l'avertissement uniquement si vous êtes certain que vous ne souhaitez pas attendre l'exécution de l'appel asynchrone et que la méthode appelée ne génèrera pas d'exception. Dans ce cas, vous pouvez supprimer l'avertissement en affectant le résultat de la tâche à une variable.

     L'exemple suivant indique comment générer l'avertissement, comment le supprimer, et comment attendre l'appel.

    ```vb
    Async Function CallingMethodAsync() As Task

        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

        ' Variable delay is used to slow down the called method so that you
        ' can distinguish between awaiting and not awaiting in the program's output.
        ' You can adjust the value to produce the output that this topic shows
        ' after the code.
        Dim delay = 5000

        ' Call #1.
        ' Call an async method. Because you don't await it, its completion isn't
        ' coordinated with the current method, CallingMethodAsync.
        ' The following line causes the warning.
        CalledMethodAsync(delay)

        ' Call #2.
        ' To suppress the warning without awaiting, you can assign the
        ' returned task to a variable. The assignment doesn't change how
        ' the program runs. However, the recommended practice is always to
        ' await a call to an async method.
        ' Replace Call #1 with the following line.
        'Task delayTask = CalledMethodAsync(delay)

        ' Call #3
        ' To contrast with an awaited call, replace the unawaited call
        ' (Call #1 or Call #2) with the following awaited call. The best
        ' practice is to await the call.

        'Await CalledMethodAsync(delay)

        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
        ' continues to run and, in this example, finishes its work and returns
        ' to its caller.
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
    End Function

    Async Function CalledMethodAsync(howLong As Integer) As Task

        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
        ' Slow the process down a little so you can distinguish between awaiting
        ' and not awaiting. Adjust the value for howLong if necessary.
        Await Task.Delay(howLong)
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
    End Function
    ```

     Dans l'exemple, si vous choisissez Appel #1 ou Appel #2, la méthode asynchrone inattendue (`CalledMethodAsync`) se termine une fois que son appelant (`CallingMethodAsync`) et l'appelant de l'appelant (`StartButton_Click`) sont terminés. La dernière ligne de la sortie suivante vous indique lorsque la méthode appelée se termine. L'entrée et la sortie du gestionnaire d'événements qui appelle `CallingMethodAsync` dans l'exemple complet sont marquées dans la sortie.

    ```console
    Entering the Click event handler.
      Entering calling method.
        Entering called method, starting and awaiting Task.Delay.
      Returning from calling method.
    Exiting the Click event handler.
        Task.Delay is finished--returning from called method.
    ```

## <a name="example"></a>Exemple

L'application suivante de Windows Presentation Foundation (WPF) contient les méthodes de l'exemple précédent. Les étapes suivantes permettent d'installer l'application.

1. Créez une application WPF et nommez-la `AsyncWarning`.

2. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

     Si l'onglet n'est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans l' **Explorateur de solutions**, puis choisissez **Afficher le code**.

3. Remplacez le code dans la vue **XAML** de MainWindow.xaml, par le code suivant.

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>
        </Grid>
    </Window>
    ```

     Une fenêtre simple contenant un bouton et une zone de texte apparaît dans la vue **Design** de MainWindow.xaml.

     Pour plus d’informations sur le concepteur XAML, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Pour plus d’informations sur la création de votre propre interface utilisateur simple, consultez les sections "Pour créer une application WPF" et "Pour concevoir une simple fenêtre MainWindow WPF" de la [Procédure pas à pas : accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).

4. Remplacez le code situé dans MainWindow.xaml.vb par le code suivant.

    ```vb
    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."
            Await CallingMethodAsync()
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."
        End Sub

        Async Function CallingMethodAsync() As Task

            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

            ' Variable delay is used to slow down the called method so that you
            ' can distinguish between awaiting and not awaiting in the program's output.
            ' You can adjust the value to produce the output that this topic shows
            ' after the code.
            Dim delay = 5000

            ' Call #1.
            ' Call an async method. Because you don't await it, its completion isn't
            ' coordinated with the current method, CallingMethodAsync.
            ' The following line causes the warning.
            CalledMethodAsync(delay)

            ' Call #2.
            ' To suppress the warning without awaiting, you can assign the
            ' returned task to a variable. The assignment doesn't change how
            ' the program runs. However, the recommended practice is always to
            ' await a call to an async method.

            ' Replace Call #1 with the following line.
            'Task delayTask = CalledMethodAsync(delay)

            ' Call #3
            ' To contrast with an awaited call, replace the unawaited call
            ' (Call #1 or Call #2) with the following awaited call. The best
            ' practice is to await the call.

            'Await CalledMethodAsync(delay)

            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
            ' continues to run and, in this example, finishes its work and returns
            ' to its caller.
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
        End Function

        Async Function CalledMethodAsync(howLong As Integer) As Task

            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
            ' Slow the process down a little so you can distinguish between awaiting
            ' and not awaiting. Adjust the value for howLong if necessary.
            Await Task.Delay(howLong)
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
        End Function

    End Class

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    '     Task.Delay is finished--returning from called method.

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '     Task.Delay is finished--returning from called method.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    ```

5. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

     La sortie attendue apparaît à la fin du code.

## <a name="see-also"></a>Voir aussi

- [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md)
