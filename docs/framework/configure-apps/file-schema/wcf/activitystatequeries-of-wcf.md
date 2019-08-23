---
title: <activityStateQueries>de WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920297"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="848c6-102">\<> activityStateQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="848c6-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="848c6-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="848c6-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="848c6-104">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité «Envoyer un message électronique» se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="848c6-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="848c6-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="848c6-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="848c6-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="848c6-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="848c6-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="848c6-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="848c6-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="848c6-108">\<system.serviceModel></span></span>  
<span data-ttu-id="848c6-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="848c6-109">\<tracking></span></span>  
<span data-ttu-id="848c6-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="848c6-110">\<profiles></span></span>  
<span data-ttu-id="848c6-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="848c6-111">\<trackingProfile></span></span>  
<span data-ttu-id="848c6-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="848c6-112">\<workflow></span></span>  
<span data-ttu-id="848c6-113">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="848c6-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="848c6-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="848c6-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="848c6-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="848c6-115">Attributes and elements</span></span>

<span data-ttu-id="848c6-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="848c6-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="848c6-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="848c6-117">Attributes</span></span>  

<span data-ttu-id="848c6-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="848c6-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="848c6-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="848c6-119">Child elements</span></span>

|<span data-ttu-id="848c6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="848c6-120">Element</span></span>|<span data-ttu-id="848c6-121">Description</span><span class="sxs-lookup"><span data-stu-id="848c6-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="848c6-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="848c6-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="848c6-123">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="848c6-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="848c6-124">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="848c6-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="848c6-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="848c6-125">Parent elements</span></span>

|<span data-ttu-id="848c6-126">Élément</span><span class="sxs-lookup"><span data-stu-id="848c6-126">Element</span></span>|<span data-ttu-id="848c6-127">Description</span><span class="sxs-lookup"><span data-stu-id="848c6-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="848c6-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="848c6-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="848c6-129">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="848c6-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="848c6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="848c6-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="848c6-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="848c6-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="848c6-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="848c6-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
