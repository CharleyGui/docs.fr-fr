---
title: Await, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d3bfafaa696955422c381aa1c17bc96591b44985
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961996"
---
# <a name="await-operator-visual-basic"></a>Await, opérateur (Visual Basic)
Vous appliquez l' `Await` opérateur à un opérande dans une méthode asynchrone ou une expression lambda pour interrompre l’exécution de la méthode jusqu’à ce que la tâche attendue se termine. La tâche représente un travail en cours.  
  
 La méthode dans laquelle `Await` est utilisé doit avoir un modificateur [Async](../../../visual-basic/language-reference/modifiers/async.md) . Cette méthode, définie à l’aide du modificateur `Async` et contenant généralement une ou plusieurs expressions `Await`, est appelée *méthode async*.  
  
> [!NOTE]
> Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012. Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 En général, la tâche à laquelle vous appliquez `Await` l’opérateur est la valeur de retour d’un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](https://go.microsoft.com/fwlink/?LinkId=204847), <xref:System.Threading.Tasks.Task> c’est-à-dire <xref:System.Threading.Tasks.Task%601>, ou.  
  
 Dans le code suivant, la <xref:System.Net.Http.HttpClient> méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retourne `getContentsTask`, a `Task(Of Byte())`. La tâche est une promesse de produire le tableau d’octets réel lorsque l’opération est terminée. L'opérateur `Await` est appliqué à `getContentsTask` pour suspendre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé. Entre-temps, le contrôle revient à l'appelant de `SumPageSizesAsync`. Quand `getContentsTask` est terminé, l'expression `Await` s'évalue en tableau d'octets.  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
> Pour un exemple complet, consultez [Procédure pas à pas : Accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger l’exemple à partir des [exemples de code pour les développeurs](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) sur le site web de Microsoft. L'exemple est dans le projet AsyncWalkthrough_HttpClient.  
  
 Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task(Of TResult)`, le type de l' `Await` expression est TResult. Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task`, l' `Await` expression ne retourne pas de valeur. L'exemple suivant illustre la différence.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 Une `Await` expression ou une instruction ne bloque pas le thread sur lequel elle s’exécute. Au lieu de cela, il force le compilateur à inscrire le reste de la méthode Async, `Await` après l’expression, en tant que continuation sur la tâche attendue. Le contrôle revient alors à l'appelant de la méthode async. Quand la tâche est terminée, elle appelle sa continuation et l'exécution de la méthode async reprend là où elle s'était arrêtée.  
  
 Une `Await` expression peut se produire uniquement dans le corps d’une méthode immédiatement englobante ou d’une expression lambda qui est `Async` marquée par un modificateur. Le terme *await* sert de mot clé uniquement dans ce contexte. Partout ailleurs, il est interprété en tant qu'identificateur. Dans une méthode Async ou une expression lambda, `Await` une expression ne peut pas se produire dans une expression `catch` de `finally` requête, dans le bloc ou d’une [tentative... Catch... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , dans l’expression de variable de contrôle de `For` boucle `For Each` d’une boucle ou, ou dans le corps d’une instruction [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .  
  
## <a name="exceptions"></a>Exceptions  
 La plupart des méthodes async retournent un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final. L'opérateur `Await` accède à ces propriétés.  
  
 Si vous attendez une méthode async retournant des tâches qui lève une exception, l'opérateur `Await` lève de nouveau l'exception.  
  
 Si vous attendez une méthode Async retournant des tâches qui est annulée, `Await` l’opérateur lève de nouveau <xref:System.OperationCanceledException>une exception.  
  
 Une tâche qui se trouve dans un état d’erreur peut refléter plusieurs exceptions.  Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quand vous attendez une telle tâche, l’opération await lève à nouveau une seule des exceptions. Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.  
  
 Pour obtenir des exemples de gestion des erreurs dans les méthodes Async, consultez [try... Catch... Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Exemples  
 L'exemple Windows Forms suivant illustre l'utilisation de `Await` dans une méthode async, `WaitAsynchronouslyAsync`. Comparez le comportement de cette méthode avec celui de `WaitSynchronously`. Sans opérateur, `WaitSynchronously` s’exécute de manière synchrone en `Async` dépit de l’utilisation du modificateur dans sa définition et d' <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> un appel à dans son corps. `Await`  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Procédure pas à pas : Accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
