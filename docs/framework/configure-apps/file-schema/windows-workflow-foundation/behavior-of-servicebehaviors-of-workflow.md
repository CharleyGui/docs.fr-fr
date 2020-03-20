---
title: <behavior>de <serviceBehaviors> flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152318"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="fe05f-102">\<comportement> de \<serviceBehaviors> de flux de travail</span><span class="sxs-lookup"><span data-stu-id="fe05f-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="fe05f-103">**L’élément comportemental** contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="fe05f-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="fe05f-104">Chaque comportement est indexé par son **nom**.</span><span class="sxs-lookup"><span data-stu-id="fe05f-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="fe05f-105">Les services peuvent se lier à chaque comportement à travers ce nom en utilisant l’attribut **de comportementconfiguration** du point de [ \<terminaison>](../wcf/endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="fe05f-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="fe05f-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="fe05f-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="fe05f-107">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe05f-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe05f-108">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fe05f-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fe05f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportements>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fe05f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fe05f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fe05f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fe05f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportement>**</span><span class="sxs-lookup"><span data-stu-id="fe05f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe05f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe05f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe05f-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fe05f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fe05f-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fe05f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe05f-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="fe05f-115">Attributes</span></span>  
  
|<span data-ttu-id="fe05f-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="fe05f-116">Attribute</span></span>|<span data-ttu-id="fe05f-117">Description</span><span class="sxs-lookup"><span data-stu-id="fe05f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe05f-118">name</span><span class="sxs-lookup"><span data-stu-id="fe05f-118">name</span></span>|<span data-ttu-id="fe05f-119">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="fe05f-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="fe05f-120">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="fe05f-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe05f-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fe05f-121">Child Elements</span></span>  
  
|<span data-ttu-id="fe05f-122">Élément</span><span class="sxs-lookup"><span data-stu-id="fe05f-122">Element</span></span>|<span data-ttu-id="fe05f-123">Description</span><span class="sxs-lookup"><span data-stu-id="fe05f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe05f-124">\<>tamponReceive</span><span class="sxs-lookup"><span data-stu-id="fe05f-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="fe05f-125">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="fe05f-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="fe05f-126">\<routage></span><span class="sxs-lookup"><span data-stu-id="fe05f-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="fe05f-127">Comportement de service qui permet à un service d'utiliser le suivi ETW à l'aide d'un objet  <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="fe05f-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="fe05f-128">\<envoyerMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="fe05f-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="fe05f-129">Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="fe05f-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="fe05f-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="fe05f-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="fe05f-131">Comportement de service qui vous permet de configurer la fonctionnalité <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui prend en charge les informations d'état persistantes pour les instances de service du flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fe05f-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="fe05f-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="fe05f-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="fe05f-133">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="fe05f-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="fe05f-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="fe05f-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="fe05f-135">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="fe05f-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="fe05f-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="fe05f-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="fe05f-137">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="fe05f-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe05f-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fe05f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="fe05f-139">Élément</span><span class="sxs-lookup"><span data-stu-id="fe05f-139">Element</span></span>|<span data-ttu-id="fe05f-140">Description</span><span class="sxs-lookup"><span data-stu-id="fe05f-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe05f-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fe05f-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="fe05f-142">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="fe05f-142">A collection of service behavior elements.</span></span>|
