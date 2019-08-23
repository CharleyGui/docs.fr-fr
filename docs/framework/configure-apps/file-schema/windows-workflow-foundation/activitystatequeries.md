---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945457"
---
# <a name="activitystatequeries"></a><span data-ttu-id="ca32d-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ca32d-101">\<activityStateQueries></span></span>
<span data-ttu-id="ca32d-102">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="ca32d-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ca32d-103">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité «Envoyer un message électronique» se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="ca32d-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ca32d-104">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="ca32d-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ca32d-105">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ca32d-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ca32d-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ca32d-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ca32d-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ca32d-107">\<system.serviceModel></span></span>  
<span data-ttu-id="ca32d-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="ca32d-108">\<tracking></span></span>  
<span data-ttu-id="ca32d-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ca32d-109">\<trackingProfile></span></span>  
<span data-ttu-id="ca32d-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ca32d-110">\<workflow></span></span>  
<span data-ttu-id="ca32d-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ca32d-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca32d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca32d-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca32d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca32d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ca32d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca32d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca32d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca32d-115">Attributes</span></span>  
 <span data-ttu-id="ca32d-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca32d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca32d-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca32d-117">Child Elements</span></span>  
  
|<span data-ttu-id="ca32d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="ca32d-118">Element</span></span>|<span data-ttu-id="ca32d-119">Description</span><span class="sxs-lookup"><span data-stu-id="ca32d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca32d-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ca32d-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="ca32d-121">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ca32d-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ca32d-122">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="ca32d-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca32d-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca32d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ca32d-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ca32d-124">Element</span></span>|<span data-ttu-id="ca32d-125">Description</span><span class="sxs-lookup"><span data-stu-id="ca32d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca32d-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ca32d-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="ca32d-127">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ca32d-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca32d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca32d-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ca32d-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ca32d-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ca32d-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ca32d-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
