---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151856"
---
# <a name="workflow"></a><span data-ttu-id="af8dc-101">\<flux de travail></span><span class="sxs-lookup"><span data-stu-id="af8dc-101">\<workflow></span></span>
<span data-ttu-id="af8dc-102">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af8dc-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="af8dc-103">Pour plus d’informations sur le suivi des flux de travail et sa configuration, voir [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="af8dc-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="af8dc-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="af8dc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="af8dc-105">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="af8dc-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="af8dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="af8dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="af8dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="af8dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="af8dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<flux de travail>**</span><span class="sxs-lookup"><span data-stu-id="af8dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8dc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8dc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af8dc-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af8dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af8dc-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af8dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af8dc-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="af8dc-112">Attributes</span></span>  
  
|<span data-ttu-id="af8dc-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="af8dc-113">Attribute</span></span>|<span data-ttu-id="af8dc-114">Description</span><span class="sxs-lookup"><span data-stu-id="af8dc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af8dc-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="af8dc-115">activityDefinitionId</span></span>|<span data-ttu-id="af8dc-116">Chaîne qui spécifie l'ID de définition de l'activité du flux de travail faisant l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="af8dc-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af8dc-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af8dc-117">Child Elements</span></span>  
  
|<span data-ttu-id="af8dc-118">Élément</span><span class="sxs-lookup"><span data-stu-id="af8dc-118">Element</span></span>|<span data-ttu-id="af8dc-119">Description</span><span class="sxs-lookup"><span data-stu-id="af8dc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af8dc-120">\<activitéScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="af8dc-121">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="af8dc-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="af8dc-122">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="af8dc-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="af8dc-123">\<activitéStateQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="af8dc-124">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="af8dc-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="af8dc-125">Par exemple, vous pouvez garder une trace de chaque fois que l’activité « Envoyer un e-mail » se termine dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="af8dc-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="af8dc-126">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="af8dc-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="af8dc-127">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="af8dc-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="af8dc-128">\<signetsResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="af8dc-129">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="af8dc-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="af8dc-130">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="af8dc-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="af8dc-131">\<annulerRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="af8dc-132">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="af8dc-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="af8dc-133">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="af8dc-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="af8dc-134">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="af8dc-135">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="af8dc-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="af8dc-136">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="af8dc-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="af8dc-137">\<fautePropagationQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="af8dc-138">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="af8dc-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="af8dc-139">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="af8dc-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="af8dc-140">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="af8dc-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="af8dc-141">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="af8dc-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="af8dc-142">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="af8dc-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="af8dc-143">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="af8dc-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af8dc-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af8dc-144">Parent Elements</span></span>  
  
|<span data-ttu-id="af8dc-145">Élément</span><span class="sxs-lookup"><span data-stu-id="af8dc-145">Element</span></span>|<span data-ttu-id="af8dc-146">Description</span><span class="sxs-lookup"><span data-stu-id="af8dc-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af8dc-147">\<suiviProfile></span><span class="sxs-lookup"><span data-stu-id="af8dc-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="af8dc-148">Représente une section de configuration pour la création d'un abonnement à des enregistrements de suivi de flux de travail dans un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="af8dc-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="af8dc-149">Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="af8dc-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="af8dc-150">Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="af8dc-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8dc-151">Notes </span><span class="sxs-lookup"><span data-stu-id="af8dc-151">Remarks</span></span>  
 <span data-ttu-id="af8dc-152">Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail particulière change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="af8dc-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="af8dc-153">L'instance de flux de travail faisant l'objet d'un suivi est identifiée par cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="af8dc-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="af8dc-154">Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un workflow.</span><span class="sxs-lookup"><span data-stu-id="af8dc-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="af8dc-155">Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="af8dc-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="af8dc-156">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="af8dc-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="af8dc-157">Quelques types de requêtes vous permettent de vous abonner à différentes classes d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="af8dc-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="af8dc-158">Pour une liste complète des requêtes, consultez la liste des éléments enfants de ce sujet et [des profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="af8dc-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="af8dc-159">L’exemple suivant montre un profil de suivi dans un `Started` fichier `Completed` de configuration qui permet à un participant de suivi de s’abonner aux événements et aux flux de travail.</span><span class="sxs-lookup"><span data-stu-id="af8dc-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af8dc-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af8dc-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="af8dc-161">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="af8dc-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="af8dc-162">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="af8dc-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
