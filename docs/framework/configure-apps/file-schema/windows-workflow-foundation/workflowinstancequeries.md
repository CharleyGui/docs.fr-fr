---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 0a32e6ee22cdf984e64c1b8fa16836c4c56d0380
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932735"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="f4e59-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f4e59-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="f4e59-102">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="f4e59-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="f4e59-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f4e59-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f4e59-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f4e59-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f4e59-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="f4e59-105">\<tracking></span></span>  
<span data-ttu-id="f4e59-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f4e59-106">\<trackingProfile></span></span>  
<span data-ttu-id="f4e59-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f4e59-107">\<workflow></span></span>  
<span data-ttu-id="f4e59-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f4e59-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e59-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4e59-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4e59-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4e59-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f4e59-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4e59-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4e59-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4e59-112">Attributes</span></span>  
 <span data-ttu-id="f4e59-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f4e59-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4e59-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4e59-114">Child Elements</span></span>  
  
|<span data-ttu-id="f4e59-115">Élément</span><span class="sxs-lookup"><span data-stu-id="f4e59-115">Element</span></span>|<span data-ttu-id="f4e59-116">Description</span><span class="sxs-lookup"><span data-stu-id="f4e59-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4e59-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f4e59-117">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="f4e59-118">Requête qui permet d'effectuer le suivi des changements dans le cycle de vie d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="f4e59-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4e59-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4e59-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f4e59-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f4e59-120">Element</span></span>|<span data-ttu-id="f4e59-121">Description</span><span class="sxs-lookup"><span data-stu-id="f4e59-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4e59-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f4e59-122">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f4e59-123">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="f4e59-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e59-124">Notes</span><span class="sxs-lookup"><span data-stu-id="f4e59-124">Remarks</span></span>  
 <span data-ttu-id="f4e59-125">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="f4e59-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f4e59-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="f4e59-126">Example</span></span>  
 <span data-ttu-id="f4e59-127">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="f4e59-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4e59-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4e59-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f4e59-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f4e59-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f4e59-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f4e59-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
