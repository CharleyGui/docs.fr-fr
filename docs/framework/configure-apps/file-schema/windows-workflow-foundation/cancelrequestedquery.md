---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: d9c3f91edb41bd034bcd978b075d62f74b6e308d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945888"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="6edc8-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6edc8-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="6edc8-102">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="6edc8-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6edc8-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="6edc8-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6edc8-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6edc8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6edc8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6edc8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6edc8-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="6edc8-106">\<tracking></span></span>  
<span data-ttu-id="6edc8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6edc8-107">\<trackingProfile></span></span>  
<span data-ttu-id="6edc8-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6edc8-108">\<workflow></span></span>  
<span data-ttu-id="6edc8-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="6edc8-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="6edc8-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6edc8-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edc8-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6edc8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6edc8-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6edc8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6edc8-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6edc8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6edc8-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="6edc8-114">Attributes</span></span>  
  
|<span data-ttu-id="6edc8-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="6edc8-115">Attribute</span></span>|<span data-ttu-id="6edc8-116">Description</span><span class="sxs-lookup"><span data-stu-id="6edc8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6edc8-117">activityName</span><span class="sxs-lookup"><span data-stu-id="6edc8-117">activityName</span></span>|<span data-ttu-id="6edc8-118">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="6edc8-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6edc8-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6edc8-119">childActivityName</span></span>|<span data-ttu-id="6edc8-120">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="6edc8-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6edc8-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6edc8-121">Child Elements</span></span>  
 <span data-ttu-id="6edc8-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6edc8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6edc8-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6edc8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6edc8-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6edc8-124">Element</span></span>|<span data-ttu-id="6edc8-125">Description</span><span class="sxs-lookup"><span data-stu-id="6edc8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6edc8-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="6edc8-126">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="6edc8-127">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="6edc8-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6edc8-128">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="6edc8-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6edc8-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6edc8-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6edc8-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="6edc8-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6edc8-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="6edc8-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
