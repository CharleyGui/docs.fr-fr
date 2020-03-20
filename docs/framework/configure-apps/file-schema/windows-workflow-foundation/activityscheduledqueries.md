---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152422"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="08690-101">\<activitéScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="08690-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="08690-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="08690-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="08690-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="08690-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="08690-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="08690-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="08690-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08690-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08690-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="08690-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="08690-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="08690-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="08690-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="08690-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="08690-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="08690-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="08690-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activitéScheduledQueries>**</span><span class="sxs-lookup"><span data-stu-id="08690-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08690-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08690-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08690-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="08690-112">Attributes and Elements</span></span>  
 <span data-ttu-id="08690-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="08690-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08690-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="08690-114">Attributes</span></span>  
 <span data-ttu-id="08690-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="08690-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08690-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="08690-116">Child Elements</span></span>  
  
|<span data-ttu-id="08690-117">Élément</span><span class="sxs-lookup"><span data-stu-id="08690-117">Element</span></span>|<span data-ttu-id="08690-118">Description</span><span class="sxs-lookup"><span data-stu-id="08690-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08690-119">\<activitéScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="08690-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="08690-120">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="08690-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08690-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="08690-121">Parent Elements</span></span>  
  
|<span data-ttu-id="08690-122">Élément</span><span class="sxs-lookup"><span data-stu-id="08690-122">Element</span></span>|<span data-ttu-id="08690-123">Description</span><span class="sxs-lookup"><span data-stu-id="08690-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08690-124">\<flux de travail></span><span class="sxs-lookup"><span data-stu-id="08690-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="08690-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **activitéDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="08690-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08690-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08690-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="08690-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="08690-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="08690-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="08690-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
