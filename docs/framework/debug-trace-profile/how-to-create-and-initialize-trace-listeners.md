---
title: 'Comment : créer et initialiser les écouteurs de la trace'
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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217441"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="5888f-102">Comment : créer et initialiser les écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="5888f-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="5888f-103">Les classes <xref:System.Diagnostics.Debug?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace?displayProperty=nameWithType> envoient des messages à des objets appelés écouteurs qui reçoivent et traitent ces messages.</span><span class="sxs-lookup"><span data-stu-id="5888f-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="5888f-104">L'un de ces écouteurs, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, est automatiquement créé et initialisé lors de l'activation du traçage ou du débogage.</span><span class="sxs-lookup"><span data-stu-id="5888f-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="5888f-105">Si vous voulez que la sortie de <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.Debug> soit dirigée vers d'autres sources, créez et initialisez des écouteurs de suivi supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5888f-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="5888f-106">Les écouteurs que vous créez doivent refléter les besoins de l'application.</span><span class="sxs-lookup"><span data-stu-id="5888f-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="5888f-107">Par exemple, si vous voulez un enregistrement textuel de toutes les sorties de trace, créez un écouteur <xref:System.Diagnostics.TextWriterTraceListener>, qui écrit toutes les sorties dans un nouveau fichier texte quand il est activé.</span><span class="sxs-lookup"><span data-stu-id="5888f-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="5888f-108">D'un autre côté, si vous voulez afficher la sortie uniquement pendant l'exécution de l'application, créez un écouteur <xref:System.Diagnostics.ConsoleTraceListener>, qui dirige toutes les sorties vers une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="5888f-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="5888f-109"><xref:System.Diagnostics.EventLogTraceListener> peut diriger la sortie de trace vers un journal d'événements.</span><span class="sxs-lookup"><span data-stu-id="5888f-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="5888f-110">Pour plus d’informations, consultez [Écouteurs de suivi](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="5888f-110">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="5888f-111">Vous pouvez créer des écouteurs de suivi dans un [fichier de configuration d’application](../configure-apps/index.md) ou dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5888f-111">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="5888f-112">Nous vous recommandons d'utiliser des fichiers de configuration d'application, car ils vous permettent d'ajouter, de modifier ou de supprimer des écouteurs de suivi sans avoir à modifier votre code.</span><span class="sxs-lookup"><span data-stu-id="5888f-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="5888f-113">Pour créer et utiliser un écouteur de suivi à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="5888f-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="5888f-114">Déclarez votre écouteur de suivi dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="5888f-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="5888f-115">Si l'écouteur que vous créez requiert d'autres objets, déclarez-les aussi.</span><span class="sxs-lookup"><span data-stu-id="5888f-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="5888f-116">L'exemple suivant montre comment créer un écouteur appelé `myListener`, qui écrit dans le fichier texte `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="5888f-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

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

2. <span data-ttu-id="5888f-117">Utilisez la classe <xref:System.Diagnostics.Trace> dans votre code pour écrire un message dans les écouteurs de suivi.</span><span class="sxs-lookup"><span data-stu-id="5888f-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="5888f-118">Pour créer et utiliser un écouteur de suivi dans le code</span><span class="sxs-lookup"><span data-stu-id="5888f-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="5888f-119">Ajoutez l’écouteur de suivi à la collection <xref:System.Diagnostics.Trace.Listeners%2A> et envoyez des informations de traçage aux écouteurs.</span><span class="sxs-lookup"><span data-stu-id="5888f-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

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

    <span data-ttu-id="5888f-120">\- ou -</span><span class="sxs-lookup"><span data-stu-id="5888f-120">\- or -</span></span>

- <span data-ttu-id="5888f-121">Si vous ne voulez pas que votre écouteur reçoive la sortie de trace, ne l'ajoutez pas à la collection <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="5888f-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="5888f-122">Vous pouvez émettre la sortie via un écouteur indépendant de la collection <xref:System.Diagnostics.Trace.Listeners%2A> en appelant les méthodes de sortie propres à l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="5888f-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="5888f-123">L'exemple suivant montre comment écrire une ligne dans un écouteur qui n'est pas dans la collection <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="5888f-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5888f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5888f-124">See also</span></span>

- [<span data-ttu-id="5888f-125">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="5888f-125">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="5888f-126">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="5888f-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="5888f-127">Guide pratique pour ajouter des instructions de suivi au code d’application</span><span class="sxs-lookup"><span data-stu-id="5888f-127">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="5888f-128">Suivi et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="5888f-128">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
