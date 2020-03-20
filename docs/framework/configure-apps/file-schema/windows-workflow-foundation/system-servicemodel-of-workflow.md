---
title: <system.serviceModel> de flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151947"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="f2f93-102">\<system.serviceModel> de flux de travail</span><span class="sxs-lookup"><span data-stu-id="f2f93-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="f2f93-103">Cette section de configuration contient tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="f2f93-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="f2f93-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2f93-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2f93-105">&nbsp;&nbsp;**\<Système. ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="f2f93-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f93-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f93-106">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore
          connectionStringName="String"
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>
     <participants>
      <add name="String"
           profileName="String"  
           type="String" />
     </participants>
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f93-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f2f93-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f93-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f2f93-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f93-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f2f93-109">Attributes</span></span>  
 <span data-ttu-id="f2f93-110">None</span><span class="sxs-lookup"><span data-stu-id="f2f93-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2f93-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f2f93-111">Child Elements</span></span>  
  
|<span data-ttu-id="f2f93-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f2f93-112">Element</span></span>|<span data-ttu-id="f2f93-113">Description</span><span class="sxs-lookup"><span data-stu-id="f2f93-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f93-114">\<comportements></span><span class="sxs-lookup"><span data-stu-id="f2f93-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="f2f93-115">Cette section définit la collection **serviceBehaviors.**</span><span class="sxs-lookup"><span data-stu-id="f2f93-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="f2f93-116">Chaque élément dans la collection définit des éléments de comportement consommés par des services.</span><span class="sxs-lookup"><span data-stu-id="f2f93-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="f2f93-117">Chaque élément de comportement est identifié par son attribut **nom** unique.</span><span class="sxs-lookup"><span data-stu-id="f2f93-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="f2f93-118">\<suivi des></span><span class="sxs-lookup"><span data-stu-id="f2f93-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="f2f93-119">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="f2f93-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="f2f93-120">Pour plus d’informations sur le suivi des flux de travail et sa configuration, voir [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="f2f93-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f93-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f2f93-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f93-122">Élément</span><span class="sxs-lookup"><span data-stu-id="f2f93-122">Element</span></span>|<span data-ttu-id="f2f93-123">Description</span><span class="sxs-lookup"><span data-stu-id="f2f93-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f93-124">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f2f93-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="f2f93-125">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="f2f93-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
