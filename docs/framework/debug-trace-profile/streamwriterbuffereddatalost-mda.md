---
title: streamWriterBufferedDataLost (MDA)
description: Passez en revue l’Assistant Débogage managé (MDA) streamWriterBufferedDataLost, qui peut s’activer si un StreamWriter n’écrit pas les 1 à 4 dernières Ko de données dans un fichier.
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
ms.openlocfilehash: 23a8146bfa5acc08000e689917abb844c5540fec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267076"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="c0166-103">streamWriterBufferedDataLost (MDA)</span><span class="sxs-lookup"><span data-stu-id="c0166-103">streamWriterBufferedDataLost MDA</span></span>

<span data-ttu-id="c0166-104">L’Assistant Débogage managé `streamWriterBufferedDataLost` est activé lors d’une écriture dans <xref:System.IO.StreamWriter>, mais la méthode <xref:System.IO.StreamWriter.Flush%2A> ou <xref:System.IO.StreamWriter.Close%2A> n’est pas appelée par la suite avant la destruction de l’instance du <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="c0166-104">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="c0166-105">Quand cet Assistant Débogage managé est activé, le runtime détermine s’il existe encore des données mises en mémoire tampon dans <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="c0166-105">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="c0166-106">Si c’est le cas, l’Assistant Débogage managé est activé.</span><span class="sxs-lookup"><span data-stu-id="c0166-106">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="c0166-107">L’appel aux méthodes <xref:System.GC.Collect%2A> et <xref:System.GC.WaitForPendingFinalizers%2A> peut forcer des finaliseurs à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c0166-107">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="c0166-108">Sinon, les finaliseurs s’exécuteront à des moments apparemment arbitraires, voire pas du tout lors de la sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="c0166-108">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="c0166-109">L’exécution explicite des finaliseurs avec cet Assistant Débogage managé activé aide à reproduire ce type de problème de façon plus fiable.</span><span class="sxs-lookup"><span data-stu-id="c0166-109">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c0166-110">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c0166-110">Symptoms</span></span>  

 <span data-ttu-id="c0166-111">Un <xref:System.IO.StreamWriter> n’écrit pas les 1 à 4 derniers kilo-octets de données dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="c0166-111">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c0166-112">Cause</span><span class="sxs-lookup"><span data-stu-id="c0166-112">Cause</span></span>  

 <span data-ttu-id="c0166-113">Le <xref:System.IO.StreamWriter> met les données en mémoire tampon en interne, ce qui exige un appel à la méthode <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> pour écrire les données mises en mémoire tampon dans le magasin de données sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="c0166-113">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="c0166-114">Si <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> n’est pas appelée au moment opportun, les données mises en mémoire tampon dans l’instance de <xref:System.IO.StreamWriter> peuvent ne pas être écrites comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c0166-114">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="c0166-115">L’exemple suivant illustre un code mal écrit que cet Assistant Débogage managé doit intercepter.</span><span class="sxs-lookup"><span data-stu-id="c0166-115">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="c0166-116">Le code précédent activera cet Assistant Débogage managé de façon plus fiable si un garbage collection est déclenché avant d’être suspendu jusqu’au terme de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="c0166-116">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="c0166-117">Pour repérer ce type de problème, vous pouvez ajouter le code suivant à la fin de la méthode précédente dans une version Debug.</span><span class="sxs-lookup"><span data-stu-id="c0166-117">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="c0166-118">Cela permet d’activer systématiquement l’Assistant Débogage managé même si cela ne résout évidemment pas la cause du problème.</span><span class="sxs-lookup"><span data-stu-id="c0166-118">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="c0166-119">Résolution</span><span class="sxs-lookup"><span data-stu-id="c0166-119">Resolution</span></span>  

 <span data-ttu-id="c0166-120">Veillez à appeler <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> avant de fermer une application ou tout bloc de code possédant une instance de <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="c0166-120">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="c0166-121">Pour ce faire, une des solutions les plus efficaces consiste à créer l’instance avec un bloc `using` C# (`Using` en Visual Basic) qui garantit l’appel à la méthode <xref:System.IO.StreamWriter.Dispose%2A> pour le writer, ce qui permet de fermer correctement l’instance.</span><span class="sxs-lookup"><span data-stu-id="c0166-121">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="c0166-122">Le code suivant illustre la même solution, à l’aide de `try/finally` au lieu d’`using`.</span><span class="sxs-lookup"><span data-stu-id="c0166-122">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
```csharp
StreamWriter sw;  
try
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 <span data-ttu-id="c0166-123">Si aucune de ces solutions ne peut être utilisée (par exemple, si un <xref:System.IO.StreamWriter> est stocké dans une variable statique et que vous ne pouvez pas exécuter facilement du code à la fin de sa durée de vie), l’appel à <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> après sa dernière utilisation ou l’affectation de la valeur `true` à la propriété <xref:System.IO.StreamWriter.AutoFlush%2A> avant sa première utilisation doit éviter ce problème.</span><span class="sxs-lookup"><span data-stu-id="c0166-123">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c0166-124">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c0166-124">Effect on the Runtime</span></span>  

 <span data-ttu-id="c0166-125">Cet Assistant Débogage managé n'a aucun effet sur le runtime.</span><span class="sxs-lookup"><span data-stu-id="c0166-125">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c0166-126">Output</span><span class="sxs-lookup"><span data-stu-id="c0166-126">Output</span></span>  

 <span data-ttu-id="c0166-127">Un message signale cette violation.</span><span class="sxs-lookup"><span data-stu-id="c0166-127">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c0166-128">Configuration</span><span class="sxs-lookup"><span data-stu-id="c0166-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0166-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0166-129">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="c0166-130">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="c0166-130">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
