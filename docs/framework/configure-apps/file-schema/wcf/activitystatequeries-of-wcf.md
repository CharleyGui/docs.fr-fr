---
title: <activityStateQueries>de WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850573"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="59ce5-102">\<> activityStateQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="59ce5-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="59ce5-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="59ce5-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="59ce5-104">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="59ce5-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="59ce5-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="59ce5-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="59ce5-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="59ce5-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="59ce5-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="59ce5-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="59ce5-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59ce5-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="59ce5-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="59ce5-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="59ce5-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="59ce5-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="59ce5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="59ce5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="59ce5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="59ce5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="59ce5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="59ce5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="59ce5-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="59ce5-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ce5-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ce5-115">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="59ce5-116">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="59ce5-116">Attributes and elements</span></span>

<span data-ttu-id="59ce5-117">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="59ce5-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="59ce5-118">Attributs</span><span class="sxs-lookup"><span data-stu-id="59ce5-118">Attributes</span></span>  

<span data-ttu-id="59ce5-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="59ce5-119">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="59ce5-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59ce5-120">Child elements</span></span>

|<span data-ttu-id="59ce5-121">Élément</span><span class="sxs-lookup"><span data-stu-id="59ce5-121">Element</span></span>|<span data-ttu-id="59ce5-122">Description</span><span class="sxs-lookup"><span data-stu-id="59ce5-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59ce5-123">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="59ce5-123">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="59ce5-124">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="59ce5-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="59ce5-125">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="59ce5-125">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="59ce5-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="59ce5-126">Parent elements</span></span>

|<span data-ttu-id="59ce5-127">Élément</span><span class="sxs-lookup"><span data-stu-id="59ce5-127">Element</span></span>|<span data-ttu-id="59ce5-128">Description</span><span class="sxs-lookup"><span data-stu-id="59ce5-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59ce5-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="59ce5-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="59ce5-130">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="59ce5-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="59ce5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ce5-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="59ce5-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="59ce5-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59ce5-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="59ce5-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
