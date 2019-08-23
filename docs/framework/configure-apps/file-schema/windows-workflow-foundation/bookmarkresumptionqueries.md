---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: f048612673a9b6b69c3cdded6526c76359c444e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945990"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="fe2d0-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="fe2d0-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="fe2d0-102">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fe2d0-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="fe2d0-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fe2d0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fe2d0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fe2d0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="fe2d0-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="fe2d0-106">\<tracking></span></span>  
<span data-ttu-id="fe2d0-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fe2d0-107">\<trackingProfile></span></span>  
<span data-ttu-id="fe2d0-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="fe2d0-108">\<workflow></span></span>  
<span data-ttu-id="fe2d0-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="fe2d0-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="fe2d0-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="fe2d0-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2d0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe2d0-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe2d0-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fe2d0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fe2d0-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe2d0-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="fe2d0-114">Attributes</span></span>  
 <span data-ttu-id="fe2d0-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe2d0-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fe2d0-116">Child Elements</span></span>  
  
|<span data-ttu-id="fe2d0-117">Élément</span><span class="sxs-lookup"><span data-stu-id="fe2d0-117">Element</span></span>|<span data-ttu-id="fe2d0-118">Description</span><span class="sxs-lookup"><span data-stu-id="fe2d0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe2d0-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="fe2d0-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="fe2d0-120">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fe2d0-121">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="fe2d0-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe2d0-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fe2d0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fe2d0-123">Élément</span><span class="sxs-lookup"><span data-stu-id="fe2d0-123">Element</span></span>|<span data-ttu-id="fe2d0-124">Description</span><span class="sxs-lookup"><span data-stu-id="fe2d0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe2d0-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="fe2d0-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="fe2d0-126">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="fe2d0-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe2d0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe2d0-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fe2d0-128">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="fe2d0-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fe2d0-129">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="fe2d0-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
