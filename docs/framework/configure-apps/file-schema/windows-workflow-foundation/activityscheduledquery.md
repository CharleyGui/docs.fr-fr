---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: aa6ee435c66303b5089b459ecc4ed3023297636d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398972"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="9e9e7-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="9e9e7-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="9e9e7-102">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="9e9e7-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="9e9e7-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9e9e7-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9e9e7-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9e9e7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="9e9e7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="9e9e7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="9e9e7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="9e9e7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="9e9e7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="9e9e7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9e7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e9e7-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e9e7-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9e9e7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9e9e7-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e9e7-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="9e9e7-115">Attributes</span></span>  
  
|<span data-ttu-id="9e9e7-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="9e9e7-116">Attribute</span></span>|<span data-ttu-id="9e9e7-117">Description</span><span class="sxs-lookup"><span data-stu-id="9e9e7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e9e7-118">activityName</span><span class="sxs-lookup"><span data-stu-id="9e9e7-118">activityName</span></span>|<span data-ttu-id="9e9e7-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="9e9e7-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="9e9e7-120">childActivityName</span></span>|<span data-ttu-id="9e9e7-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e9e7-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9e9e7-122">Child Elements</span></span>  
 <span data-ttu-id="9e9e7-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e9e7-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9e9e7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9e9e7-125">Élément</span><span class="sxs-lookup"><span data-stu-id="9e9e7-125">Element</span></span>|<span data-ttu-id="9e9e7-126">Description</span><span class="sxs-lookup"><span data-stu-id="9e9e7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e9e7-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="9e9e7-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="9e9e7-128">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="9e9e7-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e9e7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e9e7-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9e9e7-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="9e9e7-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9e9e7-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="9e9e7-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
