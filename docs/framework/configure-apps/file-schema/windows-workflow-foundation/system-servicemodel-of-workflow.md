---
title: <> System. serviceModel du flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151947"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="6f178-102">\<system.serviceModel>de flux de travail</span><span class="sxs-lookup"><span data-stu-id="6f178-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="6f178-103">Cette section de configuration contient tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6f178-103">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="6f178-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f178-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f178-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6f178-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6f178-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6f178-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f178-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6f178-107">Attributes</span></span>  
 <span data-ttu-id="6f178-108">Aucune</span><span class="sxs-lookup"><span data-stu-id="6f178-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f178-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f178-109">Child Elements</span></span>  
  
|<span data-ttu-id="6f178-110">Élément</span><span class="sxs-lookup"><span data-stu-id="6f178-110">Element</span></span>|<span data-ttu-id="6f178-111">Description</span><span class="sxs-lookup"><span data-stu-id="6f178-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="6f178-112">Cette section définit la collection **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="6f178-112">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="6f178-113">Chaque élément dans la collection définit des éléments de comportement consommés par des services.</span><span class="sxs-lookup"><span data-stu-id="6f178-113">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="6f178-114">Chaque élément de comportement est identifié par son attribut de **nom** unique.</span><span class="sxs-lookup"><span data-stu-id="6f178-114">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="6f178-115">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6f178-115">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="6f178-116">Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflows](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi pour un workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6f178-116">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f178-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f178-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6f178-118">Élément</span><span class="sxs-lookup"><span data-stu-id="6f178-118">Element</span></span>|<span data-ttu-id="6f178-119">Description</span><span class="sxs-lookup"><span data-stu-id="6f178-119">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="6f178-120">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="6f178-120">The root element for all configuration elements in a .NET configuration file.</span></span>|
