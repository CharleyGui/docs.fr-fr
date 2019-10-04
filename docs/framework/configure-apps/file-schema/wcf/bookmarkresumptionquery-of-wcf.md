---
title: <bookmarkResumptionQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834003"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="93561-102">\<> bookmarkResumptionQuery de WCF</span><span class="sxs-lookup"><span data-stu-id="93561-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="93561-103">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="93561-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="93561-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="93561-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="93561-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="93561-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="93561-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93561-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93561-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="93561-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="93561-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93561-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="93561-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="93561-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="93561-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93561-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="93561-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93561-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="93561-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93561-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="93561-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="93561-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93561-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93561-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93561-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93561-115">Attributes and elements</span></span>

<span data-ttu-id="93561-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="93561-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93561-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="93561-117">Attributes</span></span>  
  
|<span data-ttu-id="93561-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="93561-118">Attribute</span></span>|<span data-ttu-id="93561-119">Description</span><span class="sxs-lookup"><span data-stu-id="93561-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="93561-120">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="93561-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93561-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93561-121">Child elements</span></span>

<span data-ttu-id="93561-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93561-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="93561-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93561-123">Parent elements</span></span>  
  
|<span data-ttu-id="93561-124">Élément</span><span class="sxs-lookup"><span data-stu-id="93561-124">Element</span></span>|<span data-ttu-id="93561-125">Description</span><span class="sxs-lookup"><span data-stu-id="93561-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93561-126">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="93561-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="93561-127">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="93561-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93561-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93561-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="93561-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="93561-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="93561-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="93561-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
