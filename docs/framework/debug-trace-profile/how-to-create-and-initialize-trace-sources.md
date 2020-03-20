---
title: 'Comment : créer et initialiser les sources de trace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174730"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="66c5e-102">Comment : créer et initialiser les sources de trace</span><span class="sxs-lookup"><span data-stu-id="66c5e-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="66c5e-103">La classe <xref:System.Diagnostics.TraceSource> est utilisée par les applications pour produire des traces qui peuvent être associées à l'application.</span><span class="sxs-lookup"><span data-stu-id="66c5e-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="66c5e-104"><xref:System.Diagnostics.TraceSource> fournit des méthodes de traçage qui vous permettent de tracer facilement des événements et des données, ainsi que de fournir des traces d'information.</span><span class="sxs-lookup"><span data-stu-id="66c5e-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="66c5e-105">Il est possible de créer et d'initialiser une sortie de trace <xref:System.Diagnostics.TraceSource> en utilisant ou non les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="66c5e-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="66c5e-106">Cette rubrique fournit des instructions pour les deux options.</span><span class="sxs-lookup"><span data-stu-id="66c5e-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="66c5e-107">Toutefois, nous vous recommandons d'utiliser des fichiers de configuration pour simplifier la reconfiguration des traces produites par les sources de trace au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="66c5e-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="66c5e-108">Pour créer et initialiser une source de trace à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="66c5e-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="66c5e-109">Créez un projet d’application de console Visual Studio (.NET Framework) et remplacez le code fourni par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="66c5e-109">Create a Visual Studio console application project (.NET Framework) and replace the supplied code with the following code.</span></span> <span data-ttu-id="66c5e-110">Ce code consigne les erreurs et les avertissements et renvoie certains d'entre eux vers la console et d'autres vers le fichier myListener créé par les entrées dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="66c5e-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="66c5e-111">Ajoutez un fichier de configuration d'application, s'il n'en existe pas encore, au projet pour initialiser la source de trace nommée `TraceSourceApp` dans l'exemple de code à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="66c5e-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="66c5e-112">Remplacez le contenu du fichier de configuration par défaut par les paramètres suivants pour initialiser un écouteur de suivi de console et un écouteur de suivi de TextWriter pour la source de trace créée à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="66c5e-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
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
  
     <span data-ttu-id="66c5e-113">En plus de configurer les écouteurs de la trace, le fichier de configuration crée des filtres pour les deux écouteurs et un commutateur de source pour la source de trace.</span><span class="sxs-lookup"><span data-stu-id="66c5e-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="66c5e-114">L'exemple illustre deux techniques pour ajouter des écouteurs de la trace : l'ajout direct de l'écouteur à la source de trace et l'ajout d'un écouteur à la collection d'écouteurs partagés suivi de l'ajout de son nom à la source de trace.</span><span class="sxs-lookup"><span data-stu-id="66c5e-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="66c5e-115">Les filtres identifiés pour les deux écouteurs sont initialisés avec des niveaux de source différents.</span><span class="sxs-lookup"><span data-stu-id="66c5e-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="66c5e-116">Par conséquent, certains messages ne sont écrits que par un seul des deux écouteurs.</span><span class="sxs-lookup"><span data-stu-id="66c5e-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="66c5e-117">Le fichier de configuration initialise les paramètres de la source de trace lors de l'initialisation de l'application.</span><span class="sxs-lookup"><span data-stu-id="66c5e-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="66c5e-118">L'application peut modifier dynamiquement les propriétés définies par le fichier de configuration pour substituer des paramètres spécifiés par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66c5e-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="66c5e-119">Vous pouvez, par exemple, décider que les messages critiques seront toujours envoyés vers un fichier texte, quels que soient les paramètres de configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="66c5e-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="66c5e-120">L'exemple de code montre comment remplacer des paramètres du fichier de configuration pour garantir que les messages critiques sont envoyés aux écouteurs de suivi.</span><span class="sxs-lookup"><span data-stu-id="66c5e-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="66c5e-121">La modification des paramètres du fichier de configuration lorsque l'application est en cours d'exécution ne change pas les paramètres d'origine.</span><span class="sxs-lookup"><span data-stu-id="66c5e-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="66c5e-122">Pour modifier les paramètres, vous devez redémarrer l'application ou l'actualiser par programmation à l'aide de la méthode <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66c5e-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="66c5e-123">Pour initialiser des sources de trace, des écouteurs et des filtres sans fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="66c5e-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="66c5e-124">Utilisez le code d'exemple suivant pour activer le traçage par une source de trace sans utiliser un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="66c5e-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="66c5e-125">Il ne s'agit pas d'une pratique recommandée, mais il peut arriver que vous ne souhaitiez pas dépendre des fichiers de configuration pour assurer le traçage.</span><span class="sxs-lookup"><span data-stu-id="66c5e-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="66c5e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66c5e-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="66c5e-127">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="66c5e-127">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
