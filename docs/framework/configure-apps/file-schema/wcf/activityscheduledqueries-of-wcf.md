---
title: <activityScheduledQueries>de WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 83e71e2038377ae4c1c3b17334eece3f30c919f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920317"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="227ae-102">\<> activityScheduledQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="227ae-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="227ae-103">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="227ae-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="227ae-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="227ae-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="227ae-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="227ae-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="227ae-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="227ae-106">\<system.serviceModel></span></span>  
<span data-ttu-id="227ae-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="227ae-107">\<tracking></span></span>  
<span data-ttu-id="227ae-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="227ae-108">\<profiles></span></span>  
<span data-ttu-id="227ae-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="227ae-109">\<trackingProfile></span></span>  
<span data-ttu-id="227ae-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="227ae-110">\<workflow></span></span>  
<span data-ttu-id="227ae-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="227ae-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227ae-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="227ae-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="227ae-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="227ae-113">Attributes and elements</span></span>  

<span data-ttu-id="227ae-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="227ae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="227ae-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="227ae-115">Attributes</span></span>  

<span data-ttu-id="227ae-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="227ae-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="227ae-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="227ae-117">Child elements</span></span>  
  
|<span data-ttu-id="227ae-118">Élément</span><span class="sxs-lookup"><span data-stu-id="227ae-118">Element</span></span>|<span data-ttu-id="227ae-119">Description</span><span class="sxs-lookup"><span data-stu-id="227ae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="227ae-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="227ae-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="227ae-121">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="227ae-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="227ae-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="227ae-122">Parent elements</span></span>  
  
|<span data-ttu-id="227ae-123">Élément</span><span class="sxs-lookup"><span data-stu-id="227ae-123">Element</span></span>|<span data-ttu-id="227ae-124">Description</span><span class="sxs-lookup"><span data-stu-id="227ae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="227ae-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="227ae-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="227ae-126">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="227ae-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="227ae-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="227ae-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="227ae-128">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="227ae-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="227ae-129">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="227ae-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
