---
title: Tracing and Message Logging
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 55fdb31310c62c5d0ac7e5d963309cb1b3fe2da4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617534"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="802cb-102">Tracing and Message Logging</span><span class="sxs-lookup"><span data-stu-id="802cb-102">Tracing and Message Logging</span></span>
<span data-ttu-id="802cb-103">Cet exemple illustre comment activer l'enregistrement des suivis et des messages.</span><span class="sxs-lookup"><span data-stu-id="802cb-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="802cb-104">Les traces qui en résulte et les journaux de messages sont affichés à l’aide de la [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="802cb-105">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="802cb-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="802cb-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="802cb-107">Traçage</span><span class="sxs-lookup"><span data-stu-id="802cb-107">Tracing</span></span>  
 <span data-ttu-id="802cb-108">Windows Communication Foundation (WCF) utilise le mécanisme de suivi défini dans le <xref:System.Diagnostics> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="802cb-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="802cb-109">Dans ce modèle de suivi, les données de suivi sont générées par les sources de suivi implémentées par les applications.</span><span class="sxs-lookup"><span data-stu-id="802cb-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="802cb-110">Chacune de ces sources est identifiée à l'aide d'un nom.</span><span class="sxs-lookup"><span data-stu-id="802cb-110">Each source is identified by a name.</span></span> <span data-ttu-id="802cb-111">Les consommateurs de suivis créent des écouteurs pour les sources de suivi à partir desquelles ils souhaitent récupérer des informations.</span><span class="sxs-lookup"><span data-stu-id="802cb-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="802cb-112">Pour recevoir des données de suivi d'une source, vous devez créer un écouteur pour cette source.</span><span class="sxs-lookup"><span data-stu-id="802cb-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="802cb-113">Dans WCF, cela est possible en ajoutant le code suivant au fichier de configuration du client ou du service en définissant la source de suivi du modèle de Service `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="802cb-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="802cb-114">Pour plus d’informations sur les sources de trace, consultez la section de la Source de suivi dans le [configuration du suivi](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="802cb-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="802cb-115">Suivi et propagation d'activité</span><span class="sxs-lookup"><span data-stu-id="802cb-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="802cb-116">Avoir `ActivityTracing` activé et `propagateActivity` définie sur `true` dans le `system.ServiceModel` des sources de suivi pour le client et le service fournissent une corrélation de suivis dans des unités logiques de traitement (activités), entre les activités au sein de points de terminaison ( à travers des transferts d’activité) et entre les activités s’étendant sur plusieurs points de terminaison (via la propagation d’ID d’activité).</span><span class="sxs-lookup"><span data-stu-id="802cb-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="802cb-117">Ces trois mécanismes (activités, transfert et propagation) peuvent vous permettre de localiser plus facilement la cause racine d’une erreur, notamment en utilisant l’outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="802cb-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="802cb-118">Pour plus d’informations, consultez [à l’aide de Service Trace Viewer pour afficher les Traces corrélées et dépannage](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="802cb-119">Il est possible d'étendre le suivi fourni par le ServiceModel en créant des suivis d'activité définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="802cb-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="802cb-120">Les suivis d'activité définis par l'utilisateur permettent :</span><span class="sxs-lookup"><span data-stu-id="802cb-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="802cb-121">De regrouper les suivis dans des unités logiques de travail.</span><span class="sxs-lookup"><span data-stu-id="802cb-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="802cb-122">De mettre en relation les activités à l'aide du transfert et de la propagation.</span><span class="sxs-lookup"><span data-stu-id="802cb-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="802cb-123">Réduire le coût de performances du suivi WCF (par exemple, le coût de l’espace disque d’un fichier journal).</span><span class="sxs-lookup"><span data-stu-id="802cb-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="802cb-124">Pour plus d’informations sur le suivi d’activité définis par l’utilisateur, consultez le [extension suivi](../../../../docs/framework/wcf/samples/extending-tracing.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="802cb-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="802cb-125">Journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="802cb-125">Message Logging</span></span>  
 <span data-ttu-id="802cb-126">Enregistrement des messages peut être activé à la fois sur le client et le service de n’importe quelle application WCF.</span><span class="sxs-lookup"><span data-stu-id="802cb-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="802cb-127">Pour activer l'enregistrement des messages, vous devez ajouter le code suivant au client ou au service :</span><span class="sxs-lookup"><span data-stu-id="802cb-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="802cb-128">Lorsqu'un message est enregistré, le type de suivi généré pour ce message n'est pas le même si ce message est suivi au niveau du client ou du serveur.</span><span class="sxs-lookup"><span data-stu-id="802cb-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="802cb-129">Par exemple, le suivi du message « Add » est assuré dans la catégorie « TransportWrite », au niveau du client alors que son suivi est assuré dans la catégorie « TransportRead », au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="802cb-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="802cb-130">Configurez l'écouteur de suivi en ajoutant le code suivant à la section <xref:System.Diagnostics> du fichier App.config du client ou du fichier Web.config du service :</span><span class="sxs-lookup"><span data-stu-id="802cb-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="802cb-131">Les messages sont enregistrés au format XML dans le fichier de configuration stocké dans le répertoire cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="802cb-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="802cb-132">Les fichiers de suivi ne peuvent pas être créés si un répertoire de journal n'est pas créé auparavant.</span><span class="sxs-lookup"><span data-stu-id="802cb-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="802cb-133">Assurez-vous que le répertoire C:\logs\ existe ou définissez un autre répertoire d'enregistrement dans la configuration de l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="802cb-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="802cb-134">Consultez les instructions initiales de configuration figurant en fin de rubrique pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="802cb-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="802cb-135">Pour plus d’informations sur la journalisation des messages, consultez le [configuration de la journalisation du Message](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="802cb-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="802cb-136">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="802cb-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="802cb-137">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="802cb-138">Avant d'exécuter l'exemple Tracing and Message Logging, créez le répertoire C:\logs\ dans lequel le service stockera les fichiers .svclog.</span><span class="sxs-lookup"><span data-stu-id="802cb-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="802cb-139">Le nom de ce répertoire est défini dans le fichier de configuration sous la forme d'un chemin d'accès indiquant où les suivis et les messages doivent être enregistrés. Ce chemin peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="802cb-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="802cb-140">Accordez à l'utilisateur des droits d'accès en écriture de service réseau au répertoire des journaux.</span><span class="sxs-lookup"><span data-stu-id="802cb-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="802cb-141">Pour générer l’édition c#, C++ ou Visual Basic .NET de la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="802cb-142">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="802cb-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="802cb-143">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="802cb-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="802cb-144">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="802cb-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="802cb-145">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="802cb-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="802cb-146">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="802cb-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="802cb-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="802cb-147">See also</span></span>

- [<span data-ttu-id="802cb-148">Suivi</span><span class="sxs-lookup"><span data-stu-id="802cb-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="802cb-149">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="802cb-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
