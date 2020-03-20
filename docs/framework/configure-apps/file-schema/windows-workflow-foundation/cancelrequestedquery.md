---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152285"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="6826e-101">\<annulerRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6826e-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="6826e-102">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="6826e-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6826e-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="6826e-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6826e-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6826e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6826e-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6826e-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="6826e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="6826e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="6826e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="6826e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<annulerRequestedQueries>**](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="6826e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="6826e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<annulerRequestedQuery>**</span><span class="sxs-lookup"><span data-stu-id="6826e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6826e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6826e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6826e-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6826e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6826e-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6826e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6826e-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="6826e-115">Attributes</span></span>  
  
|<span data-ttu-id="6826e-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="6826e-116">Attribute</span></span>|<span data-ttu-id="6826e-117">Description</span><span class="sxs-lookup"><span data-stu-id="6826e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6826e-118">activityName</span><span class="sxs-lookup"><span data-stu-id="6826e-118">activityName</span></span>|<span data-ttu-id="6826e-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="6826e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6826e-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6826e-120">childActivityName</span></span>|<span data-ttu-id="6826e-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="6826e-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6826e-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6826e-122">Child Elements</span></span>  
 <span data-ttu-id="6826e-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6826e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6826e-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6826e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6826e-125">Élément</span><span class="sxs-lookup"><span data-stu-id="6826e-125">Element</span></span>|<span data-ttu-id="6826e-126">Description</span><span class="sxs-lookup"><span data-stu-id="6826e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6826e-127">\<fautePropagationQuery></span><span class="sxs-lookup"><span data-stu-id="6826e-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="6826e-128">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="6826e-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6826e-129">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="6826e-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6826e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6826e-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6826e-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="6826e-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6826e-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="6826e-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
