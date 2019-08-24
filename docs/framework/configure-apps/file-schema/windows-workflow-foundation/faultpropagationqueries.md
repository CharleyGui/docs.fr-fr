---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: b8052138a729fcba7cb158d81a63126f59e0c4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988727"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="e4a0c-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e4a0c-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="e4a0c-102">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e4a0c-103">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e4a0c-104">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e4a0c-105">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e4a0c-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e4a0c-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e4a0c-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e4a0c-107">\<system.serviceModel></span></span>  
<span data-ttu-id="e4a0c-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e4a0c-108">\<tracking></span></span>  
<span data-ttu-id="e4a0c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e4a0c-109">\<trackingProfile></span></span>  
<span data-ttu-id="e4a0c-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e4a0c-110">\<workflow></span></span>  
<span data-ttu-id="e4a0c-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e4a0c-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a0c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a0c-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4a0c-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e4a0c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e4a0c-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4a0c-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="e4a0c-115">Attributes</span></span>  
 <span data-ttu-id="e4a0c-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4a0c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e4a0c-117">Child Elements</span></span>  
  
|<span data-ttu-id="e4a0c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="e4a0c-118">Element</span></span>|<span data-ttu-id="e4a0c-119">Description</span><span class="sxs-lookup"><span data-stu-id="e4a0c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4a0c-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e4a0c-120">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e4a0c-121">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e4a0c-122">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4a0c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e4a0c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e4a0c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e4a0c-124">Element</span></span>|<span data-ttu-id="e4a0c-125">Description</span><span class="sxs-lookup"><span data-stu-id="e4a0c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4a0c-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e4a0c-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e4a0c-127">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="e4a0c-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4a0c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4a0c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e4a0c-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e4a0c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e4a0c-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e4a0c-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
