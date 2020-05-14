---
title: Utilisation d’async pour l’accès aux fichiers (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 8e0a62c2263ed3fd11eb4accb54978ef439ac010
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396962"
---
# <a name="using-async-for-file-access-c"></a>Utilisation d’async pour l’accès aux fichiers (C#)
Vous pouvez utiliser la fonctionnalité Async pour accéder à des fichiers. La fonctionnalité async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda. Pour rendre le code synchrone asynchrone, il vous suffit d’appeler une méthode asynchrone au lieu d’une méthode synchrone, puis d’ajouter quelques mots clés au code.  
  
 Vous pouvez considérer les raisons suivantes pour ajouter de l'asynchrone aux appels d'accès aux fichiers :  
  
- L'asynchronisme rend les applications d'interface utilisateur plus réactives parce que le thread d'interface utilisateur qui lance l'exécution peut effectuer d'autres tâches. Si le thread d’interface utilisateur doit exécuter du code qui prend du temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut figer jusqu’à ce que l’E/S soit terminée et que le thread d’interface utilisateur puisse traiter à nouveau des entrées au clavier et à la souris et d’autres événements.  
  
- L'asynchronisme améliore l'extensibilité d'ASP.NET et d'autres applications serveur en réduisant le besoin de threads. Si l'application utilise un thread dédié par réponse et que mille demandes sont traitées simultanément, mille threads sont nécessaires. Les opérations asynchrones n'ont souvent pas besoin d'utiliser un thread pendant l'attente. Elles utilisent le thread de terminaison d’E/S existant brièvement à la fin.  
  
- La latence d'une opération d'accès à un fichier peut être très basse sous les conditions actuelles, mais la latence peut considérablement augmenter à l'avenir. Par exemple, un fichier peut être déplacé vers un serveur qui se trouve à travers le monde.  
  
- La charge mémoire supplémentaire pour l'utilisation de la fonctionnalité Async est faible.  
  
- Les tâches asynchrones peuvent facilement être exécutées en parallèle.  
  
## <a name="running-the-examples"></a>Exécution des exemples  
 Pour exécuter les exemples de cette rubrique, vous pouvez créer une **application WPF** ou une **application Windows Forms**, puis ajouter un **bouton**. Dans l’événement `Click` du bouton, ajoutez un appel à la première méthode de chaque exemple.  
  
 Dans les exemples suivants, incluez les `using` directives suivantes.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Utilisation de la classe FileStream  
 Les exemples de cette rubrique utilisent la classe <xref:System.IO.FileStream>, avec une option qui provoque une E/S asynchrone au niveau du système d’exploitation. En utilisant cette option, vous pouvez éviter de bloquer un thread de ThreadPool dans de nombreux cas. Pour l’activer, spécifiez l’argument `useAsync=true` ou `options=FileOptions.Asynchronous` dans l’appel de constructeur.  
  
 Vous ne pouvez pas utiliser cette option avec <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> si vous les ouvrez directement en spécifiant un chemin de fichier. Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream> ouvert par la classe <xref:System.IO.FileStream>. Notez que les appels asynchrones sont plus rapides dans des applications d’interface utilisateur même si un thread du ThreadPool est bloqué, car le thread d’interface utilisateur n’est pas bloqué pendant l’attente.  
  
## <a name="writing-text"></a>Écriture de texte  
 L’exemple suivant écrit du texte dans un fichier. À chaque instruction await, la méthode s'arrête immédiatement. Quand l’E/S de fichier est terminée, la méthode reprend à l’instruction qui suit l’instruction await. Notez que le modificateur async se trouve dans la définition des méthodes qui utilisent l'instruction await.  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 L’exemple d’origine comprend l’instruction `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, qui est une contraction des deux instructions suivantes :  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 La première instruction retourne une tâche et provoque le début du traitement du fichier. La deuxième instruction avec await provoque la fin immédiate de la méthode et retourne une tâche différente. Quand le traitement du fichier se termine plus loin, l’exécution retourne à l’instruction qui suit l’attente. Pour plus d’informations, consultez [Flux de contrôle dans les programmes Async (C#)](./control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Lecture de texte  
 L'exemple suivant lit du texte dans un fichier. Le texte est mis en mémoire tampon et, dans cet exemple, est placé dans un <xref:System.Text.StringBuilder>. Contrairement à l’exemple précédent, l’évaluation de l’instruction await génère une valeur. La méthode <xref:System.IO.Stream.ReadAsync%2A> retourne un <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, de sorte que l’évaluation de l’expression await génère une valeur `Int32` (`numRead`) une fois l’opération effectuée. Pour plus d’informations, consultez [Types de retour Async (C#)](./async-return-types.md).  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a>E/S asynchrones en parallèle  
 L’exemple suivant illustre le traitement en parallèle en écrivant 10 fichiers texte. Pour chaque fichier, la méthode <xref:System.IO.Stream.WriteAsync%2A> retourne une tâche qui est ensuite ajoutée à une liste des tâches. L’instruction `await Task.WhenAll(tasks);` quitte la méthode et reprend dans cette dernière quand le traitement du fichier est terminé pour toutes les tâches.  
  
 L’exemple ferme toutes les instances de <xref:System.IO.FileStream> dans un bloc `finally` une fois les tâches effectuées. Si chaque `FileStream` était plutôt créé dans une instruction `using`, `FileStream` pourrait être libéré avant que la tâche ne soit terminée.  
  
 Notez que toutes les améliorations de performances sont presque entièrement dues au traitement parallèle et non au traitement asynchrone. Les avantages du mode asynchrone sont qu'il n'attache pas plusieurs threads et qu'il ne bloque pas le thread d'interface utilisateur.  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 Quand vous utilisez les méthodes <xref:System.IO.Stream.WriteAsync%2A> et <xref:System.IO.Stream.ReadAsync%2A>, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler l’opération en cours de route. Pour plus d’informations, consultez [Réglage de votre application Async (C#)](./fine-tuning-your-async-application.md) et [Annulation dans les threads managés](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (C#)](./index.md)
- [Types de retour async (C#)](./async-return-types.md)
- [Workflow de contrôle dans les programmes Async (C#)](./control-flow-in-async-programs.md)
