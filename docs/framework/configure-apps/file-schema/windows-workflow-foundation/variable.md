---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397766"
---
# <a name="variable"></a><span data-ttu-id="d0de4-101">\<variable></span><span class="sxs-lookup"><span data-stu-id="d0de4-101">\<variable></span></span>
<span data-ttu-id="d0de4-102">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="d0de4-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="d0de4-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d0de4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d0de4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d0de4-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d0de4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d0de4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d0de4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d0de4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="d0de4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="d0de4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<variables >** ](variables.md)</span><span class="sxs-lookup"><span data-stu-id="d0de4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)</span></span>\
<span data-ttu-id="d0de4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> variable**</span><span class="sxs-lookup"><span data-stu-id="d0de4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0de4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0de4-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0de4-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d0de4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d0de4-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d0de4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0de4-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="d0de4-116">Attributes</span></span>  
  
|<span data-ttu-id="d0de4-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="d0de4-117">Attribute</span></span>|<span data-ttu-id="d0de4-118">Description</span><span class="sxs-lookup"><span data-stu-id="d0de4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0de4-119">name</span><span class="sxs-lookup"><span data-stu-id="d0de4-119">name</span></span>|<span data-ttu-id="d0de4-120">Chaîne qui spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="d0de4-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0de4-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0de4-121">Child Elements</span></span>  
 <span data-ttu-id="d0de4-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0de4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0de4-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0de4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d0de4-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d0de4-124">Element</span></span>|<span data-ttu-id="d0de4-125">Description</span><span class="sxs-lookup"><span data-stu-id="d0de4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0de4-126">\<variable></span><span class="sxs-lookup"><span data-stu-id="d0de4-126">\<variable></span></span>](variable.md)|<span data-ttu-id="d0de4-127">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="d0de4-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0de4-128">Notes</span><span class="sxs-lookup"><span data-stu-id="d0de4-128">Remarks</span></span>  
 <span data-ttu-id="d0de4-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d0de4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d0de4-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="d0de4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d0de4-131">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="d0de4-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d0de4-132">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="d0de4-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d0de4-133">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d0de4-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0de4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0de4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d0de4-135">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="d0de4-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d0de4-136">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="d0de4-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
