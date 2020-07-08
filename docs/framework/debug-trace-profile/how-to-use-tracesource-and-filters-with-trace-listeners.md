---
title: 'Comment : utiliser des TraceSource et des filtres avec des écouteurs de la trace'
description: Utilisez la classe TraceSource et des filtres avec des écouteurs de suivi dans .NET. TraceSource remplace les méthodes statiques des anciennes classes de trace et de débogage.
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
ms.openlocfilehash: 432c866f7c3ca1fd59f8f3d36acd61740b6584c0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051257"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Comment : utiliser des TraceSource et des filtres avec des écouteurs de la trace
L’une des nouveautés du .NET Framework version 2.0 est un système de suivi amélioré. Le principe de base reste inchangé : les messages de suivi sont envoyés par l’intermédiaire de commutateurs aux écouteurs qui transmettent les données à un support de sortie associé. Une différence majeure de la version 2.0 est que les suivis peuvent être lancés via des instances de la classe <xref:System.Diagnostics.TraceSource>. La classe <xref:System.Diagnostics.TraceSource> est conçue pour fonctionner comme système de suivi amélioré et peut être utilisée à la place des méthodes statiques des anciennes classes de suivi <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug>. Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> existent encore, mais l’utilisation de la classe <xref:System.Diagnostics.TraceSource> est désormais la méthode recommandée pour le suivi.  
  
 Cette rubrique décrit l’utilisation de la classe <xref:System.Diagnostics.TraceSource> associée à un fichier de configuration de l’application.  Il est déconseillé, mais néanmoins possible, d’effectuer le suivi à l’aide de <xref:System.Diagnostics.TraceSource> sans utiliser de fichier de configuration. Pour plus d’informations sur le suivi sans fichier de configuration, consultez [Guide pratique pour créer et initialiser des sources de suivi](how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Pour créer et initialiser votre source de suivi  
  
1. Pour instrumenter une application avec le suivi, la première étape consiste à créer une source de suivi. Dans les projets importants intégrant divers composants, vous pouvez créer une source de suivi séparée pour chaque composant. La méthode conseillée consiste à utiliser le nom de l’application comme nom de la source de suivi. Cela permet de distinguer plus facilement les différents suivis. Le code suivant crée une source de suivi (`mySource)`) et appelle une méthode (`Activity1`) qui effectue le suivi des événements.  Les messages de suivi sont écrits par l’écouteur de suivi par défaut.  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Pour créer et initialiser des filtres et des écouteurs de suivi  
  
1. Le code de la première procédure n’identifie aucun filtre ni écouteur de suivi par programmation. Le code permet uniquement d’écrire les messages de suivi dans l’écouteur de suivi par défaut. Pour configurer des écouteurs de suivi spécifiques et leurs filtres associés, modifiez le fichier de configuration correspondant au nom de votre application. Dans ce fichier, vous pouvez ajouter ou supprimer un écouteur, définir les propriétés et un filtre pour un écouteur ou supprimer des écouteurs. L’exemple de fichier de configuration suivant montre comment initialiser un écouteur de suivi de console et un écouteur de suivi TextWriter pour la source de suivi créée dans la procédure précédente. En plus de configurer les écouteurs de suivi, le fichier de configuration crée des filtres pour les deux écouteurs ainsi qu’un commutateur source pour la source de suivi. L'exemple illustre deux techniques pour ajouter des écouteurs de la trace : l'ajout direct de l'écouteur à la source de trace et l'ajout d'un écouteur à la collection d'écouteurs partagés suivi de l'ajout de son nom à la source de trace. Les filtres identifiés pour les deux écouteurs sont initialisés avec des niveaux de source différents. Par conséquent, certains messages ne sont écrits que par un seul des deux écouteurs.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"
            switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"
            type="System.Diagnostics.TextWriterTraceListener"
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Pour modifier le niveau auquel un écouteur écrit un message de suivi  
  
1. Le fichier de configuration initialise les paramètres de la source de trace lors de l'initialisation de l'application. Pour changer ces paramètres, vous devez modifier le fichier de configuration et redémarrer l’application ou actualiser l’application par programmation à l’aide de la méthode <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>. L'application peut modifier dynamiquement les propriétés définies par le fichier de configuration pour substituer des paramètres spécifiés par l'utilisateur.  Vous pouvez, par exemple, décider que les messages critiques sont toujours envoyés vers un fichier texte, quels que soient les paramètres de la configuration actuelle.  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners
                // for all event types. This statement will override
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Comment : créer et initialiser les sources de trace](how-to-create-and-initialize-trace-sources.md)
- [Écouteurs de suivi](trace-listeners.md)
