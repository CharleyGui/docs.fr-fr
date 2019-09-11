---
title: <activityScheduledQueries>de WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850496"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="74a84-102">\<> activityScheduledQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="74a84-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="74a84-103">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="74a84-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="74a84-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="74a84-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="74a84-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="74a84-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74a84-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="74a84-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="74a84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="74a84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="74a84-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="74a84-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="74a84-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="74a84-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="74a84-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a84-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74a84-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74a84-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="74a84-114">Attributes and elements</span></span>  

<span data-ttu-id="74a84-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="74a84-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74a84-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="74a84-116">Attributes</span></span>  

<span data-ttu-id="74a84-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="74a84-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74a84-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="74a84-118">Child elements</span></span>  
  
|<span data-ttu-id="74a84-119">Élément</span><span class="sxs-lookup"><span data-stu-id="74a84-119">Element</span></span>|<span data-ttu-id="74a84-120">Description</span><span class="sxs-lookup"><span data-stu-id="74a84-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74a84-121">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="74a84-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="74a84-122">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="74a84-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74a84-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="74a84-123">Parent elements</span></span>  
  
|<span data-ttu-id="74a84-124">Élément</span><span class="sxs-lookup"><span data-stu-id="74a84-124">Element</span></span>|<span data-ttu-id="74a84-125">Description</span><span class="sxs-lookup"><span data-stu-id="74a84-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74a84-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="74a84-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="74a84-127">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="74a84-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74a84-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74a84-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="74a84-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="74a84-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="74a84-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="74a84-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
