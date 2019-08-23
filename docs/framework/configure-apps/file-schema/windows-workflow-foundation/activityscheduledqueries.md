---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945536"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="946a1-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="946a1-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="946a1-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="946a1-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="946a1-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="946a1-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="946a1-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="946a1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="946a1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="946a1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="946a1-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="946a1-106">\<tracking></span></span>  
<span data-ttu-id="946a1-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="946a1-107">\<trackingProfile></span></span>  
<span data-ttu-id="946a1-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="946a1-108">\<workflow></span></span>  
<span data-ttu-id="946a1-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="946a1-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946a1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="946a1-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="946a1-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="946a1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="946a1-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="946a1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="946a1-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="946a1-113">Attributes</span></span>  
 <span data-ttu-id="946a1-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="946a1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="946a1-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="946a1-115">Child Elements</span></span>  
  
|<span data-ttu-id="946a1-116">Élément</span><span class="sxs-lookup"><span data-stu-id="946a1-116">Element</span></span>|<span data-ttu-id="946a1-117">Description</span><span class="sxs-lookup"><span data-stu-id="946a1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="946a1-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="946a1-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="946a1-119">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="946a1-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="946a1-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="946a1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="946a1-121">Élément</span><span class="sxs-lookup"><span data-stu-id="946a1-121">Element</span></span>|<span data-ttu-id="946a1-122">Description</span><span class="sxs-lookup"><span data-stu-id="946a1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="946a1-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="946a1-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="946a1-124">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="946a1-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="946a1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="946a1-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="946a1-126">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="946a1-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="946a1-127">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="946a1-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
