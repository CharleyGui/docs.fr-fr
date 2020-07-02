---
title: Écouteurs de la trace
description: Explorez les écouteurs de suivi, qui sont un mécanisme de collecte et d’enregistrement des messages de suivi envoyés dans .NET. Un écouteur collecte, stocke et route des messages.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803521"
---
# <a name="trace-listeners"></a><span data-ttu-id="c83de-104">Écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="c83de-104">Trace Listeners</span></span>
<span data-ttu-id="c83de-105">Quand vous utilisez **Trace**, **Debug** et <xref:System.Diagnostics.TraceSource>, vous devez disposer d’un mécanisme de collecte et d’enregistrement des messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="c83de-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="c83de-106">Les messages de trace sont reçus par des *écouteurs*.</span><span class="sxs-lookup"><span data-stu-id="c83de-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="c83de-107">Le but d'un écouteur est de collecter, de stocker et de router les messages de suivi.</span><span class="sxs-lookup"><span data-stu-id="c83de-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="c83de-108">Les écouteurs dirigent la sortie de suivi vers une cible appropriée, telle qu'un journal, une fenêtre ou un fichier de texte.</span><span class="sxs-lookup"><span data-stu-id="c83de-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="c83de-109">Les écouteurs sont disponibles pour les classes **Debug**, **Trace** et <xref:System.Diagnostics.TraceSource>, et chacune d’elles peut envoyer sa sortie à de nombreux objets écouteur.</span><span class="sxs-lookup"><span data-stu-id="c83de-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="c83de-110">Voici les écouteurs prédéfinis couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="c83de-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="c83de-111"><xref:System.Diagnostics.TextWriterTraceListener> redirige la sortie vers une instance de la classe <xref:System.IO.TextWriter> ou vers toute classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="c83de-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="c83de-112">Il peut également écrire dans la console ou un fichier, car il s'agit de classes <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="c83de-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="c83de-113"><xref:System.Diagnostics.EventLogTraceListener> redirige la sortie vers un journal d'événements.</span><span class="sxs-lookup"><span data-stu-id="c83de-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="c83de-114"><xref:System.Diagnostics.DefaultTraceListener> émet des messages **Write** et **WriteLine** vers **OutputDebugString** et la méthode **Debugger.Log**.</span><span class="sxs-lookup"><span data-stu-id="c83de-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="c83de-115">Dans Visual Studio, cela entraîne l'affichage des messages de débogage dans la fenêtre de sortie.</span><span class="sxs-lookup"><span data-stu-id="c83de-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="c83de-116">Les messages **Fail** et les messages **Assert** d’échec émettent également vers l’API Windows **OutputDebugString** et la méthode **Debugger.Log**, et entraînent aussi l’affichage d’une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="c83de-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="c83de-117">Ce comportement est le comportement par défaut pour les messages **Debug** et **Trace**, car **DefaultTraceListener** est le seul écouteur automatiquement inclus dans chaque collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="c83de-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="c83de-118"><xref:System.Diagnostics.ConsoleTraceListener> dirige la sortie de traçage ou de débogage vers la sortie standard ou le flux d'erreurs standard.</span><span class="sxs-lookup"><span data-stu-id="c83de-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="c83de-119"><xref:System.Diagnostics.DelimitedListTraceListener> dirige la sortie de traçage ou de débogage vers un writer de texte (par ex., un writer de flux), ou vers un flux de données (par ex., un flux de fichiers).</span><span class="sxs-lookup"><span data-stu-id="c83de-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="c83de-120">La sortie de trace est dans un format de texte délimité qui utilise le délimiteur spécifié par la <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c83de-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="c83de-121"><xref:System.Diagnostics.XmlWriterTraceListener> dirige la sortie de traçage ou de débogage sous forme de données encodées en XML vers un <xref:System.IO.TextWriter> ou un <xref:System.IO.Stream>, par exemple, un <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="c83de-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="c83de-122">Si vous voulez qu’un autre écouteur en plus de <xref:System.Diagnostics.DefaultTraceListener> reçoive également la sortie de **Debug**, **Trace** et <xref:System.Diagnostics.TraceSource>, vous devez l’ajouter à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="c83de-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="c83de-123">Pour plus d’informations, consultez [Guide pratique pour créer et initialiser des écouteurs de suivi](how-to-create-and-initialize-trace-listeners.md) et [Guide pratique pour utiliser un TraceSource et des filtres avec des écouteurs de suivi](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="c83de-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="c83de-124">N’importe quel écouteur de la collection **Listeners** reçoit les mêmes messages en provenance des méthodes de sortie de suivi.</span><span class="sxs-lookup"><span data-stu-id="c83de-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="c83de-125">Par exemple, supposons que vous définissiez deux écouteurs : **TextWriterTraceListener** et **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="c83de-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="c83de-126">Chaque écouteur reçoit le même message.</span><span class="sxs-lookup"><span data-stu-id="c83de-126">Each listener receives the same message.</span></span> <span data-ttu-id="c83de-127">**TextWriterTraceListener** dirige sa sortie vers un flux et **EventLogTraceListener** dirige sa sortie vers un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="c83de-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="c83de-128">L’exemple suivant montre comment envoyer la sortie vers la collection **Listeners**.</span><span class="sxs-lookup"><span data-stu-id="c83de-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="c83de-129">Debug et Trace partagent la même collection **Listeners** ; par conséquent, si vous ajoutez un objet écouteur à une collection **Debug.Listeners** dans votre application, il est également ajouté à la collection **Trace.Listeners**.</span><span class="sxs-lookup"><span data-stu-id="c83de-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="c83de-130">L'exemple suivant montre comment utiliser un écouteur pour envoyer des informations de traçage à une console :</span><span class="sxs-lookup"><span data-stu-id="c83de-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="c83de-131">Écouteurs définis par le développeur</span><span class="sxs-lookup"><span data-stu-id="c83de-131">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="c83de-132">Vous pouvez définir vos propres écouteurs en héritant de la classe de base **TraceListener** et en remplaçant ses méthodes par vos méthodes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c83de-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="c83de-133">Pour plus d'informations sur la création d'écouteurs définis par le développeur, voir <xref:System.Diagnostics.TraceListener> dans la documentation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c83de-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83de-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c83de-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c83de-135">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="c83de-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="c83de-136">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="c83de-136">Trace Switches</span></span>](trace-switches.md)
