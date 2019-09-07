---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398574"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="f11fc-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f11fc-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="f11fc-102">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="f11fc-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f11fc-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f11fc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f11fc-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f11fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="f11fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="f11fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f11fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="f11fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="f11fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11fc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11fc-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f11fc-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f11fc-111">Attributes and Elements</span></span>  

<span data-ttu-id="f11fc-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f11fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f11fc-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f11fc-113">Attributes</span></span>  

<span data-ttu-id="f11fc-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f11fc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f11fc-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f11fc-115">Child Elements</span></span>  
  
|<span data-ttu-id="f11fc-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f11fc-116">Element</span></span>|<span data-ttu-id="f11fc-117">Description</span><span class="sxs-lookup"><span data-stu-id="f11fc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f11fc-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f11fc-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="f11fc-119">Requête qui permet d'effectuer le suivi des changements dans le cycle de vie d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="f11fc-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f11fc-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f11fc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f11fc-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f11fc-121">Element</span></span>|<span data-ttu-id="f11fc-122">Description</span><span class="sxs-lookup"><span data-stu-id="f11fc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f11fc-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f11fc-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f11fc-124">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="f11fc-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f11fc-125">Notes</span><span class="sxs-lookup"><span data-stu-id="f11fc-125">Remarks</span></span>  

<span data-ttu-id="f11fc-126">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="f11fc-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f11fc-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="f11fc-127">Example</span></span>  

<span data-ttu-id="f11fc-128">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="f11fc-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f11fc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f11fc-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f11fc-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f11fc-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f11fc-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f11fc-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
