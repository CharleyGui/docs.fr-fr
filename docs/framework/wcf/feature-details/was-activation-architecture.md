---
title: Architecture d'activation WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184253"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="8479e-102">Architecture d'activation WAS</span><span class="sxs-lookup"><span data-stu-id="8479e-102">WAS Activation Architecture</span></span>
<span data-ttu-id="8479e-103">Cette rubrique détaille et décrit les composants du service d'activation des processus de Windows (également appelé WAS).</span><span class="sxs-lookup"><span data-stu-id="8479e-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="8479e-104">Composants d'activation</span><span class="sxs-lookup"><span data-stu-id="8479e-104">Activation Components</span></span>  
 <span data-ttu-id="8479e-105">Le service WAS se compose de plusieurs composants architecturaux :</span><span class="sxs-lookup"><span data-stu-id="8479e-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="8479e-106">Adaptateurs d'écouteur.</span><span class="sxs-lookup"><span data-stu-id="8479e-106">Listener adapters.</span></span> <span data-ttu-id="8479e-107">Services Windows qui reçoivent des messages sur des protocoles réseau spécifiques et communiquent avec WAS pour acheminer les messages entrants vers le processus de travail correct.</span><span class="sxs-lookup"><span data-stu-id="8479e-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="8479e-108">WAS.</span><span class="sxs-lookup"><span data-stu-id="8479e-108">WAS.</span></span> <span data-ttu-id="8479e-109">Service Windows qui gère la création et la durée de vie des processus de travail.</span><span class="sxs-lookup"><span data-stu-id="8479e-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="8479e-110">Fichier exécutable de processus de travail générique (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="8479e-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="8479e-111">Gestionnaire d'application.</span><span class="sxs-lookup"><span data-stu-id="8479e-111">Application manager.</span></span> <span data-ttu-id="8479e-112">Gère la création et la durée de vie des domaines d'application qui hébergent des applications dans le processus de travail.</span><span class="sxs-lookup"><span data-stu-id="8479e-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="8479e-113">Gestionnaires de protocoles.</span><span class="sxs-lookup"><span data-stu-id="8479e-113">Protocol handlers.</span></span> <span data-ttu-id="8479e-114">Composants spécifiques au protocole qui s'exécutent dans le processus de travail et gèrent les communications entre le processus de travail et les différents adaptateurs d'écouteur.</span><span class="sxs-lookup"><span data-stu-id="8479e-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="8479e-115">Il existe deux types de gestionnaires de protocoles : les gestionnaires de protocoles de processus et les gestionnaires de protocoles de domaine d'application (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="8479e-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="8479e-116">Lorsque le service WAS active une instance de processus de traitement, il charge les gestionnaires de protocoles de processus requis dans le processus de traitement et utilise le gestionnaire d'application pour créer un domaine d'application destiné à héberger l'application.</span><span class="sxs-lookup"><span data-stu-id="8479e-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="8479e-117">Le domaine d'application charge le code de l'application ainsi que les gestionnaires de protocoles AppDomain requis par l'application.</span><span class="sxs-lookup"><span data-stu-id="8479e-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Capture d’écran qui montre l’architecture WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="8479e-119">Adaptateurs d'écouteur</span><span class="sxs-lookup"><span data-stu-id="8479e-119">Listener Adapters</span></span>  
 <span data-ttu-id="8479e-120">Les adaptateurs d'écouteur sont des services Windows individuels qui implémentent la logique de la communication réseau utilisée pour recevoir les messages à l'aide du protocole réseau sur lequel ils écoutent.</span><span class="sxs-lookup"><span data-stu-id="8479e-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="8479e-121">Le tableau suivant répertorie les adaptateurs de l’auditeur pour les protocoles de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8479e-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="8479e-122">Nom du service d'adaptateur de l'écouteur</span><span class="sxs-lookup"><span data-stu-id="8479e-122">Listener adapter service name</span></span>|<span data-ttu-id="8479e-123">Protocol</span><span class="sxs-lookup"><span data-stu-id="8479e-123">Protocol</span></span>|<span data-ttu-id="8479e-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8479e-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="8479e-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="8479e-125">W3SVC</span></span>|<span data-ttu-id="8479e-126">http</span><span class="sxs-lookup"><span data-stu-id="8479e-126">http</span></span>|<span data-ttu-id="8479e-127">Composant commun qui fournit l’activation HTTP pour l’IIS 7.0 et le WCF.</span><span class="sxs-lookup"><span data-stu-id="8479e-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="8479e-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="8479e-128">NetTcpActivator</span></span>|<span data-ttu-id="8479e-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="8479e-129">net.tcp</span></span>|<span data-ttu-id="8479e-130">Dépend du service NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="8479e-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="8479e-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="8479e-131">NetPipeActivator</span></span>|<span data-ttu-id="8479e-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="8479e-132">net.pipe</span></span>||  
|<span data-ttu-id="8479e-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="8479e-133">NetMsmqActivator</span></span>|<span data-ttu-id="8479e-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="8479e-134">net.msmq</span></span>|<span data-ttu-id="8479e-135">Pour une utilisation avec des applications de file d’attente de message basées sur WCF.</span><span class="sxs-lookup"><span data-stu-id="8479e-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="8479e-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="8479e-136">NetMsmqActivator</span></span>|<span data-ttu-id="8479e-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="8479e-137">msmq.formatname</span></span>|<span data-ttu-id="8479e-138">Assure la compatibilité descendante avec les applications Message Queuing existantes.</span><span class="sxs-lookup"><span data-stu-id="8479e-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="8479e-139">Les adaptateurs d'écouteur pour des protocoles spécifiques sont enregistrés lors de l'installation dans le fichier applicationHost.config, comme l'illustre l'exemple XML suivant.</span><span class="sxs-lookup"><span data-stu-id="8479e-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="8479e-140">Gestionnaires de protocoles</span><span class="sxs-lookup"><span data-stu-id="8479e-140">Protocol Handlers</span></span>  
 <span data-ttu-id="8479e-141">Les gestionnaires de protocoles de processus et AppDomain pour des protocoles spécifiques sont enregistrés dans le fichier Web.config de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8479e-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8479e-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8479e-142">See also</span></span>

- [<span data-ttu-id="8479e-143">Configuration du service WAS pour une utilisation avec WCF</span><span class="sxs-lookup"><span data-stu-id="8479e-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="8479e-144">[Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8479e-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
