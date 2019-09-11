---
title: <cancelRequestedQuery>de WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850052"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="17f04-102">\<> cancelRequestedQuery de WCF</span><span class="sxs-lookup"><span data-stu-id="17f04-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="17f04-103">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="17f04-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="17f04-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="17f04-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="17f04-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="17f04-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="17f04-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="17f04-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="17f04-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="17f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="17f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="17f04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="17f04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="17f04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17f04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="17f04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="17f04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="17f04-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17f04-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17f04-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="17f04-115">Attributes and elements</span></span>

<span data-ttu-id="17f04-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="17f04-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="17f04-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="17f04-117">Attributes</span></span>  
  
|<span data-ttu-id="17f04-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="17f04-118">Attribute</span></span>|<span data-ttu-id="17f04-119">Description</span><span class="sxs-lookup"><span data-stu-id="17f04-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="17f04-120">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="17f04-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="17f04-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="17f04-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17f04-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="17f04-122">Child elements</span></span>

<span data-ttu-id="17f04-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="17f04-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="17f04-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="17f04-124">Parent elements</span></span>
  
|<span data-ttu-id="17f04-125">Élément</span><span class="sxs-lookup"><span data-stu-id="17f04-125">Element</span></span>|<span data-ttu-id="17f04-126">Description</span><span class="sxs-lookup"><span data-stu-id="17f04-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17f04-127">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="17f04-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="17f04-128">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="17f04-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17f04-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17f04-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="17f04-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="17f04-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="17f04-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="17f04-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
