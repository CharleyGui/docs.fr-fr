---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398979"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="cc7b5-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cc7b5-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="cc7b5-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cc7b5-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="cc7b5-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cc7b5-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc7b5-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cc7b5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cc7b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cc7b5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc7b5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cc7b5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="cc7b5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7b5-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7b5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc7b5-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cc7b5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cc7b5-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc7b5-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="cc7b5-114">Attributes</span></span>  
 <span data-ttu-id="cc7b5-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc7b5-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cc7b5-116">Child Elements</span></span>  
  
|<span data-ttu-id="cc7b5-117">Élément</span><span class="sxs-lookup"><span data-stu-id="cc7b5-117">Element</span></span>|<span data-ttu-id="cc7b5-118">Description</span><span class="sxs-lookup"><span data-stu-id="cc7b5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc7b5-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="cc7b5-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="cc7b5-120">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc7b5-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cc7b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cc7b5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="cc7b5-122">Element</span></span>|<span data-ttu-id="cc7b5-123">Description</span><span class="sxs-lookup"><span data-stu-id="cc7b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc7b5-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cc7b5-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cc7b5-125">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="cc7b5-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc7b5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc7b5-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cc7b5-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="cc7b5-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cc7b5-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="cc7b5-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
