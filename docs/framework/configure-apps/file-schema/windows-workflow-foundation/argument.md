---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: f2aeb61e2e72f5bd6a696c031279f2c57907166b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946151"
---
# <a name="argument"></a><span data-ttu-id="58536-101">\<argument></span><span class="sxs-lookup"><span data-stu-id="58536-101">\<argument></span></span>
<span data-ttu-id="58536-102">Élément de configuration qui représente un argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="58536-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="58536-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="58536-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="58536-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58536-104">\<system.serviceModel></span></span>  
<span data-ttu-id="58536-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="58536-105">\<tracking></span></span>  
<span data-ttu-id="58536-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="58536-106">\<trackingProfile></span></span>  
<span data-ttu-id="58536-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="58536-107">\<workflow></span></span>  
<span data-ttu-id="58536-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="58536-108">\<activityStateQueries></span></span>  
<span data-ttu-id="58536-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="58536-109">\<activityStateQuery></span></span>  
<span data-ttu-id="58536-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="58536-110">\<arguments></span></span>  
<span data-ttu-id="58536-111">\<argument></span><span class="sxs-lookup"><span data-stu-id="58536-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58536-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58536-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58536-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58536-113">Attributes and Elements</span></span>  
 <span data-ttu-id="58536-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58536-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58536-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="58536-115">Attributes</span></span>  
  
|<span data-ttu-id="58536-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="58536-116">Attribute</span></span>|<span data-ttu-id="58536-117">Description</span><span class="sxs-lookup"><span data-stu-id="58536-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58536-118">name</span><span class="sxs-lookup"><span data-stu-id="58536-118">name</span></span>|<span data-ttu-id="58536-119">Chaîne qui spécifie le nom de l'argument.</span><span class="sxs-lookup"><span data-stu-id="58536-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58536-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58536-120">Child Elements</span></span>  
 <span data-ttu-id="58536-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="58536-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58536-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58536-122">Parent Elements</span></span>  
  
|<span data-ttu-id="58536-123">Élément</span><span class="sxs-lookup"><span data-stu-id="58536-123">Element</span></span>|<span data-ttu-id="58536-124">Description</span><span class="sxs-lookup"><span data-stu-id="58536-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58536-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="58536-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="58536-126">Collection d’arguments associés à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="58536-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58536-127">Notes</span><span class="sxs-lookup"><span data-stu-id="58536-127">Remarks</span></span>  
 <span data-ttu-id="58536-128">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="58536-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="58536-129">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="58536-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="58536-130">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="58536-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="58536-131">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="58536-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="58536-132">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="58536-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58536-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58536-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="58536-134">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="58536-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="58536-135">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="58536-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
