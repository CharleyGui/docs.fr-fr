---
title: <behavior>de <serviceBehaviors> Workflow
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946079"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="6781e-102">\<> de comportement \<de la > serviceBehaviors du flux de travail</span><span class="sxs-lookup"><span data-stu-id="6781e-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="6781e-103">L’élément **Behavior** contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="6781e-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="6781e-104">Chaque comportement est indexé par son **nom**.</span><span class="sxs-lookup"><span data-stu-id="6781e-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="6781e-105">Les services peuvent être liés à chaque comportement via ce nom à l’aide de l’attribut **behaviorConfiguration** de l' [ \<élément de point de terminaison >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6781e-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="6781e-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="6781e-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="6781e-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6781e-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="6781e-108">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="6781e-108">\<behaviors></span></span>  
<span data-ttu-id="6781e-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6781e-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="6781e-110">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="6781e-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6781e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6781e-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  hostLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6781e-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6781e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6781e-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6781e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6781e-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="6781e-114">Attributes</span></span>  
  
|<span data-ttu-id="6781e-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="6781e-115">Attribute</span></span>|<span data-ttu-id="6781e-116">Description</span><span class="sxs-lookup"><span data-stu-id="6781e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6781e-117">name</span><span class="sxs-lookup"><span data-stu-id="6781e-117">name</span></span>|<span data-ttu-id="6781e-118">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="6781e-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="6781e-119">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="6781e-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6781e-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6781e-120">Child Elements</span></span>  
  
|<span data-ttu-id="6781e-121">Élément</span><span class="sxs-lookup"><span data-stu-id="6781e-121">Element</span></span>|<span data-ttu-id="6781e-122">Description</span><span class="sxs-lookup"><span data-stu-id="6781e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6781e-123">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="6781e-123">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="6781e-124">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="6781e-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="6781e-125">\<routing></span><span class="sxs-lookup"><span data-stu-id="6781e-125">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="6781e-126">Comportement de service qui permet à un service d’utiliser le suivi ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>à l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="6781e-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="6781e-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="6781e-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="6781e-128">Comportement de service qui permet la personnalisation des niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux pour les flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’activités de messagerie d’envoi.</span><span class="sxs-lookup"><span data-stu-id="6781e-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="6781e-129">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="6781e-129">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="6781e-130">Comportement de service qui vous permet de configurer la <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge la persistance des informations d’État pour les instances de service de workflow dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="6781e-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="6781e-131">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="6781e-131">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="6781e-132">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="6781e-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="6781e-133">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="6781e-133">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="6781e-134">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="6781e-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="6781e-135">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="6781e-135">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="6781e-136">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="6781e-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6781e-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6781e-137">Parent Elements</span></span>  
  
|<span data-ttu-id="6781e-138">Élément</span><span class="sxs-lookup"><span data-stu-id="6781e-138">Element</span></span>|<span data-ttu-id="6781e-139">Description</span><span class="sxs-lookup"><span data-stu-id="6781e-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6781e-140">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6781e-140">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="6781e-141">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="6781e-141">A collection of service behavior elements.</span></span>|
