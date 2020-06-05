---
title: Types de retour Async
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 5d19fc9831580412da24333be0885fce55384658
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396712"
---
# <a name="async-return-types-visual-basic"></a>Types de retour Async (Visual Basic)

Les méthodes async ont trois types de retour possibles : <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> et void. En Visual Basic, le type de retour void est écrit sous forme de procédure [Sub](../../language-features/procedures/sub-procedures.md). Pour plus d’informations sur les méthodes Async, consultez [programmation asynchrone avec Async et await (Visual Basic)](index.md).

Chaque type de retour est examiné dans l’une des sections suivantes, et vous trouverez un exemple complet qui utilise les trois types à la fin de la rubrique.

> [!NOTE]
> Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a> Type de retour Task(T)

Le <xref:System.Threading.Tasks.Task%601> type de retour est utilisé pour une méthode Async qui contient une instruction [Return](../../../language-reference/statements/return-statement.md) dans laquelle l’opérande a le type `TResult` .

Dans l’exemple suivant, la méthode async `TaskOfT_MethodAsync` contient une instruction return qui retourne un entier. La déclaration de méthode doit donc spécifier un type de retour `Task(Of Integer)`.

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

Quand `TaskOfT_MethodAsync` est appelé à partir d’une expression await, celle-ci récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par `TaskOfT_MethodAsync`. Pour plus d’informations sur les expressions await, consultez [await, opérateur](../../../language-reference/operators/await-operator.md).

Le code suivant appelle et attend la méthode `TaskOfT_MethodAsync`. Le résultat est assigné à la variable `result1`.

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

Vous pouvez mieux comprendre comment cela se produit en séparant l’appel à `TaskOfT_MethodAsync` de l’application de `Await`, comme l’illustre le code suivant. Un appel à la méthode `TaskOfT_MethodAsync` qui n’est pas immédiatement attendue retourne un type `Task(Of Integer)`, comme vous pourriez l’attendre de la déclaration de la méthode. La tâche est assignée à la variable `integerTask` dans l’exemple. Comme `integerTask` est un <xref:System.Threading.Tasks.Task%601>, il contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`. Dans ce cas, TResult représente un type entier. Quand `Await` est appliqué à `integerTask`, l’expression await prend pour la valeur le contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. La valeur est assignée à la variable `result2`.

> [!WARNING]
> <xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante. Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible. Dans la plupart des cas, vous devez accéder à la valeur avec `Await` au lieu d’accéder directement à la propriété.

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

Les instructions d’affichage dans le code suivant vérifient que les valeurs de la variable `result1`, de la variable `result2` et de la propriété `Result` sont identiques. N’oubliez pas que `Result` est une propriété bloquante et que vous ne devez pas y accéder avant que sa tâche soit attendue.

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a> Type de retour Task

Les méthodes async qui ne contiennent pas d’instruction return ou qui en contiennent une qui ne retourne pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>. Ces méthodes seraient des [sous](../../language-features/procedures/sub-procedures.md) -procédures si elles ont été écrites pour s’exécuter de façon synchrone. Si vous utilisez un type de retour `Task` pour une méthode async, une méthode d’appel peut utiliser un opérateur `Await` pour suspendre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.

Dans l’exemple suivant, la méthode async `Task_MethodAsync` ne contient pas d’instruction return. Par conséquent, vous spécifiez le type de retour `Task` pour la méthode, ce qui permet à `Task_MethodAsync` d’être attendu. La définition du type `Task` n’inclut pas de propriété `Result` pour stocker une valeur de retour.

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

`Task_MethodAsync` est appelé et attendu à l’aide d’une instruction await et non d’une expression await, à l’instar de l’instruction d’appel d’une méthode `Sub` synchrone ou d’une méthode qui retourne une valeur void. `Await`Dans ce cas, l’application d’un opérateur ne produit pas de valeur.

Le code suivant appelle et attend la méthode `Task_MethodAsync`.

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

Comme dans l' <xref:System.Threading.Tasks.Task%601> exemple précédent, vous pouvez séparer l’appel à `Task_MethodAsync` de l’application d’un `Await` opérateur, comme le montre le code suivant. Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.

Le code suivant sépare l’appel à `Task_MethodAsync` de l’attente de la tâche que retourne `Task_MethodAsync`.

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a>Type de retour void

L’utilisation principale des `Sub` procédures est dans les gestionnaires d’événements, où il n’y a aucun type de retour (appelé type de retour void dans d’autres langages). Le retour de type void peut aussi être utilisé pour remplacer les méthodes qui retournent void ou pour les méthodes qui effectuent des activités considérées comme autonomes après activation (« Fire and Forget ». Toutefois, vous devez retourner un type `Task` dans la mesure du possible, car une méthode async qui retourne un type void ne peut pas être attendue. Tout appelant d’une telle méthode doit pouvoir continuer jusqu’à l’achèvement sans attendre que la méthode async soit terminée, et l’appelant doit être indépendant des valeurs ou des exceptions générées par la méthode async.

L’appelant d’une méthode async qui retourne une valeur void ne peut pas intercepter les exceptions levées à partir de la méthode, et ces exceptions non gérées peuvent entraîner l’échec de votre application. Si une exception se produit dans une méthode asyn qui retourne <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, l’exception est stockée dans la tâche retournée et est à nouveau levée pendant l’attente de la tâche. Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.

Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez la page [Instruction Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).

Le code suivant définit un gestionnaire d’événements asynchrones.

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="complete-example"></a><a name="BKMK_Example"></a>Exemple complet

Le projet Windows Presentation Foundation (WPF) suivant contient les exemples de code de cette rubrique.

 Pour exécuter le projet, procédez comme suit :

1. Démarrez Visual Studio.

2. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans la catégorie **installé**, **modèles** , choisissez **Visual Basic**, puis choisissez **Windows**. Choisissez **Application WPF** dans la liste des types de projets.

4. Entrez `AsyncReturnTypes` comme nom du projet, puis choisissez le bouton **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

5. Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .

     Si l’onglet n’est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Ouvrir**.

6. Dans la fenêtre **XAML** de MainWindow.xaml, remplacez le code existant par le code suivant.

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la fenêtre **Design** de MainWindow.xaml.

7. Dans **Explorateur de solutions**, ouvrez le menu contextuel de MainWindow. Xaml. vb, puis choisissez **afficher le code**.

8. Remplacez le code situé dans MainWindow.xaml.vb par le code suivant.

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.

     La sortie suivante doit s’afficher :

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Procédure pas à pas : accès au web avec Async et Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Flux de contrôle dans les programmes Async (Visual Basic)](control-flow-in-async-programs.md)
- [Asynchrone](../../../language-reference/modifiers/async.md)
- [Await (opérateur)](../../../language-reference/operators/await-operator.md)
