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
# <a name="how-to-create-and-initialize-trace-listeners"></a>Comment : créer et initialiser les écouteurs de la trace

Les classes <xref:System.Diagnostics.Debug?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace?displayProperty=nameWithType> envoient des messages à des objets appelés écouteurs qui reçoivent et traitent ces messages. L'un de ces écouteurs, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, est automatiquement créé et initialisé lors de l'activation du traçage ou du débogage. Si vous voulez que la sortie de <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.Debug> soit dirigée vers d'autres sources, créez et initialisez des écouteurs de suivi supplémentaires.

Les écouteurs que vous créez doivent refléter les besoins de l'application. Par exemple, si vous voulez un enregistrement textuel de toutes les sorties de trace, créez un écouteur <xref:System.Diagnostics.TextWriterTraceListener>, qui écrit toutes les sorties dans un nouveau fichier texte quand il est activé. D'un autre côté, si vous voulez afficher la sortie uniquement pendant l'exécution de l'application, créez un écouteur <xref:System.Diagnostics.ConsoleTraceListener>, qui dirige toutes les sorties vers une fenêtre de console. <xref:System.Diagnostics.EventLogTraceListener> peut diriger la sortie de trace vers un journal d'événements. Pour plus d’informations, consultez [Écouteurs de suivi](trace-listeners.md).

Vous pouvez créer des écouteurs de suivi dans un [fichier de configuration d’application](../configure-apps/index.md) ou dans votre code. Nous vous recommandons d'utiliser des fichiers de configuration d'application, car ils vous permettent d'ajouter, de modifier ou de supprimer des écouteurs de suivi sans avoir à modifier votre code.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Pour créer et utiliser un écouteur de suivi à l'aide d'un fichier de configuration

1. Déclarez votre écouteur de suivi dans le fichier de configuration de votre application. Si l'écouteur que vous créez requiert d'autres objets, déclarez-les aussi. L'exemple suivant montre comment créer un écouteur appelé `myListener`, qui écrit dans le fichier texte `TextWriterOutput.log`.

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

2. Utilisez la classe <xref:System.Diagnostics.Trace> dans votre code pour écrire un message dans les écouteurs de suivi.

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a>Pour créer et utiliser un écouteur de suivi dans le code

- Ajoutez l’écouteur de suivi à la collection <xref:System.Diagnostics.Trace.Listeners%2A> et envoyez des informations de traçage aux écouteurs.

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

    \- ou -

- Si vous ne voulez pas que votre écouteur reçoive la sortie de trace, ne l'ajoutez pas à la collection <xref:System.Diagnostics.Trace.Listeners%2A>. Vous pouvez émettre la sortie via un écouteur indépendant de la collection <xref:System.Diagnostics.Trace.Listeners%2A> en appelant les méthodes de sortie propres à l’écouteur. L'exemple suivant montre comment écrire une ligne dans un écouteur qui n'est pas dans la collection <xref:System.Diagnostics.Trace.Listeners%2A>.

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

## <a name="see-also"></a>Voir aussi

- [Écouteurs de suivi](trace-listeners.md)
- [Commutateurs de traçage](trace-switches.md)
- [Comment : ajouter des instructions de traçage dans le code d'une application](how-to-add-trace-statements-to-application-code.md)
- [Traçage et instrumentation d'applications](tracing-and-instrumenting-applications.md)
