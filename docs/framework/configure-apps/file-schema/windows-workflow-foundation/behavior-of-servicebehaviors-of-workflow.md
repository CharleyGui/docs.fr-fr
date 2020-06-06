---
title: <behavior>de <serviceBehaviors> Workflow
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152318"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="29c8a-102">\<behavior>de \<serviceBehaviors> Workflow</span><span class="sxs-lookup"><span data-stu-id="29c8a-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="29c8a-103">L’élément **Behavior** contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="29c8a-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="29c8a-104">Chaque comportement est indexé par son **nom**.</span><span class="sxs-lookup"><span data-stu-id="29c8a-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="29c8a-105">Les services peuvent être liés à chaque comportement via ce nom à l’aide de l’attribut **behaviorConfiguration** de l' [\<endpoint>](../wcf/endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="29c8a-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="29c8a-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="29c8a-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="29c8a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c8a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29c8a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29c8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29c8a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="29c8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29c8a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="29c8a-110">Attributes</span></span>  
  
|<span data-ttu-id="29c8a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="29c8a-111">Attribute</span></span>|<span data-ttu-id="29c8a-112">Description</span><span class="sxs-lookup"><span data-stu-id="29c8a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29c8a-113">name</span><span class="sxs-lookup"><span data-stu-id="29c8a-113">name</span></span>|<span data-ttu-id="29c8a-114">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="29c8a-114">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="29c8a-115">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="29c8a-115">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29c8a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29c8a-116">Child Elements</span></span>  
  
|<span data-ttu-id="29c8a-117">Élément</span><span class="sxs-lookup"><span data-stu-id="29c8a-117">Element</span></span>|<span data-ttu-id="29c8a-118">Description</span><span class="sxs-lookup"><span data-stu-id="29c8a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="29c8a-119">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="29c8a-119">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="29c8a-120">Comportement de service qui permet à un service d'utiliser le suivi ETW à l'aide d'un objet  <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="29c8a-120">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="29c8a-121">Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="29c8a-121">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="29c8a-122">Comportement de service qui vous permet de configurer la fonctionnalité <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui prend en charge les informations d'état persistantes pour les instances de service du flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="29c8a-122">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="29c8a-123">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="29c8a-123">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="29c8a-124">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="29c8a-124">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="29c8a-125">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="29c8a-125">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29c8a-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29c8a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="29c8a-127">Élément</span><span class="sxs-lookup"><span data-stu-id="29c8a-127">Element</span></span>|<span data-ttu-id="29c8a-128">Description</span><span class="sxs-lookup"><span data-stu-id="29c8a-128">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="29c8a-129">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="29c8a-129">A collection of service behavior elements.</span></span>|
