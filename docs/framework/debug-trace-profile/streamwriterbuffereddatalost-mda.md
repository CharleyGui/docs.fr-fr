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
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost (MDA)

L’Assistant Débogage managé `streamWriterBufferedDataLost` est activé lors d’une écriture dans <xref:System.IO.StreamWriter>, mais la méthode <xref:System.IO.StreamWriter.Flush%2A> ou <xref:System.IO.StreamWriter.Close%2A> n’est pas appelée par la suite avant la destruction de l’instance du <xref:System.IO.StreamWriter>. Quand cet Assistant Débogage managé est activé, le runtime détermine s’il existe encore des données mises en mémoire tampon dans <xref:System.IO.StreamWriter>. Si c’est le cas, l’Assistant Débogage managé est activé. L’appel aux méthodes <xref:System.GC.Collect%2A> et <xref:System.GC.WaitForPendingFinalizers%2A> peut forcer des finaliseurs à s’exécuter. Sinon, les finaliseurs s’exécuteront à des moments apparemment arbitraires, voire pas du tout lors de la sortie du processus. L’exécution explicite des finaliseurs avec cet Assistant Débogage managé activé aide à reproduire ce type de problème de façon plus fiable.  
  
## <a name="symptoms"></a>Symptômes  

 Un <xref:System.IO.StreamWriter> n’écrit pas les 1 à 4 derniers kilo-octets de données dans un fichier.  
  
## <a name="cause"></a>Cause  

 Le <xref:System.IO.StreamWriter> met les données en mémoire tampon en interne, ce qui exige un appel à la méthode <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> pour écrire les données mises en mémoire tampon dans le magasin de données sous-jacent. Si <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> n’est pas appelée au moment opportun, les données mises en mémoire tampon dans l’instance de <xref:System.IO.StreamWriter> peuvent ne pas être écrites comme prévu.  
  
 L’exemple suivant illustre un code mal écrit que cet Assistant Débogage managé doit intercepter.  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Le code précédent activera cet Assistant Débogage managé de façon plus fiable si un garbage collection est déclenché avant d’être suspendu jusqu’au terme de l’exécution des finaliseurs. Pour repérer ce type de problème, vous pouvez ajouter le code suivant à la fin de la méthode précédente dans une version Debug. Cela permet d’activer systématiquement l’Assistant Débogage managé même si cela ne résout évidemment pas la cause du problème.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Résolution  

 Veillez à appeler <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> avant de fermer une application ou tout bloc de code possédant une instance de <xref:System.IO.StreamWriter>. Pour ce faire, une des solutions les plus efficaces consiste à créer l’instance avec un bloc `using` C# (`Using` en Visual Basic) qui garantit l’appel à la méthode <xref:System.IO.StreamWriter.Dispose%2A> pour le writer, ce qui permet de fermer correctement l’instance.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Le code suivant illustre la même solution, à l’aide de `try/finally` au lieu d’`using`.  
  
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
  
 Si aucune de ces solutions ne peut être utilisée (par exemple, si un <xref:System.IO.StreamWriter> est stocké dans une variable statique et que vous ne pouvez pas exécuter facilement du code à la fin de sa durée de vie), l’appel à <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> après sa dernière utilisation ou l’affectation de la valeur `true` à la propriété <xref:System.IO.StreamWriter.AutoFlush%2A> avant sa première utilisation doit éviter ce problème.  
  
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
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le runtime.  
  
## <a name="output"></a>Output  

 Un message signale cette violation.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamWriter>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
