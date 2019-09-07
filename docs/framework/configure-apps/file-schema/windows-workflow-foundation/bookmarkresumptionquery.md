---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398853"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="70fd9-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="70fd9-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="70fd9-102">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="70fd9-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="70fd9-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="70fd9-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="70fd9-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="70fd9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70fd9-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="70fd9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="70fd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="70fd9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="70fd9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="70fd9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="70fd9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="70fd9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70fd9-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70fd9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70fd9-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70fd9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="70fd9-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70fd9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70fd9-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="70fd9-115">Attributes</span></span>  
  
|<span data-ttu-id="70fd9-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="70fd9-116">Attribute</span></span>|<span data-ttu-id="70fd9-117">Description</span><span class="sxs-lookup"><span data-stu-id="70fd9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70fd9-118">name</span><span class="sxs-lookup"><span data-stu-id="70fd9-118">name</span></span>|<span data-ttu-id="70fd9-119">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="70fd9-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70fd9-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70fd9-120">Child Elements</span></span>  
 <span data-ttu-id="70fd9-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="70fd9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70fd9-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70fd9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="70fd9-123">Élément</span><span class="sxs-lookup"><span data-stu-id="70fd9-123">Element</span></span>|<span data-ttu-id="70fd9-124">Description</span><span class="sxs-lookup"><span data-stu-id="70fd9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70fd9-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="70fd9-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="70fd9-126">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="70fd9-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70fd9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70fd9-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="70fd9-128">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="70fd9-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="70fd9-129">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="70fd9-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
