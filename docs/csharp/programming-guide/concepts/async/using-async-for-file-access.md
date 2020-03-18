---
title: Utilisation d’async pour l’accès aux fichiers (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595537"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="26212-102">Utilisation d’async pour l’accès aux fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="26212-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="26212-103">Vous pouvez utiliser la fonctionnalité Async pour accéder à des fichiers.</span><span class="sxs-lookup"><span data-stu-id="26212-103">You can use the async feature to access files.</span></span> <span data-ttu-id="26212-104">La fonctionnalité async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="26212-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="26212-105">Pour rendre le code synchrone asynchrone, il vous suffit d’appeler une méthode asynchrone au lieu d’une méthode synchrone, puis d’ajouter quelques mots clés au code.</span><span class="sxs-lookup"><span data-stu-id="26212-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="26212-106">Vous pouvez considérer les raisons suivantes pour ajouter de l'asynchrone aux appels d'accès aux fichiers :</span><span class="sxs-lookup"><span data-stu-id="26212-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="26212-107">L'asynchronisme rend les applications d'interface utilisateur plus réactives parce que le thread d'interface utilisateur qui lance l'exécution peut effectuer d'autres tâches.</span><span class="sxs-lookup"><span data-stu-id="26212-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="26212-108">Si le thread d’interface utilisateur doit exécuter du code qui prend du temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut figer jusqu’à ce que l’E/S soit terminée et que le thread d’interface utilisateur puisse traiter à nouveau des entrées au clavier et à la souris et d’autres événements.</span><span class="sxs-lookup"><span data-stu-id="26212-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="26212-109">L'asynchronisme améliore l'extensibilité d'ASP.NET et d'autres applications serveur en réduisant le besoin de threads.</span><span class="sxs-lookup"><span data-stu-id="26212-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="26212-110">Si l'application utilise un thread dédié par réponse et que mille demandes sont traitées simultanément, mille threads sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="26212-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="26212-111">Les opérations asynchrones n'ont souvent pas besoin d'utiliser un thread pendant l'attente.</span><span class="sxs-lookup"><span data-stu-id="26212-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="26212-112">Elles utilisent le thread de terminaison d’E/S existant brièvement à la fin.</span><span class="sxs-lookup"><span data-stu-id="26212-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="26212-113">La latence d'une opération d'accès à un fichier peut être très basse sous les conditions actuelles, mais la latence peut considérablement augmenter à l'avenir.</span><span class="sxs-lookup"><span data-stu-id="26212-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="26212-114">Par exemple, un fichier peut être déplacé vers un serveur qui se trouve à travers le monde.</span><span class="sxs-lookup"><span data-stu-id="26212-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="26212-115">La charge mémoire supplémentaire pour l'utilisation de la fonctionnalité Async est faible.</span><span class="sxs-lookup"><span data-stu-id="26212-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="26212-116">Les tâches asynchrones peuvent facilement être exécutées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="26212-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="26212-117">Exécution des exemples</span><span class="sxs-lookup"><span data-stu-id="26212-117">Running the Examples</span></span>  
 <span data-ttu-id="26212-118">Pour exécuter les exemples de cette rubrique, vous pouvez créer une **application WPF** ou une **application Windows Forms**, puis ajouter un **bouton**.</span><span class="sxs-lookup"><span data-stu-id="26212-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="26212-119">Dans l’événement `Click` du bouton, ajoutez un appel à la première méthode de chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="26212-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="26212-120">Dans les exemples qui suivent, incluez les instructions `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="26212-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="26212-121">Utilisation de la classe FileStream</span><span class="sxs-lookup"><span data-stu-id="26212-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="26212-122">Les exemples de cette rubrique utilisent la classe <xref:System.IO.FileStream>, avec une option qui provoque une E/S asynchrone au niveau du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="26212-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="26212-123">En utilisant cette option, vous pouvez éviter de bloquer un thread de ThreadPool dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="26212-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="26212-124">Pour l’activer, spécifiez l’argument `useAsync=true` ou `options=FileOptions.Asynchronous` dans l’appel de constructeur.</span><span class="sxs-lookup"><span data-stu-id="26212-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="26212-125">Vous ne pouvez pas utiliser cette option avec <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> si vous les ouvrez directement en spécifiant un chemin de fichier.</span><span class="sxs-lookup"><span data-stu-id="26212-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="26212-126">Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream> ouvert par la classe <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="26212-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="26212-127">Notez que les appels asynchrones sont plus rapides dans des applications d’interface utilisateur même si un thread du ThreadPool est bloqué, car le thread d’interface utilisateur n’est pas bloqué pendant l’attente.</span><span class="sxs-lookup"><span data-stu-id="26212-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="26212-128">Écriture de texte</span><span class="sxs-lookup"><span data-stu-id="26212-128">Writing Text</span></span>  
 <span data-ttu-id="26212-129">L’exemple suivant écrit du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="26212-129">The following example writes text to a file.</span></span> <span data-ttu-id="26212-130">À chaque instruction await, la méthode s'arrête immédiatement.</span><span class="sxs-lookup"><span data-stu-id="26212-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="26212-131">Quand l’E/S de fichier est terminée, la méthode reprend à l’instruction qui suit l’instruction await.</span><span class="sxs-lookup"><span data-stu-id="26212-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="26212-132">Notez que le modificateur async se trouve dans la définition des méthodes qui utilisent l'instruction await.</span><span class="sxs-lookup"><span data-stu-id="26212-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="26212-133">L’exemple d’origine comprend l’instruction `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, qui est une contraction des deux instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="26212-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="26212-134">La première instruction retourne une tâche et provoque le début du traitement du fichier.</span><span class="sxs-lookup"><span data-stu-id="26212-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="26212-135">La deuxième instruction avec await provoque la fin immédiate de la méthode et retourne une tâche différente.</span><span class="sxs-lookup"><span data-stu-id="26212-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="26212-136">Quand le traitement du fichier se termine plus loin, l’exécution retourne à l’instruction qui suit l’attente.</span><span class="sxs-lookup"><span data-stu-id="26212-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="26212-137">Pour plus d’informations, consultez [Flux de contrôle dans les programmes Async (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="26212-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="26212-138">Lecture de texte</span><span class="sxs-lookup"><span data-stu-id="26212-138">Reading Text</span></span>  
 <span data-ttu-id="26212-139">L'exemple suivant lit du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="26212-139">The following example reads text from a file.</span></span> <span data-ttu-id="26212-140">Le texte est mis en mémoire tampon et, dans cet exemple, est placé dans un <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="26212-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="26212-141">Contrairement à l’exemple précédent, l’évaluation de l’instruction await génère une valeur.</span><span class="sxs-lookup"><span data-stu-id="26212-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="26212-142">La méthode <xref:System.IO.Stream.ReadAsync%2A> retourne un <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, de sorte que l’évaluation de l’expression await génère une valeur `Int32` (`numRead`) une fois l’opération effectuée.</span><span class="sxs-lookup"><span data-stu-id="26212-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="26212-143">Pour plus d’informations, consultez [Types de retour Async (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="26212-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="26212-144">E/S asynchrones en parallèle</span><span class="sxs-lookup"><span data-stu-id="26212-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="26212-145">L’exemple suivant illustre le traitement en parallèle en écrivant 10 fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="26212-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="26212-146">Pour chaque fichier, la méthode <xref:System.IO.Stream.WriteAsync%2A> retourne une tâche qui est ensuite ajoutée à une liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="26212-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="26212-147">L’instruction `await Task.WhenAll(tasks);` quitte la méthode et reprend dans cette dernière quand le traitement du fichier est terminé pour toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="26212-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="26212-148">L’exemple ferme toutes les instances de <xref:System.IO.FileStream> dans un bloc `finally` une fois les tâches effectuées.</span><span class="sxs-lookup"><span data-stu-id="26212-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="26212-149">Si chaque `FileStream` était plutôt créé dans une instruction `using`, `FileStream` pourrait être libéré avant que la tâche ne soit terminée.</span><span class="sxs-lookup"><span data-stu-id="26212-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="26212-150">Notez que toutes les améliorations de performances sont presque entièrement dues au traitement parallèle et non au traitement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="26212-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="26212-151">Les avantages du mode asynchrone sont qu'il n'attache pas plusieurs threads et qu'il ne bloque pas le thread d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="26212-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="26212-152">Quand vous utilisez les méthodes <xref:System.IO.Stream.WriteAsync%2A> et <xref:System.IO.Stream.ReadAsync%2A>, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler l’opération en cours de route.</span><span class="sxs-lookup"><span data-stu-id="26212-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="26212-153">Pour plus d’informations, consultez [Réglage de votre application Async (C#)](./fine-tuning-your-async-application.md) et [Annulation dans les threads managés](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="26212-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26212-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26212-154">See also</span></span>

- [<span data-ttu-id="26212-155">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="26212-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="26212-156">Types de retour async (C#)</span><span class="sxs-lookup"><span data-stu-id="26212-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="26212-157">Flux de contrôle dans les programmes Async (C)</span><span class="sxs-lookup"><span data-stu-id="26212-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
