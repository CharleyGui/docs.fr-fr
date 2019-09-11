---
title: <workflowInstanceQueries>de WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854773"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="a5d8c-102">\<> workflowInstanceQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="a5d8c-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="a5d8c-103">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="a5d8c-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="a5d8c-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a5d8c-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5d8c-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a5d8c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a5d8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="a5d8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a5d8c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a5d8c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5d8c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a5d8c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="a5d8c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d8c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5d8c-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5d8c-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5d8c-113">Attributes and elements</span></span>

<span data-ttu-id="a5d8c-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a5d8c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5d8c-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5d8c-115">Attributes</span></span>  

<span data-ttu-id="a5d8c-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a5d8c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5d8c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5d8c-117">Child elements</span></span>  
  
|<span data-ttu-id="a5d8c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="a5d8c-118">Element</span></span>|<span data-ttu-id="a5d8c-119">Description</span><span class="sxs-lookup"><span data-stu-id="a5d8c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5d8c-120">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="a5d8c-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="a5d8c-121">Requête qui permet d'effectuer le suivi des changements dans le cycle de vie d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a5d8c-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5d8c-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5d8c-122">Parent elements</span></span>  
  
|<span data-ttu-id="a5d8c-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a5d8c-123">Element</span></span>|<span data-ttu-id="a5d8c-124">Description</span><span class="sxs-lookup"><span data-stu-id="a5d8c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5d8c-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a5d8c-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a5d8c-126">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété [ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) .</span><span class="sxs-lookup"><span data-stu-id="a5d8c-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5d8c-127">Notes</span><span class="sxs-lookup"><span data-stu-id="a5d8c-127">Remarks</span></span>

<span data-ttu-id="a5d8c-128">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="a5d8c-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="a5d8c-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5d8c-129">Example</span></span>  

<span data-ttu-id="a5d8c-130">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="a5d8c-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a5d8c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5d8c-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a5d8c-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="a5d8c-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5d8c-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="a5d8c-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
