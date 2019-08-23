---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 560df771b44fc8ba8d192657677bf0496283b539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945425"
---
# <a name="activitystatequery"></a><span data-ttu-id="5e593-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5e593-101">\<activityStateQuery></span></span>
<span data-ttu-id="5e593-102">Représente une requête qui permet d'effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5e593-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="5e593-103">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité «Envoyer un message électronique» se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="5e593-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="5e593-104">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="5e593-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="5e593-105">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="5e593-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="5e593-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5e593-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5e593-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e593-107">\<system.serviceModel></span></span>  
<span data-ttu-id="5e593-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="5e593-108">\<tracking></span></span>  
<span data-ttu-id="5e593-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5e593-109">\<trackingProfile></span></span>  
<span data-ttu-id="5e593-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5e593-110">\<workflow></span></span>  
<span data-ttu-id="5e593-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="5e593-111">\<activityStateQueries></span></span>  
<span data-ttu-id="5e593-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5e593-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e593-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e593-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
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
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e593-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5e593-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5e593-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5e593-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e593-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="5e593-116">Attributes</span></span>  
  
|<span data-ttu-id="5e593-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="5e593-117">Attribute</span></span>|<span data-ttu-id="5e593-118">Description</span><span class="sxs-lookup"><span data-stu-id="5e593-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e593-119">activityName</span><span class="sxs-lookup"><span data-stu-id="5e593-119">activityName</span></span>|<span data-ttu-id="5e593-120">Chaîne qui spécifie le nom de l'activité sur lequel filtrer des instances <xref:System.Activities.Tracking.ActivityStateRecord>.</span><span class="sxs-lookup"><span data-stu-id="5e593-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e593-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5e593-121">Child Elements</span></span>  
  
|<span data-ttu-id="5e593-122">Élément</span><span class="sxs-lookup"><span data-stu-id="5e593-122">Element</span></span>|<span data-ttu-id="5e593-123">Description</span><span class="sxs-lookup"><span data-stu-id="5e593-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e593-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="5e593-124">\<arguments></span></span>](arguments.md)|<span data-ttu-id="5e593-125">Collection d’arguments associés à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="5e593-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="5e593-126">\<states></span><span class="sxs-lookup"><span data-stu-id="5e593-126">\<states></span></span>](states.md)|<span data-ttu-id="5e593-127">Collection d’éléments de configuration qui contiennent les états de l’activité faisant l’objet d’un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="5e593-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="5e593-128">\<states></span><span class="sxs-lookup"><span data-stu-id="5e593-128">\<states></span></span>](states.md)|<span data-ttu-id="5e593-129">Collection de variables associées à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="5e593-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e593-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5e593-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5e593-131">Élément</span><span class="sxs-lookup"><span data-stu-id="5e593-131">Element</span></span>|<span data-ttu-id="5e593-132">Description</span><span class="sxs-lookup"><span data-stu-id="5e593-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e593-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5e593-133">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="5e593-134">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="5e593-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5e593-135">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="5e593-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e593-136">Notes</span><span class="sxs-lookup"><span data-stu-id="5e593-136">Remarks</span></span>  
 <span data-ttu-id="5e593-137">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5e593-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5e593-138">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="5e593-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5e593-139">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="5e593-139">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5e593-140">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="5e593-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5e593-141">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="5e593-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e593-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e593-142">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5e593-143">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="5e593-143">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5e593-144">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="5e593-144">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
