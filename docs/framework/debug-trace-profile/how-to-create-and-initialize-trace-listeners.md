---
title: 'Comment : créer et initialiser les écouteurs de la trace'
description: Découvrez comment créer et initialiser des écouteurs de suivi à l’aide de classes telles que System. Diagnostics. DefaultTraceListener dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
ms.openlocfilehash: 752306124e41a7fb7458daccc8c2891631eb9616
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051205"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="05de8-103">Comment : créer et initialiser les écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="05de8-103">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="05de8-104">Les classes <xref:System.Diagnostics.Debug?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace?displayProperty=nameWithType> envoient des messages à des objets appelés écouteurs qui reçoivent et traitent ces messages.</span><span class="sxs-lookup"><span data-stu-id="05de8-104">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="05de8-105">L'un de ces écouteurs, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, est automatiquement créé et initialisé lors de l'activation du traçage ou du débogage.</span><span class="sxs-lookup"><span data-stu-id="05de8-105">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="05de8-106">Si vous voulez que la sortie de <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.Debug> soit dirigée vers d'autres sources, créez et initialisez des écouteurs de suivi supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05de8-106">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="05de8-107">Les écouteurs que vous créez doivent refléter les besoins de l'application.</span><span class="sxs-lookup"><span data-stu-id="05de8-107">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="05de8-108">Par exemple, si vous voulez un enregistrement textuel de toutes les sorties de trace, créez un écouteur <xref:System.Diagnostics.TextWriterTraceListener>, qui écrit toutes les sorties dans un nouveau fichier texte quand il est activé.</span><span class="sxs-lookup"><span data-stu-id="05de8-108">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="05de8-109">D'un autre côté, si vous voulez afficher la sortie uniquement pendant l'exécution de l'application, créez un écouteur <xref:System.Diagnostics.ConsoleTraceListener>, qui dirige toutes les sorties vers une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="05de8-109">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="05de8-110"><xref:System.Diagnostics.EventLogTraceListener> peut diriger la sortie de trace vers un journal d'événements.</span><span class="sxs-lookup"><span data-stu-id="05de8-110">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="05de8-111">Pour plus d’informations, consultez [Écouteurs de suivi](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="05de8-111">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="05de8-112">Vous pouvez créer des écouteurs de suivi dans un [fichier de configuration d’application](../configure-apps/index.md) ou dans votre code.</span><span class="sxs-lookup"><span data-stu-id="05de8-112">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="05de8-113">Nous vous recommandons d'utiliser des fichiers de configuration d'application, car ils vous permettent d'ajouter, de modifier ou de supprimer des écouteurs de suivi sans avoir à modifier votre code.</span><span class="sxs-lookup"><span data-stu-id="05de8-113">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="05de8-114">Pour créer et utiliser un écouteur de suivi à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="05de8-114">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="05de8-115">Déclarez votre écouteur de suivi dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="05de8-115">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="05de8-116">Si l'écouteur que vous créez requiert d'autres objets, déclarez-les aussi.</span><span class="sxs-lookup"><span data-stu-id="05de8-116">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="05de8-117">L'exemple suivant montre comment créer un écouteur appelé `myListener`, qui écrit dans le fichier texte `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="05de8-117">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. <span data-ttu-id="05de8-118">Utilisez la classe <xref:System.Diagnostics.Trace> dans votre code pour écrire un message dans les écouteurs de suivi.</span><span class="sxs-lookup"><span data-stu-id="05de8-118">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="05de8-119">Pour créer et utiliser un écouteur de suivi dans le code</span><span class="sxs-lookup"><span data-stu-id="05de8-119">To create and use a trace listener in code</span></span>

- <span data-ttu-id="05de8-120">Ajoutez l’écouteur de suivi à la collection <xref:System.Diagnostics.Trace.Listeners%2A> et envoyez des informations de traçage aux écouteurs.</span><span class="sxs-lookup"><span data-stu-id="05de8-120">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    <span data-ttu-id="05de8-121">\- ou -</span><span class="sxs-lookup"><span data-stu-id="05de8-121">\- or -</span></span>

- <span data-ttu-id="05de8-122">Si vous ne voulez pas que votre écouteur reçoive la sortie de trace, ne l'ajoutez pas à la collection <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="05de8-122">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="05de8-123">Vous pouvez émettre la sortie via un écouteur indépendant de la collection <xref:System.Diagnostics.Trace.Listeners%2A> en appelant les méthodes de sortie propres à l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="05de8-123">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="05de8-124">L'exemple suivant montre comment écrire une ligne dans un écouteur qui n'est pas dans la collection <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="05de8-124">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a><span data-ttu-id="05de8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05de8-125">See also</span></span>

- [<span data-ttu-id="05de8-126">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="05de8-126">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="05de8-127">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="05de8-127">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="05de8-128">Comment : ajouter des instructions de traçage dans le code d'une application</span><span class="sxs-lookup"><span data-stu-id="05de8-128">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="05de8-129">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="05de8-129">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
