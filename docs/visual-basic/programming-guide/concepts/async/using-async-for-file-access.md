---
title: Utiliser Async pour l'accès aux fichiers
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 2e7fa4a78363a08f2ff25e6a961868e85994e200
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077356"
---
# <a name="using-async-for-file-access-visual-basic"></a>Utilisation d’async pour l’accès aux fichiers (Visual Basic)

Vous pouvez utiliser la fonctionnalité Async pour accéder aux fichiers. La fonctionnalité Async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda. Pour rendre le code synchrone asynchrone, il vous suffit d’appeler une méthode asynchrone au lieu d’une méthode synchrone, puis d’ajouter quelques mots clés au code.  
  
 Vous pouvez considérer les raisons suivantes pour ajouter de l'asynchrone aux appels d'accès aux fichiers :  
  
- L'asynchronisme rend les applications d'interface utilisateur plus réactives parce que le thread d'interface utilisateur qui lance l'exécution peut effectuer d'autres tâches. Si le thread d’interface utilisateur doit exécuter du code qui prend du temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut figer jusqu’à ce que l’E/S soit terminée et que le thread d’interface utilisateur puisse traiter à nouveau des entrées au clavier et à la souris et d’autres événements.  
  
- L'asynchronisme améliore l'extensibilité d'ASP.NET et d'autres applications serveur en réduisant le besoin de threads. Si l'application utilise un thread dédié par réponse et que mille demandes sont traitées simultanément, mille threads sont nécessaires. Les opérations asynchrones n'ont souvent pas besoin d'utiliser un thread pendant l'attente. Elles utilisent le thread de terminaison d’E/S existant brièvement à la fin.  
  
- La latence d'une opération d'accès à un fichier peut être très basse sous les conditions actuelles, mais la latence peut considérablement augmenter à l'avenir. Par exemple, un fichier peut être déplacé vers un serveur qui se trouve à travers le monde.  
  
- La charge mémoire supplémentaire pour l'utilisation de la fonctionnalité Async est faible.  
  
- Les tâches asynchrones peuvent facilement être exécutées en parallèle.  
  
## <a name="running-the-examples"></a>Exécution des exemples  

 Pour exécuter les exemples de cette rubrique, vous pouvez créer une **application WPF** ou une **application Windows Forms**, puis ajouter un **bouton**. Dans l’événement `Click` du bouton, ajoutez un appel à la première méthode de chaque exemple.  
  
 Dans les exemples qui suivent, incluez les instructions `Imports` suivantes.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Utilisation de la classe FileStream  

 Les exemples de cette rubrique utilisent la classe <xref:System.IO.FileStream>, avec une option qui provoque une E/S asynchrone au niveau du système d’exploitation. En utilisant cette option, vous pouvez éviter de bloquer un thread de ThreadPool dans de nombreux cas. Pour l’activer, spécifiez l’argument `useAsync=true` ou `options=FileOptions.Asynchronous` dans l’appel de constructeur.  
  
 Vous ne pouvez pas utiliser cette option avec <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> si vous les ouvrez directement en spécifiant un chemin de fichier. Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream> ouvert par la classe <xref:System.IO.FileStream>. Notez que les appels asynchrones sont plus rapides dans des applications d’interface utilisateur même si un thread du ThreadPool est bloqué, car le thread d’interface utilisateur n’est pas bloqué pendant l’attente.  
  
## <a name="writing-text"></a>Écriture de texte  

 L’exemple suivant écrit du texte dans un fichier. À chaque instruction await, la méthode s'arrête immédiatement. Quand l’E/S de fichier est terminée, la méthode reprend à l’instruction qui suit l’instruction await. Notez que le modificateur async se trouve dans la définition des méthodes qui utilisent l'instruction await.  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 L’exemple d’origine comprend l’instruction `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, qui est une contraction des deux instructions suivantes :  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 La première instruction retourne une tâche et provoque le début du traitement du fichier. La deuxième instruction avec await provoque la fin immédiate de la méthode et retourne une tâche différente. Quand le traitement du fichier se termine plus loin, l’exécution retourne à l’instruction qui suit l’attente. Pour plus d’informations, consultez  [Control flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Lecture de texte  

 L'exemple suivant lit du texte dans un fichier. Le texte est mis en mémoire tampon et, dans cet exemple, est placé dans un <xref:System.Text.StringBuilder>. Contrairement à l’exemple précédent, l’évaluation de l’instruction await génère une valeur. La méthode <xref:System.IO.Stream.ReadAsync%2A> retourne un <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, de sorte que l’évaluation de l’expression await génère une valeur `Int32` (`numRead`) une fois l’opération effectuée. Pour plus d’informations, consultez [types de retour Async (Visual Basic)](async-return-types.md).  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>E/S asynchrones en parallèle  

 L’exemple suivant illustre le traitement en parallèle en écrivant 10 fichiers texte. Pour chaque fichier, la méthode <xref:System.IO.Stream.WriteAsync%2A> retourne une tâche qui est ensuite ajoutée à une liste des tâches. L’instruction `Await Task.WhenAll(tasks)` quitte la méthode et reprend dans cette dernière quand le traitement du fichier est terminé pour toutes les tâches.  
  
 L’exemple ferme toutes les instances de <xref:System.IO.FileStream> dans un bloc `Finally` une fois les tâches effectuées. Si chaque `FileStream` était plutôt créé dans une instruction `Imports`, `FileStream` pourrait être libéré avant que la tâche ne soit terminée.  
  
 Notez que toutes les améliorations de performances sont presque entièrement dues au traitement parallèle et non au traitement asynchrone. Les avantages du mode asynchrone sont qu'il n'attache pas plusieurs threads et qu'il ne bloque pas le thread d'interface utilisateur.  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 Quand vous utilisez les méthodes <xref:System.IO.Stream.WriteAsync%2A> et <xref:System.IO.Stream.ReadAsync%2A>, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler l’opération en cours de route. Pour plus d’informations, consultez [réglage de votre application Async (Visual Basic)](fine-tuning-your-async-application.md) et [annulation dans les threads managés](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (Visual Basic)](index.md)
- [Types de retour Async (Visual Basic)](async-return-types.md)
- [Flux de contrôle dans les programmes Async (Visual Basic)](control-flow-in-async-programs.md)
