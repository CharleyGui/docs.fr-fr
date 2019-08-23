---
title: <state> de <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947494"
---
# <a name="state-of-states"></a><span data-ttu-id="59ca4-102">\<État > des \<États ></span><span class="sxs-lookup"><span data-stu-id="59ca4-102">\<state> of \<states></span></span>
<span data-ttu-id="59ca4-103">Élément de configuration qui contient l'état de l'activité faisant l'objet d'un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="59ca4-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="59ca4-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="59ca4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="59ca4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59ca4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="59ca4-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="59ca4-106">\<tracking></span></span>  
<span data-ttu-id="59ca4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59ca4-107">\<trackingProfile></span></span>  
<span data-ttu-id="59ca4-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="59ca4-108">\<workflow></span></span>  
<span data-ttu-id="59ca4-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="59ca4-109">\<activityStateQueries></span></span>  
<span data-ttu-id="59ca4-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="59ca4-110">\<activityStateQuery></span></span>  
<span data-ttu-id="59ca4-111">\<states></span><span class="sxs-lookup"><span data-stu-id="59ca4-111">\<states></span></span>  
<span data-ttu-id="59ca4-112">\<state></span><span class="sxs-lookup"><span data-stu-id="59ca4-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ca4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ca4-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ca4-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="59ca4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="59ca4-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="59ca4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ca4-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="59ca4-116">Attributes</span></span>  
  
|<span data-ttu-id="59ca4-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="59ca4-117">Attribute</span></span>|<span data-ttu-id="59ca4-118">Description</span><span class="sxs-lookup"><span data-stu-id="59ca4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59ca4-119">name</span><span class="sxs-lookup"><span data-stu-id="59ca4-119">name</span></span>|<span data-ttu-id="59ca4-120">Chaîne qui spécifie l'état de l'activité faisant l'objet d'un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="59ca4-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59ca4-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59ca4-121">Child Elements</span></span>  
 <span data-ttu-id="59ca4-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="59ca4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59ca4-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="59ca4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="59ca4-124">Élément</span><span class="sxs-lookup"><span data-stu-id="59ca4-124">Element</span></span>|<span data-ttu-id="59ca4-125">Description</span><span class="sxs-lookup"><span data-stu-id="59ca4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59ca4-126">\<states></span><span class="sxs-lookup"><span data-stu-id="59ca4-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="59ca4-127">Collection d’éléments de configuration qui contiennent les états de l’activité faisant l’objet d’un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="59ca4-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ca4-128">Notes</span><span class="sxs-lookup"><span data-stu-id="59ca4-128">Remarks</span></span>  
 <span data-ttu-id="59ca4-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="59ca4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="59ca4-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="59ca4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="59ca4-131">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="59ca4-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="59ca4-132">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="59ca4-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="59ca4-133">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="59ca4-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59ca4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ca4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="59ca4-135">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="59ca4-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59ca4-136">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="59ca4-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
