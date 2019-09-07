---
title: <behavior>de <serviceBehaviors> Workflow
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398888"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="0d101-102">\<> de comportement \<de la > serviceBehaviors du flux de travail</span><span class="sxs-lookup"><span data-stu-id="0d101-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="0d101-103">L’élément **Behavior** contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="0d101-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="0d101-104">Chaque comportement est indexé par son **nom**.</span><span class="sxs-lookup"><span data-stu-id="0d101-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="0d101-105">Les services peuvent être liés à chaque comportement via ce nom à l’aide de l’attribut **behaviorConfiguration** de l' [ \<élément de point de terminaison >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0d101-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="0d101-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0d101-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="0d101-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d101-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d101-108">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0d101-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0d101-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0d101-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="0d101-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0d101-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="0d101-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de comportement**</span><span class="sxs-lookup"><span data-stu-id="0d101-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d101-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d101-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d101-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0d101-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0d101-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0d101-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d101-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="0d101-115">Attributes</span></span>  
  
|<span data-ttu-id="0d101-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="0d101-116">Attribute</span></span>|<span data-ttu-id="0d101-117">Description</span><span class="sxs-lookup"><span data-stu-id="0d101-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d101-118">name</span><span class="sxs-lookup"><span data-stu-id="0d101-118">name</span></span>|<span data-ttu-id="0d101-119">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="0d101-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="0d101-120">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="0d101-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d101-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0d101-121">Child Elements</span></span>  
  
|<span data-ttu-id="0d101-122">Élément</span><span class="sxs-lookup"><span data-stu-id="0d101-122">Element</span></span>|<span data-ttu-id="0d101-123">Description</span><span class="sxs-lookup"><span data-stu-id="0d101-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d101-124">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="0d101-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="0d101-125">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="0d101-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="0d101-126">\<routing></span><span class="sxs-lookup"><span data-stu-id="0d101-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="0d101-127">Comportement de service qui permet à un service d’utiliser le suivi ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>à l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="0d101-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="0d101-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="0d101-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="0d101-129">Comportement de service qui permet la personnalisation des niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux pour les flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’activités de messagerie d’envoi.</span><span class="sxs-lookup"><span data-stu-id="0d101-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="0d101-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="0d101-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="0d101-131">Comportement de service qui vous permet de configurer la <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge la persistance des informations d’État pour les instances de service de workflow dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0d101-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="0d101-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="0d101-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="0d101-133">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="0d101-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="0d101-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="0d101-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="0d101-135">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="0d101-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="0d101-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="0d101-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="0d101-137">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="0d101-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d101-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0d101-138">Parent Elements</span></span>  
  
|<span data-ttu-id="0d101-139">Élément</span><span class="sxs-lookup"><span data-stu-id="0d101-139">Element</span></span>|<span data-ttu-id="0d101-140">Description</span><span class="sxs-lookup"><span data-stu-id="0d101-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d101-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0d101-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="0d101-142">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="0d101-142">A collection of service behavior elements.</span></span>|
