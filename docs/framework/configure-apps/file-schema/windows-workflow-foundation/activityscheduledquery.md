---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945499"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="89b81-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="89b81-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="89b81-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="89b81-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="89b81-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="89b81-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="89b81-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="89b81-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="89b81-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="89b81-105">\<system.serviceModel></span></span>  
<span data-ttu-id="89b81-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="89b81-106">\<tracking></span></span>  
<span data-ttu-id="89b81-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="89b81-107">\<trackingProfile></span></span>  
<span data-ttu-id="89b81-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="89b81-108">\<workflow></span></span>  
<span data-ttu-id="89b81-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="89b81-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="89b81-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="89b81-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b81-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89b81-111">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89b81-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89b81-112">Attributes and Elements</span></span>  
 <span data-ttu-id="89b81-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89b81-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89b81-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="89b81-114">Attributes</span></span>  
  
|<span data-ttu-id="89b81-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="89b81-115">Attribute</span></span>|<span data-ttu-id="89b81-116">Description</span><span class="sxs-lookup"><span data-stu-id="89b81-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89b81-117">activityName</span><span class="sxs-lookup"><span data-stu-id="89b81-117">activityName</span></span>|<span data-ttu-id="89b81-118">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="89b81-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="89b81-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="89b81-119">childActivityName</span></span>|<span data-ttu-id="89b81-120">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="89b81-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89b81-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89b81-121">Child Elements</span></span>  
 <span data-ttu-id="89b81-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89b81-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89b81-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89b81-123">Parent Elements</span></span>  
  
|<span data-ttu-id="89b81-124">Élément</span><span class="sxs-lookup"><span data-stu-id="89b81-124">Element</span></span>|<span data-ttu-id="89b81-125">Description</span><span class="sxs-lookup"><span data-stu-id="89b81-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89b81-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="89b81-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="89b81-127">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="89b81-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89b81-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b81-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="89b81-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="89b81-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="89b81-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="89b81-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
