---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397509"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="7985f-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7985f-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="7985f-102">Représente une requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début et la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="7985f-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="7985f-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7985f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7985f-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7985f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7985f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7985f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7985f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="7985f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="7985f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="7985f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7985f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7985f-111">Syntax</span></span>  
  
```xml  
<tracking>
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
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7985f-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7985f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7985f-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7985f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7985f-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="7985f-114">Attributes</span></span>  
 <span data-ttu-id="7985f-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7985f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7985f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7985f-116">Child Elements</span></span>  
  
|<span data-ttu-id="7985f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="7985f-117">Element</span></span>|<span data-ttu-id="7985f-118">Description</span><span class="sxs-lookup"><span data-stu-id="7985f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7985f-119">\<states></span><span class="sxs-lookup"><span data-stu-id="7985f-119">\<states></span></span>](states.md)|<span data-ttu-id="7985f-120">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="7985f-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7985f-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7985f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7985f-122">Élément</span><span class="sxs-lookup"><span data-stu-id="7985f-122">Element</span></span>|<span data-ttu-id="7985f-123">Description</span><span class="sxs-lookup"><span data-stu-id="7985f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7985f-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7985f-124">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="7985f-125">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="7985f-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7985f-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7985f-126">Remarks</span></span>  
 <span data-ttu-id="7985f-127">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="7985f-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7985f-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="7985f-128">Example</span></span>  
 <span data-ttu-id="7985f-129">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="7985f-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7985f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7985f-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7985f-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="7985f-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7985f-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="7985f-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
