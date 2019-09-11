---
title: <cancelRequestedQueries>de WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850095"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="271f8-102">\<> cancelRequestedQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="271f8-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="271f8-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="271f8-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="271f8-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="271f8-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="271f8-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="271f8-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="271f8-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="271f8-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="271f8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="271f8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="271f8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="271f8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="271f8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="271f8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="271f8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271f8-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="271f8-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="271f8-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="271f8-114">Attributes and elements</span></span>  

<span data-ttu-id="271f8-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="271f8-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="271f8-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="271f8-116">Attributes</span></span>

<span data-ttu-id="271f8-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="271f8-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="271f8-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="271f8-118">Child elements</span></span>
  
|<span data-ttu-id="271f8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="271f8-119">Element</span></span>|<span data-ttu-id="271f8-120">Description</span><span class="sxs-lookup"><span data-stu-id="271f8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="271f8-121">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="271f8-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="271f8-122">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="271f8-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="271f8-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="271f8-123">Parent elements</span></span>  
  
|<span data-ttu-id="271f8-124">Élément</span><span class="sxs-lookup"><span data-stu-id="271f8-124">Element</span></span>|<span data-ttu-id="271f8-125">Description</span><span class="sxs-lookup"><span data-stu-id="271f8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="271f8-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="271f8-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="271f8-127">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId>.</span><span class="sxs-lookup"><span data-stu-id="271f8-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="271f8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="271f8-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="271f8-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="271f8-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="271f8-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="271f8-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
