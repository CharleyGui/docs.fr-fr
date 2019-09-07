---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398826"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="ce2fb-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ce2fb-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="ce2fb-102">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="ce2fb-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ce2fb-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="ce2fb-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="ce2fb-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ce2fb-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce2fb-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ce2fb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ce2fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ce2fb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ce2fb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="ce2fb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2fb-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce2fb-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce2fb-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ce2fb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ce2fb-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ce2fb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce2fb-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ce2fb-114">Attributes</span></span>  
 <span data-ttu-id="ce2fb-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ce2fb-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ce2fb-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ce2fb-116">Child Elements</span></span>  
  
|<span data-ttu-id="ce2fb-117">Élément</span><span class="sxs-lookup"><span data-stu-id="ce2fb-117">Element</span></span>|<span data-ttu-id="ce2fb-118">Description</span><span class="sxs-lookup"><span data-stu-id="ce2fb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce2fb-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="ce2fb-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="ce2fb-120">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="ce2fb-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce2fb-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ce2fb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce2fb-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ce2fb-122">Element</span></span>|<span data-ttu-id="ce2fb-123">Description</span><span class="sxs-lookup"><span data-stu-id="ce2fb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce2fb-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ce2fb-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="ce2fb-125">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ce2fb-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce2fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce2fb-126">See also</span></span>

- [<span data-ttu-id="ce2fb-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ce2fb-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ce2fb-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ce2fb-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
