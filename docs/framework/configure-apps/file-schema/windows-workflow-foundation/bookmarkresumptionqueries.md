---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398866"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="160a7-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="160a7-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="160a7-102">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="160a7-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="160a7-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="160a7-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="160a7-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="160a7-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="160a7-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="160a7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="160a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="160a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="160a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="160a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="160a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="160a7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="160a7-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="160a7-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="160a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="160a7-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="160a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="160a7-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="160a7-114">Attributes</span></span>  
 <span data-ttu-id="160a7-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="160a7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="160a7-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="160a7-116">Child Elements</span></span>  
  
|<span data-ttu-id="160a7-117">Élément</span><span class="sxs-lookup"><span data-stu-id="160a7-117">Element</span></span>|<span data-ttu-id="160a7-118">Description</span><span class="sxs-lookup"><span data-stu-id="160a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="160a7-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="160a7-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="160a7-120">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="160a7-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="160a7-121">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="160a7-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="160a7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="160a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="160a7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="160a7-123">Element</span></span>|<span data-ttu-id="160a7-124">Description</span><span class="sxs-lookup"><span data-stu-id="160a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="160a7-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="160a7-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="160a7-126">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="160a7-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="160a7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="160a7-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="160a7-128">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="160a7-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="160a7-129">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="160a7-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
