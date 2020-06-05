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
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="29023-102">Types de retour Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29023-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="29023-103">Les méthodes async ont trois types de retour possibles : <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> et void.</span><span class="sxs-lookup"><span data-stu-id="29023-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="29023-104">En Visual Basic, le type de retour void est écrit sous forme de procédure [Sub](../../language-features/procedures/sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="29023-104">In Visual Basic, the void return type is written as a [Sub](../../language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="29023-105">Pour plus d’informations sur les méthodes Async, consultez [programmation asynchrone avec Async et await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="29023-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="29023-106">Chaque type de retour est examiné dans l’une des sections suivantes, et vous trouverez un exemple complet qui utilise les trois types à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="29023-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="29023-107">Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29023-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="29023-108">Type de retour Task(T)</span><span class="sxs-lookup"><span data-stu-id="29023-108">Task(T) Return Type</span></span>

<span data-ttu-id="29023-109">Le <xref:System.Threading.Tasks.Task%601> type de retour est utilisé pour une méthode Async qui contient une instruction [Return](../../../language-reference/statements/return-statement.md) dans laquelle l’opérande a le type `TResult` .</span><span class="sxs-lookup"><span data-stu-id="29023-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="29023-110">Dans l’exemple suivant, la méthode async `TaskOfT_MethodAsync` contient une instruction return qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="29023-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="29023-111">La déclaration de méthode doit donc spécifier un type de retour `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="29023-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="29023-112">Quand `TaskOfT_MethodAsync` est appelé à partir d’une expression await, celle-ci récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="29023-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="29023-113">Pour plus d’informations sur les expressions await, consultez [await, opérateur](../../../language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="29023-113">For more information about await expressions, see [Await Operator](../../../language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="29023-114">Le code suivant appelle et attend la méthode `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="29023-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="29023-115">Le résultat est assigné à la variable `result1`.</span><span class="sxs-lookup"><span data-stu-id="29023-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="29023-116">Vous pouvez mieux comprendre comment cela se produit en séparant l’appel à `TaskOfT_MethodAsync` de l’application de `Await`, comme l’illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29023-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="29023-117">Un appel à la méthode `TaskOfT_MethodAsync` qui n’est pas immédiatement attendue retourne un type `Task(Of Integer)`, comme vous pourriez l’attendre de la déclaration de la méthode.</span><span class="sxs-lookup"><span data-stu-id="29023-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="29023-118">La tâche est assignée à la variable `integerTask` dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="29023-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="29023-119">Comme `integerTask` est un <xref:System.Threading.Tasks.Task%601>, il contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="29023-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="29023-120">Dans ce cas, TResult représente un type entier.</span><span class="sxs-lookup"><span data-stu-id="29023-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="29023-121">Quand `Await` est appliqué à `integerTask`, l’expression await prend pour la valeur le contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="29023-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="29023-122">La valeur est assignée à la variable `result2`.</span><span class="sxs-lookup"><span data-stu-id="29023-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="29023-123"><xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante.</span><span class="sxs-lookup"><span data-stu-id="29023-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="29023-124">Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="29023-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="29023-125">Dans la plupart des cas, vous devez accéder à la valeur avec `Await` au lieu d’accéder directement à la propriété.</span><span class="sxs-lookup"><span data-stu-id="29023-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="29023-126">Les instructions d’affichage dans le code suivant vérifient que les valeurs de la variable `result1`, de la variable `result2` et de la propriété `Result` sont identiques.</span><span class="sxs-lookup"><span data-stu-id="29023-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="29023-127">N’oubliez pas que `Result` est une propriété bloquante et que vous ne devez pas y accéder avant que sa tâche soit attendue.</span><span class="sxs-lookup"><span data-stu-id="29023-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a> <span data-ttu-id="29023-128">Type de retour Task</span><span class="sxs-lookup"><span data-stu-id="29023-128">Task Return Type</span></span>

<span data-ttu-id="29023-129">Les méthodes async qui ne contiennent pas d’instruction return ou qui en contiennent une qui ne retourne pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="29023-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="29023-130">Ces méthodes seraient des [sous](../../language-features/procedures/sub-procedures.md) -procédures si elles ont été écrites pour s’exécuter de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="29023-130">Such methods would be [Sub](../../language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="29023-131">Si vous utilisez un type de retour `Task` pour une méthode async, une méthode d’appel peut utiliser un opérateur `Await` pour suspendre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.</span><span class="sxs-lookup"><span data-stu-id="29023-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="29023-132">Dans l’exemple suivant, la méthode async `Task_MethodAsync` ne contient pas d’instruction return.</span><span class="sxs-lookup"><span data-stu-id="29023-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="29023-133">Par conséquent, vous spécifiez le type de retour `Task` pour la méthode, ce qui permet à `Task_MethodAsync` d’être attendu.</span><span class="sxs-lookup"><span data-stu-id="29023-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="29023-134">La définition du type `Task` n’inclut pas de propriété `Result` pour stocker une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="29023-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

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

<span data-ttu-id="29023-135">`Task_MethodAsync` est appelé et attendu à l’aide d’une instruction await et non d’une expression await, à l’instar de l’instruction d’appel d’une méthode `Sub` synchrone ou d’une méthode qui retourne une valeur void.</span><span class="sxs-lookup"><span data-stu-id="29023-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="29023-136">`Await`Dans ce cas, l’application d’un opérateur ne produit pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="29023-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="29023-137">Le code suivant appelle et attend la méthode `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="29023-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="29023-138">Comme dans l' <xref:System.Threading.Tasks.Task%601> exemple précédent, vous pouvez séparer l’appel à `Task_MethodAsync` de l’application d’un `Await` opérateur, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29023-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="29023-139">Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.</span><span class="sxs-lookup"><span data-stu-id="29023-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="29023-140">Le code suivant sépare l’appel à `Task_MethodAsync` de l’attente de la tâche que retourne `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="29023-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a><span data-ttu-id="29023-141">Type de retour void</span><span class="sxs-lookup"><span data-stu-id="29023-141">Void Return Type</span></span>

<span data-ttu-id="29023-142">L’utilisation principale des `Sub` procédures est dans les gestionnaires d’événements, où il n’y a aucun type de retour (appelé type de retour void dans d’autres langages).</span><span class="sxs-lookup"><span data-stu-id="29023-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="29023-143">Le retour de type void peut aussi être utilisé pour remplacer les méthodes qui retournent void ou pour les méthodes qui effectuent des activités considérées comme autonomes après activation (« Fire and Forget ».</span><span class="sxs-lookup"><span data-stu-id="29023-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="29023-144">Toutefois, vous devez retourner un type `Task` dans la mesure du possible, car une méthode async qui retourne un type void ne peut pas être attendue.</span><span class="sxs-lookup"><span data-stu-id="29023-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="29023-145">Tout appelant d’une telle méthode doit pouvoir continuer jusqu’à l’achèvement sans attendre que la méthode async soit terminée, et l’appelant doit être indépendant des valeurs ou des exceptions générées par la méthode async.</span><span class="sxs-lookup"><span data-stu-id="29023-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="29023-146">L’appelant d’une méthode async qui retourne une valeur void ne peut pas intercepter les exceptions levées à partir de la méthode, et ces exceptions non gérées peuvent entraîner l’échec de votre application.</span><span class="sxs-lookup"><span data-stu-id="29023-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="29023-147">Si une exception se produit dans une méthode asyn qui retourne <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, l’exception est stockée dans la tâche retournée et est à nouveau levée pendant l’attente de la tâche.</span><span class="sxs-lookup"><span data-stu-id="29023-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="29023-148">Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.</span><span class="sxs-lookup"><span data-stu-id="29023-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="29023-149">Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez la page [Instruction Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29023-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="29023-150">Le code suivant définit un gestionnaire d’événements asynchrones.</span><span class="sxs-lookup"><span data-stu-id="29023-150">The following code defines an async event handler.</span></span>

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

## <a name="complete-example"></a><a name="BKMK_Example"></a><span data-ttu-id="29023-151">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="29023-151">Complete Example</span></span>

<span data-ttu-id="29023-152">Le projet Windows Presentation Foundation (WPF) suivant contient les exemples de code de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="29023-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="29023-153">Pour exécuter le projet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="29023-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="29023-154">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29023-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="29023-155">Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="29023-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="29023-156">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="29023-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="29023-157">Dans la catégorie **installé**, **modèles** , choisissez **Visual Basic**, puis choisissez **Windows**.</span><span class="sxs-lookup"><span data-stu-id="29023-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="29023-158">Choisissez **Application WPF** dans la liste des types de projets.</span><span class="sxs-lookup"><span data-stu-id="29023-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="29023-159">Entrez `AsyncReturnTypes` comme nom du projet, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="29023-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="29023-160">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="29023-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="29023-161">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="29023-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="29023-162">Si l’onglet n’est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="29023-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="29023-163">Dans la fenêtre **XAML** de MainWindow.xaml, remplacez le code existant par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29023-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="29023-164">Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la fenêtre **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="29023-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="29023-165">Dans **Explorateur de solutions**, ouvrez le menu contextuel de MainWindow. Xaml. vb, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="29023-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="29023-166">Remplacez le code situé dans MainWindow.xaml.vb par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29023-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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

9. <span data-ttu-id="29023-167">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="29023-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="29023-168">La sortie suivante doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="29023-168">The following output should appear:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29023-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29023-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="29023-170">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29023-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="29023-171">Flux de contrôle dans les programmes Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29023-171">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
- [<span data-ttu-id="29023-172">Asynchrone</span><span class="sxs-lookup"><span data-stu-id="29023-172">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="29023-173">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="29023-173">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
