---
title: <bookmarkResumptionQueries>de WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850126"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="40a1b-102">\<> bookmarkResumptionQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="40a1b-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="40a1b-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="40a1b-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="40a1b-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="40a1b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="40a1b-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="40a1b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="40a1b-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40a1b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40a1b-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="40a1b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="40a1b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="40a1b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="40a1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="40a1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="40a1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="40a1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="40a1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="40a1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="40a1b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="40a1b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="40a1b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40a1b-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40a1b-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40a1b-114">Attributes and elements</span></span>  
  
<span data-ttu-id="40a1b-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40a1b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40a1b-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="40a1b-116">Attributes</span></span>  
  
<span data-ttu-id="40a1b-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="40a1b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40a1b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40a1b-118">Child elements</span></span>  
  
|<span data-ttu-id="40a1b-119">Élément</span><span class="sxs-lookup"><span data-stu-id="40a1b-119">Element</span></span>|<span data-ttu-id="40a1b-120">Description</span><span class="sxs-lookup"><span data-stu-id="40a1b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40a1b-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="40a1b-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="40a1b-122">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="40a1b-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="40a1b-123">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="40a1b-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40a1b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40a1b-124">Parent elements</span></span>  
  
|<span data-ttu-id="40a1b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="40a1b-125">Element</span></span>|<span data-ttu-id="40a1b-126">Description</span><span class="sxs-lookup"><span data-stu-id="40a1b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40a1b-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="40a1b-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="40a1b-128">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="40a1b-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40a1b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40a1b-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="40a1b-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="40a1b-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="40a1b-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="40a1b-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
