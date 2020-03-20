---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152305"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="079d6-101">\<annulerRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="079d6-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="079d6-102">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="079d6-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="079d6-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="079d6-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="079d6-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="079d6-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="079d6-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="079d6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="079d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="079d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="079d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="079d6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<annulerRequestedQueries>**</span><span class="sxs-lookup"><span data-stu-id="079d6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079d6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079d6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="079d6-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="079d6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="079d6-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="079d6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="079d6-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="079d6-114">Attributes</span></span>  
 <span data-ttu-id="079d6-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="079d6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="079d6-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="079d6-116">Child Elements</span></span>  
  
|<span data-ttu-id="079d6-117">Élément</span><span class="sxs-lookup"><span data-stu-id="079d6-117">Element</span></span>|<span data-ttu-id="079d6-118">Description</span><span class="sxs-lookup"><span data-stu-id="079d6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="079d6-119">\<annulerRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="079d6-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="079d6-120">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="079d6-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="079d6-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="079d6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="079d6-122">Élément</span><span class="sxs-lookup"><span data-stu-id="079d6-122">Element</span></span>|<span data-ttu-id="079d6-123">Description</span><span class="sxs-lookup"><span data-stu-id="079d6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="079d6-124">\<flux de travail></span><span class="sxs-lookup"><span data-stu-id="079d6-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="079d6-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **activitéDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="079d6-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="079d6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="079d6-126">See also</span></span>

- [<span data-ttu-id="079d6-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="079d6-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="079d6-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="079d6-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
