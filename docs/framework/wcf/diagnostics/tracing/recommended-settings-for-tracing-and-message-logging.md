---
title: Paramètres recommandés pour le suivi et l'enregistrement des messages
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 9d2586570a3f590735c2a8e1ca176580886c8d92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578914"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="5b0da-102">Paramètres recommandés pour le suivi et l'enregistrement des messages</span><span class="sxs-lookup"><span data-stu-id="5b0da-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="5b0da-103">Cette rubrique décrit les paramètres de suivi et d'enregistrement des messages recommandés pour différents environnements d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="5b0da-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="5b0da-104">Paramètres recommandés pour un environnement de production</span><span class="sxs-lookup"><span data-stu-id="5b0da-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="5b0da-105">Pour un environnement de production, si vous utilisez les sources de suivi WCF, affectez à `switchValue` la valeur Warning.</span><span class="sxs-lookup"><span data-stu-id="5b0da-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="5b0da-106">Si vous utilisez la source de suivi WCF `System.ServiceModel`, affectez à l'attribut `switchValue` la valeur `Warning` et à l'attribut `propagateActivity` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5b0da-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="5b0da-107">Si vous utilisez une source de suivi définie par l'utilisateur, affectez à l'attribut `switchValue` la valeur `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="5b0da-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="5b0da-108">Vous pouvez effectuer cette opération manuellement à l’aide de l' [outil Éditeur de configuration (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5b0da-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="5b0da-109">Si vous ne prévoyez pas d'augmentation des performances, vous pouvez affecter la valeur `switchValue` à l'attribut `Information` dans tous les cas mentionnés précédemment, ce qui génère une quantité assez élevée de données de suivi.</span><span class="sxs-lookup"><span data-stu-id="5b0da-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="5b0da-110">L'exemple suivant illustre ces paramètres recommandés.</span><span class="sxs-lookup"><span data-stu-id="5b0da-110">The following example demonstrates these recommended settings.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="5b0da-111">Paramètres recommandés pour le déploiement ou le débogage</span><span class="sxs-lookup"><span data-stu-id="5b0da-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="5b0da-112">Pour l'environnement de déploiement ou de débogage , choisissez `Information` ou `Verbose`, avec `ActivityTracing` pour une source de suivi `System.ServiceModel` ou définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5b0da-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="5b0da-113">Pour améliorer le débogage, vous devez également ajouter une source de suivi supplémentaire (`System.ServiceModel.MessageLogging`) à la configuration afin d'activer l'enregistrement des messages.</span><span class="sxs-lookup"><span data-stu-id="5b0da-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="5b0da-114">Remarquez que l'attribut `switchValue` n'a aucun impact sur cette source de suivi.</span><span class="sxs-lookup"><span data-stu-id="5b0da-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="5b0da-115">L'exemple suivant illustre les paramètres recommandés, à l'aide d'un écouteur partagé qui utilise le `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="5b0da-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging
           logEntireMessage="true"
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="5b0da-116">Utilisation de WMI pour modifier des paramètres</span><span class="sxs-lookup"><span data-stu-id="5b0da-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="5b0da-117">Vous pouvez utiliser WMI pour modifier des paramètres de configuration pendant l'exécution (en activant l'attribut `wmiProviderEnabled` dans la configuration, comme cela est indiqué dans l'exemple de configuration précédent).</span><span class="sxs-lookup"><span data-stu-id="5b0da-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="5b0da-118">Par exemple, vous pouvez utiliser WMI dans le CIM Studio pour modifier les niveaux de source de suivi de Warning à Information au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="5b0da-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="5b0da-119">Vous devez savoir que le coût de performance du débogage en direct de cette manière peut être très élevé.</span><span class="sxs-lookup"><span data-stu-id="5b0da-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="5b0da-120">Pour plus d’informations sur l’utilisation de WMI, consultez la rubrique [utilisation de Windows Management Instrumentation pour les diagnostics](../wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="5b0da-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="5b0da-121">Activer des événements corrélés dans le suivi ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b0da-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="5b0da-122">Les événements ASP.NET ne définissent pas l'ID de corrélation (ActivityID), sauf si le suivi de l'élément ASP.NET est activé.</span><span class="sxs-lookup"><span data-stu-id="5b0da-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="5b0da-123">Pour afficher correctement les événements corrélés, vous devez activer le suivi des événements ASP.NET à l’aide de la commande suivante dans la console de commande, qui peut être appelée en accédant à **Démarrer**, **exécuter** , puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="5b0da-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="5b0da-124">Pour désactiver le suivi des événements ASP.NET, utilisez la commande suivante,</span><span class="sxs-lookup"><span data-stu-id="5b0da-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b0da-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b0da-125">See also</span></span>

- [<span data-ttu-id="5b0da-126">Utilisation de Windows Management Instrumentation pour les Diagnostics</span><span class="sxs-lookup"><span data-stu-id="5b0da-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
