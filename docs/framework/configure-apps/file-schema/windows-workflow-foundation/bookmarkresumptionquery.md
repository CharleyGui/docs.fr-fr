---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 9043deb66e1a4314df97f4da41103e74676a270c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945958"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="7a078-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7a078-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="7a078-102">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="7a078-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7a078-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="7a078-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7a078-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7a078-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7a078-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7a078-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7a078-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="7a078-106">\<tracking></span></span>  
<span data-ttu-id="7a078-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7a078-107">\<trackingProfile></span></span>  
<span data-ttu-id="7a078-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7a078-108">\<workflow></span></span>  
<span data-ttu-id="7a078-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7a078-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7a078-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7a078-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a078-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a078-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a078-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7a078-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7a078-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7a078-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a078-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a078-114">Attributes</span></span>  
  
|<span data-ttu-id="7a078-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="7a078-115">Attribute</span></span>|<span data-ttu-id="7a078-116">Description</span><span class="sxs-lookup"><span data-stu-id="7a078-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a078-117">name</span><span class="sxs-lookup"><span data-stu-id="7a078-117">name</span></span>|<span data-ttu-id="7a078-118">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="7a078-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a078-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a078-119">Child Elements</span></span>  
 <span data-ttu-id="7a078-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7a078-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a078-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a078-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7a078-122">Élément</span><span class="sxs-lookup"><span data-stu-id="7a078-122">Element</span></span>|<span data-ttu-id="7a078-123">Description</span><span class="sxs-lookup"><span data-stu-id="7a078-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a078-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7a078-124">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="7a078-125">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="7a078-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a078-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a078-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7a078-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="7a078-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7a078-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="7a078-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
