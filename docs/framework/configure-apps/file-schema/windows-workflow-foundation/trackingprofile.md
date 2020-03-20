---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8985da7e1223ac117cf1b68227140634f9c85d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151887"
---
# <a name="trackingprofile"></a><span data-ttu-id="438c6-101">\<suiviProfile></span><span class="sxs-lookup"><span data-stu-id="438c6-101">\<trackingProfile></span></span>
<span data-ttu-id="438c6-102">Représente une section de configuration pour la création d'un abonnement à des enregistrements de suivi de flux de travail dans un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="438c6-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="438c6-103">Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="438c6-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="438c6-104">Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="438c6-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="438c6-105">Pour plus d’informations sur le suivi des flux de travail et sa configuration, voir [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="438c6-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="438c6-106">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="438c6-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="438c6-107">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="438c6-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="438c6-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="438c6-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="438c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<suiviProfile>**</span><span class="sxs-lookup"><span data-stu-id="438c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438c6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438c6-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
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
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
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
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="438c6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="438c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="438c6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="438c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="438c6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="438c6-113">Attributes</span></span>  
  
|<span data-ttu-id="438c6-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="438c6-114">Attribute</span></span>|<span data-ttu-id="438c6-115">Description</span><span class="sxs-lookup"><span data-stu-id="438c6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="438c6-116">name</span><span class="sxs-lookup"><span data-stu-id="438c6-116">name</span></span>|<span data-ttu-id="438c6-117">Chaîne qui spécifie le nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="438c6-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="438c6-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="438c6-118">Child Elements</span></span>  
  
|<span data-ttu-id="438c6-119">Élément</span><span class="sxs-lookup"><span data-stu-id="438c6-119">Element</span></span>|<span data-ttu-id="438c6-120">Description</span><span class="sxs-lookup"><span data-stu-id="438c6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="438c6-121">\<participants></span><span class="sxs-lookup"><span data-stu-id="438c6-121">\<participants></span></span>](participants.md)|<span data-ttu-id="438c6-122">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="438c6-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="438c6-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="438c6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="438c6-124">Élément</span><span class="sxs-lookup"><span data-stu-id="438c6-124">Element</span></span>|<span data-ttu-id="438c6-125">Description</span><span class="sxs-lookup"><span data-stu-id="438c6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="438c6-126">\<suivi des></span><span class="sxs-lookup"><span data-stu-id="438c6-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="438c6-127">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="438c6-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="438c6-128">Notes </span><span class="sxs-lookup"><span data-stu-id="438c6-128">Remarks</span></span>  
 <span data-ttu-id="438c6-129">Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="438c6-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="438c6-130">Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un workflow.</span><span class="sxs-lookup"><span data-stu-id="438c6-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="438c6-131">Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="438c6-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="438c6-132">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="438c6-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="438c6-133">Il existe une poignée de types de requêtes <xref:System.Activities.Tracking.TrackingRecord> qui vous permettent de vous abonner à différentes classes d’objets.</span><span class="sxs-lookup"><span data-stu-id="438c6-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="438c6-134">Pour une liste complète des [ \<](participants.md) requêtes, voir les participants>et [les profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="438c6-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="438c6-135">L’exemple suivant montre un profil de suivi dans un `Started` fichier `Completed` de configuration qui permet à un participant de suivi de s’abonner aux événements et aux flux de travail.</span><span class="sxs-lookup"><span data-stu-id="438c6-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="438c6-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="438c6-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="438c6-137">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="438c6-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="438c6-138">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="438c6-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
