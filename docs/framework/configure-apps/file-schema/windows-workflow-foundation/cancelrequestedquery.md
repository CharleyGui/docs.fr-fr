---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5de459717fdc0dbf946f12dceda18dce79ca4b06
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398814"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="a9210-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="a9210-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="a9210-102">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="a9210-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a9210-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="a9210-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a9210-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a9210-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a9210-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a9210-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a9210-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a9210-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a9210-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a9210-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="a9210-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="a9210-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="a9210-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9210-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9210-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9210-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9210-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a9210-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9210-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9210-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9210-115">Attributes</span></span>  
  
|<span data-ttu-id="a9210-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="a9210-116">Attribute</span></span>|<span data-ttu-id="a9210-117">Description</span><span class="sxs-lookup"><span data-stu-id="a9210-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9210-118">activityName</span><span class="sxs-lookup"><span data-stu-id="a9210-118">activityName</span></span>|<span data-ttu-id="a9210-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="a9210-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a9210-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a9210-120">childActivityName</span></span>|<span data-ttu-id="a9210-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="a9210-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9210-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9210-122">Child Elements</span></span>  
 <span data-ttu-id="a9210-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a9210-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9210-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9210-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a9210-125">Élément</span><span class="sxs-lookup"><span data-stu-id="a9210-125">Element</span></span>|<span data-ttu-id="a9210-126">Description</span><span class="sxs-lookup"><span data-stu-id="a9210-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9210-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a9210-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="a9210-128">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="a9210-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a9210-129">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="a9210-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9210-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9210-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a9210-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="a9210-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a9210-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="a9210-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
