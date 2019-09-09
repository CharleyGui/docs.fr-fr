---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 6a3d9c8eb8e5929796683bd0bb50159ca0c69f1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959871"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
Le `Async` modificateur indique que la méthode ou l' [expression lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) qu’il modifie est asynchrone. Ces méthodes sont appelées *méthodes Async*.  
  
 Une méthode async offre un moyen pratique d'exécuter un travail potentiellement long sans bloquer le thread de l'appelant. L’appelant d’une méthode Async peut reprendre son travail sans attendre la fin de la méthode Async.  
  
> [!NOTE]
> Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012. Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 L’exemple suivant illustre la structure d’une méthode Async. Par Convention, les noms de méthodes Async se terminent par « Async ».  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 En règle générale, une méthode modifiée `Async` par le mot clé contient au moins une expression ou une instruction [await](../../../visual-basic/language-reference/modifiers/async.md) . La méthode s’exécute de façon synchrone jusqu’à ce `Await`qu’elle atteigne le premier, point où elle s’interrompt jusqu’à ce que la tâche attendue se termine. Dans le même temps, le contrôle est retourné à l’appelant de la méthode. Si la méthode ne contient pas `Await` une expression ou une instruction, la méthode n’est pas suspendue et s’exécute en tant que méthode synchrone. Un avertissement du compilateur vous signale toutes les méthodes Async qui `Await` ne contiennent pas, car cette situation peut indiquer une erreur. Pour plus d’informations, consultez l' [Erreur du compilateur](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 Le `Async` mot clé est un mot clé non réservé. Il s’agit d’un mot clé lorsqu’il modifie une méthode ou une expression lambda. Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## <a name="return-types"></a>Types de retours  
 Une méthode Async est soit une [sous](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) -procédure, soit une procédure de [fonction](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) qui a un type <xref:System.Threading.Tasks.Task> de <xref:System.Threading.Tasks.Task%601>retour ou. La méthode ne peut pas déclarer de paramètres [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .  
  
 Vous spécifiez `Task(Of TResult)` pour le type de retour d’une méthode Async si l’instruction [Return](../../../visual-basic/language-reference/statements/return-statement.md) de la méthode a un opérande de type TResult. Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée. Autrement dit, un appel à la méthode `Task`retourne, mais lorsque la `Task` est terminée, toute `Await` instruction qui attend le `Task` ne produit pas de valeur de résultat.  
  
 Les sous-routines Async sont principalement utilisées pour définir des gestionnaires d' `Sub` événements dans lesquels une procédure est requise. L’appelant d’une sous-routine Async ne peut pas l’attendre et ne peut pas intercepter les exceptions levées par la méthode.  
  
 Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemples  
 Les exemples suivants illustrent un gestionnaire d’événements asynchrones, une expression lambda Async et une méthode Async. Pour obtenir un exemple complet qui utilise ces éléments, [consultez Procédure pas à pas : Accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger le code de procédure à partir des [Exemples de code du développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")  
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
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Procédure pas à pas : Accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
