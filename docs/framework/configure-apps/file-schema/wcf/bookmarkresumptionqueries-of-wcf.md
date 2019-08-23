---
title: <bookmarkResumptionQueries>de WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919740"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="3a5fc-102">\<> bookmarkResumptionQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="3a5fc-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="3a5fc-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3a5fc-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="3a5fc-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3a5fc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="3a5fc-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3a5fc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3a5fc-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3a5fc-107">\<tracking></span></span>  
<span data-ttu-id="3a5fc-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="3a5fc-108">\<profiles></span></span>  
<span data-ttu-id="3a5fc-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3a5fc-109">\<trackingProfile></span></span>  
<span data-ttu-id="3a5fc-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3a5fc-110">\<workflow></span></span>  
<span data-ttu-id="3a5fc-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="3a5fc-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3a5fc-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="3a5fc-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a5fc-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a5fc-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a5fc-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a5fc-114">Attributes and elements</span></span>  
  
<span data-ttu-id="3a5fc-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a5fc-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a5fc-116">Attributes</span></span>  
  
<span data-ttu-id="3a5fc-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a5fc-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a5fc-118">Child elements</span></span>  
  
|<span data-ttu-id="3a5fc-119">Élément</span><span class="sxs-lookup"><span data-stu-id="3a5fc-119">Element</span></span>|<span data-ttu-id="3a5fc-120">Description</span><span class="sxs-lookup"><span data-stu-id="3a5fc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a5fc-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="3a5fc-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="3a5fc-122">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3a5fc-123">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a5fc-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a5fc-124">Parent elements</span></span>  
  
|<span data-ttu-id="3a5fc-125">Élément</span><span class="sxs-lookup"><span data-stu-id="3a5fc-125">Element</span></span>|<span data-ttu-id="3a5fc-126">Description</span><span class="sxs-lookup"><span data-stu-id="3a5fc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a5fc-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3a5fc-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="3a5fc-128">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="3a5fc-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a5fc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a5fc-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3a5fc-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="3a5fc-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3a5fc-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="3a5fc-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
