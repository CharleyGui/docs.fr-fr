---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8b8cfe95a646563642e7425fdb4b5257cafa466f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947299"
---
# <a name="trackingprofile"></a><span data-ttu-id="39302-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="39302-101">\<trackingProfile></span></span>
<span data-ttu-id="39302-102">Représente une section de configuration pour la création d’un abonnement aux enregistrements de suivi de flux de travail dans un participant de suivi.</span><span class="sxs-lookup"><span data-stu-id="39302-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="39302-103">Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="39302-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="39302-104">Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="39302-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="39302-105">Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflow](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [profils](../../../windows-workflow-foundation/tracking-profiles.md)de suivi.</span><span class="sxs-lookup"><span data-stu-id="39302-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="39302-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39302-106">\<system.serviceModel></span></span>  
<span data-ttu-id="39302-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="39302-107">\<tracking></span></span>  
<span data-ttu-id="39302-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="39302-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39302-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39302-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39302-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="39302-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39302-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="39302-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39302-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="39302-112">Attributes</span></span>  
  
|<span data-ttu-id="39302-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="39302-113">Attribute</span></span>|<span data-ttu-id="39302-114">Description</span><span class="sxs-lookup"><span data-stu-id="39302-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39302-115">name</span><span class="sxs-lookup"><span data-stu-id="39302-115">name</span></span>|<span data-ttu-id="39302-116">Chaîne qui spécifie le nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="39302-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39302-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="39302-117">Child Elements</span></span>  
  
|<span data-ttu-id="39302-118">Élément</span><span class="sxs-lookup"><span data-stu-id="39302-118">Element</span></span>|<span data-ttu-id="39302-119">Description</span><span class="sxs-lookup"><span data-stu-id="39302-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39302-120">\<participants></span><span class="sxs-lookup"><span data-stu-id="39302-120">\<participants></span></span>](participants.md)|<span data-ttu-id="39302-121">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39302-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39302-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="39302-122">Parent Elements</span></span>  
  
|<span data-ttu-id="39302-123">Élément</span><span class="sxs-lookup"><span data-stu-id="39302-123">Element</span></span>|<span data-ttu-id="39302-124">Description</span><span class="sxs-lookup"><span data-stu-id="39302-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39302-125">\<tracking></span><span class="sxs-lookup"><span data-stu-id="39302-125">\<tracking></span></span>](tracking.md)|<span data-ttu-id="39302-126">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="39302-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39302-127">Notes</span><span class="sxs-lookup"><span data-stu-id="39302-127">Remarks</span></span>  
 <span data-ttu-id="39302-128">Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="39302-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="39302-129">Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un workflow.</span><span class="sxs-lookup"><span data-stu-id="39302-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="39302-130">Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="39302-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="39302-131">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="39302-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="39302-132">Il existe quelques types de requêtes qui vous permettent de vous abonner à différentes <xref:System.Activities.Tracking.TrackingRecord> classes d’objets.</span><span class="sxs-lookup"><span data-stu-id="39302-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="39302-133">Pour obtenir la liste complète des requêtes, consultez [ \<participants >](participants.md) et [profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="39302-133">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="39302-134">L’exemple suivant montre un modèle de suivi dans un fichier de configuration qui permet à un participant de suivi `Started` de `Completed` s’abonner aux événements de flux de travail et.</span><span class="sxs-lookup"><span data-stu-id="39302-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39302-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39302-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="39302-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="39302-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="39302-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="39302-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
