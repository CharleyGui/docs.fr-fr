---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f77a613f4eb0456a0085096aa478d37c78122217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946316"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="631e9-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="631e9-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="631e9-102">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="631e9-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="631e9-103">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="631e9-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="631e9-104">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="631e9-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="631e9-105">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="631e9-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="631e9-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="631e9-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="631e9-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="631e9-107">\<system.serviceModel></span></span>\
<span data-ttu-id="631e9-108">\<suivi des > </span><span class="sxs-lookup"><span data-stu-id="631e9-108">\<tracking></span></span>\
<span data-ttu-id="631e9-109">\<trackingProfile > </span><span class="sxs-lookup"><span data-stu-id="631e9-109">\<trackingProfile></span></span>\
<span data-ttu-id="631e9-110">\<Workflow > </span><span class="sxs-lookup"><span data-stu-id="631e9-110">\<workflow></span></span>\
<span data-ttu-id="631e9-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="631e9-111">\<faultPropagationQueries></span></span>\
<span data-ttu-id="631e9-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="631e9-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="631e9-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="631e9-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="631e9-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="631e9-114">Attributes and Elements</span></span>

<span data-ttu-id="631e9-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="631e9-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="631e9-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="631e9-116">Attributes</span></span>

|<span data-ttu-id="631e9-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="631e9-117">Attribute</span></span>|<span data-ttu-id="631e9-118">Description</span><span class="sxs-lookup"><span data-stu-id="631e9-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="631e9-119">activityName</span><span class="sxs-lookup"><span data-stu-id="631e9-119">activityName</span></span>|<span data-ttu-id="631e9-120">Chaîne qui spécifie le nom de l’activité de gestionnaire d’erreur qui a propagé l’erreur.</span><span class="sxs-lookup"><span data-stu-id="631e9-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="631e9-121">La valeur par défaut est \*, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="631e9-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="631e9-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="631e9-122">faultHandlerActivityName</span></span>|<span data-ttu-id="631e9-123">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="631e9-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="631e9-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="631e9-124">Child Elements</span></span>

<span data-ttu-id="631e9-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="631e9-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="631e9-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="631e9-126">Parent Elements</span></span>

|<span data-ttu-id="631e9-127">Élément</span><span class="sxs-lookup"><span data-stu-id="631e9-127">Element</span></span>|<span data-ttu-id="631e9-128">Description</span><span class="sxs-lookup"><span data-stu-id="631e9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="631e9-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="631e9-129">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="631e9-130">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="631e9-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="631e9-131">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="631e9-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="631e9-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="631e9-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="631e9-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="631e9-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="631e9-134">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="631e9-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
