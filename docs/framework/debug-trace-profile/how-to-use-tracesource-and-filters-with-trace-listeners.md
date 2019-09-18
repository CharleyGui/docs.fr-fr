---
title: 'Procédure : Utiliser des TraceSource et des filtres avec des écouteurs de trace'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1e214266b66f390fecffe802270a4181a6d7a7f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052681"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="ed3ea-102">Procédure : Utiliser des TraceSource et des filtres avec des écouteurs de trace</span><span class="sxs-lookup"><span data-stu-id="ed3ea-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="ed3ea-103">L’une des nouveautés du .NET Framework version 2.0 est un système de suivi amélioré.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="ed3ea-104">Le principe de base reste inchangé : les messages de suivi sont envoyés par l’intermédiaire de commutateurs aux écouteurs qui transmettent les données à un support de sortie associé.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="ed3ea-105">Une différence majeure de la version 2.0 est que les suivis peuvent être lancés via des instances de la classe <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="ed3ea-106">La classe <xref:System.Diagnostics.TraceSource> est conçue pour fonctionner comme système de suivi amélioré et peut être utilisée à la place des méthodes statiques des anciennes classes de suivi <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug>.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="ed3ea-107">Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> existent encore, mais l’utilisation de la classe <xref:System.Diagnostics.TraceSource> est désormais la méthode recommandée pour le suivi.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="ed3ea-108">Cette rubrique décrit l’utilisation de la classe <xref:System.Diagnostics.TraceSource> associée à un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="ed3ea-109">Il est déconseillé, mais néanmoins possible, d’effectuer le suivi à l’aide de <xref:System.Diagnostics.TraceSource> sans utiliser de fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="ed3ea-110">Pour plus d’informations sur le suivi sans fichier de [configuration, consultez Procédure : Créer et initialiser des sources](how-to-create-and-initialize-trace-sources.md)de suivi.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="ed3ea-111">Pour créer et initialiser votre source de suivi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="ed3ea-112">Pour instrumenter une application avec le suivi, la première étape consiste à créer une source de suivi.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="ed3ea-113">Dans les projets importants intégrant divers composants, vous pouvez créer une source de suivi séparée pour chaque composant.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="ed3ea-114">La méthode conseillée consiste à utiliser le nom de l’application comme nom de la source de suivi.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="ed3ea-115">Cela permet de distinguer plus facilement les différents suivis.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="ed3ea-116">Le code suivant crée une source de suivi (`mySource)`) et appelle une méthode (`Activity1`) qui effectue le suivi des événements.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="ed3ea-117">Les messages de suivi sont écrits par l’écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="ed3ea-118">Pour créer et initialiser des filtres et des écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="ed3ea-119">Le code de la première procédure n’identifie aucun filtre ni écouteur de suivi par programmation.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="ed3ea-120">Le code permet uniquement d’écrire les messages de suivi dans l’écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="ed3ea-121">Pour configurer des écouteurs de suivi spécifiques et leurs filtres associés, modifiez le fichier de configuration correspondant au nom de votre application.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="ed3ea-122">Dans ce fichier, vous pouvez ajouter ou supprimer un écouteur, définir les propriétés et un filtre pour un écouteur ou supprimer des écouteurs.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="ed3ea-123">L’exemple de fichier de configuration suivant montre comment initialiser un écouteur de suivi de console et un écouteur de suivi TextWriter pour la source de suivi créée dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="ed3ea-124">En plus de configurer les écouteurs de suivi, le fichier de configuration crée des filtres pour les deux écouteurs ainsi qu’un commutateur source pour la source de suivi.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="ed3ea-125">L'exemple illustre deux techniques pour ajouter des écouteurs de la trace : l'ajout direct de l'écouteur à la source de trace et l'ajout d'un écouteur à la collection d'écouteurs partagés suivi de l'ajout de son nom à la source de trace.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="ed3ea-126">Les filtres identifiés pour les deux écouteurs sont initialisés avec des niveaux de source différents.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="ed3ea-127">Par conséquent, certains messages ne sont écrits que par un seul des deux écouteurs.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="ed3ea-128">Pour modifier le niveau auquel un écouteur écrit un message de suivi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="ed3ea-129">Le fichier de configuration initialise les paramètres de la source de trace lors de l'initialisation de l'application.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="ed3ea-130">Pour changer ces paramètres, vous devez modifier le fichier de configuration et redémarrer l’application ou actualiser l’application par programmation à l’aide de la méthode <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ed3ea-131">L'application peut modifier dynamiquement les propriétés définies par le fichier de configuration pour substituer des paramètres spécifiés par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="ed3ea-132">Vous pouvez, par exemple, décider que les messages critiques sont toujours envoyés vers un fichier texte, quels que soient les paramètres de la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed3ea-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="ed3ea-134">Guide pratique pour Créer et initialiser des sources de suivi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-134">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="ed3ea-135">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="ed3ea-135">Trace Listeners</span></span>](trace-listeners.md)
