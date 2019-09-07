---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397590"
---
# <a name="variables"></a><span data-ttu-id="4dc9f-101">\<variables></span><span class="sxs-lookup"><span data-stu-id="4dc9f-101">\<variables></span></span>
<span data-ttu-id="4dc9f-102">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="4dc9f-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4dc9f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4dc9f-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4dc9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="4dc9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="4dc9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="4dc9f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="4dc9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="4dc9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="4dc9f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<variables >**</span><span class="sxs-lookup"><span data-stu-id="4dc9f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc9f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dc9f-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dc9f-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4dc9f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4dc9f-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dc9f-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="4dc9f-115">Attributes</span></span>  
 <span data-ttu-id="4dc9f-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dc9f-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4dc9f-117">Child Elements</span></span>  
  
|<span data-ttu-id="4dc9f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="4dc9f-118">Element</span></span>|<span data-ttu-id="4dc9f-119">Description</span><span class="sxs-lookup"><span data-stu-id="4dc9f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc9f-120">\<variable></span><span class="sxs-lookup"><span data-stu-id="4dc9f-120">\<variable></span></span>](variable.md)|<span data-ttu-id="4dc9f-121">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dc9f-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4dc9f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4dc9f-123">Élément</span><span class="sxs-lookup"><span data-stu-id="4dc9f-123">Element</span></span>|<span data-ttu-id="4dc9f-124">Description</span><span class="sxs-lookup"><span data-stu-id="4dc9f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc9f-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4dc9f-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="4dc9f-126">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4dc9f-127">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dc9f-128">Notes</span><span class="sxs-lookup"><span data-stu-id="4dc9f-128">Remarks</span></span>  
 <span data-ttu-id="4dc9f-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4dc9f-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4dc9f-131">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4dc9f-132">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="4dc9f-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4dc9f-133">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9f-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4dc9f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dc9f-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4dc9f-135">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="4dc9f-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4dc9f-136">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="4dc9f-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
