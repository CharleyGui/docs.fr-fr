---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152409"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="bdb8d-101">\<activitéScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="bdb8d-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="bdb8d-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="bdb8d-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="bdb8d-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bdb8d-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bdb8d-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="bdb8d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="bdb8d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="bdb8d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="bdb8d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activitéScheduledQueries>**](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="bdb8d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="bdb8d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activitéScheduledQuery>**</span><span class="sxs-lookup"><span data-stu-id="bdb8d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb8d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb8d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdb8d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bdb8d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bdb8d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdb8d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="bdb8d-115">Attributes</span></span>  
  
|<span data-ttu-id="bdb8d-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="bdb8d-116">Attribute</span></span>|<span data-ttu-id="bdb8d-117">Description</span><span class="sxs-lookup"><span data-stu-id="bdb8d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bdb8d-118">activityName</span><span class="sxs-lookup"><span data-stu-id="bdb8d-118">activityName</span></span>|<span data-ttu-id="bdb8d-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="bdb8d-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="bdb8d-120">childActivityName</span></span>|<span data-ttu-id="bdb8d-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdb8d-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bdb8d-122">Child Elements</span></span>  
 <span data-ttu-id="bdb8d-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdb8d-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bdb8d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bdb8d-125">Élément</span><span class="sxs-lookup"><span data-stu-id="bdb8d-125">Element</span></span>|<span data-ttu-id="bdb8d-126">Description</span><span class="sxs-lookup"><span data-stu-id="bdb8d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdb8d-127">\<activitéScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="bdb8d-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="bdb8d-128">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="bdb8d-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdb8d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdb8d-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bdb8d-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="bdb8d-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bdb8d-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="bdb8d-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
