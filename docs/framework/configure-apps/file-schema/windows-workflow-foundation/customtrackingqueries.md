---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 429940b2ed69d8be497626f634a21adca540b529
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945824"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="9ee7e-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9ee7e-101">\<customTrackingQueries></span></span>
<span data-ttu-id="9ee7e-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="9ee7e-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9ee7e-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9ee7e-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9ee7e-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9ee7e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9ee7e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ee7e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9ee7e-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="9ee7e-106">\<tracking></span></span>  
<span data-ttu-id="9ee7e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9ee7e-107">\<trackingProfile></span></span>  
<span data-ttu-id="9ee7e-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9ee7e-108">\<workflow></span></span>  
<span data-ttu-id="9ee7e-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9ee7e-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee7e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee7e-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ee7e-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ee7e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9ee7e-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ee7e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ee7e-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ee7e-113">Attributes</span></span>  
 <span data-ttu-id="9ee7e-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9ee7e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ee7e-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ee7e-115">Child Elements</span></span>  
  
|<span data-ttu-id="9ee7e-116">Élément</span><span class="sxs-lookup"><span data-stu-id="9ee7e-116">Element</span></span>|<span data-ttu-id="9ee7e-117">Description</span><span class="sxs-lookup"><span data-stu-id="9ee7e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ee7e-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="9ee7e-118">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="9ee7e-119">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="9ee7e-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ee7e-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ee7e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9ee7e-121">Élément</span><span class="sxs-lookup"><span data-stu-id="9ee7e-121">Element</span></span>|<span data-ttu-id="9ee7e-122">Description</span><span class="sxs-lookup"><span data-stu-id="9ee7e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ee7e-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9ee7e-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="9ee7e-124">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="9ee7e-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ee7e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ee7e-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ee7e-126">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="9ee7e-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ee7e-127">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="9ee7e-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
