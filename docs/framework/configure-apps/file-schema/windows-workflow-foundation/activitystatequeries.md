---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398954"
---
# <a name="activitystatequeries"></a><span data-ttu-id="93e1b-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="93e1b-101">\<activityStateQueries></span></span>
<span data-ttu-id="93e1b-102">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="93e1b-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="93e1b-103">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="93e1b-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="93e1b-104">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="93e1b-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="93e1b-105">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="93e1b-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="93e1b-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="93e1b-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="93e1b-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93e1b-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93e1b-108">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="93e1b-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="93e1b-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="93e1b-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="93e1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="93e1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="93e1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="93e1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="93e1b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="93e1b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93e1b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93e1b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93e1b-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93e1b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="93e1b-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="93e1b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93e1b-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="93e1b-116">Attributes</span></span>  
 <span data-ttu-id="93e1b-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93e1b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93e1b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93e1b-118">Child Elements</span></span>  
  
|<span data-ttu-id="93e1b-119">Élément</span><span class="sxs-lookup"><span data-stu-id="93e1b-119">Element</span></span>|<span data-ttu-id="93e1b-120">Description</span><span class="sxs-lookup"><span data-stu-id="93e1b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93e1b-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="93e1b-121">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="93e1b-122">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="93e1b-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="93e1b-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="93e1b-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93e1b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93e1b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="93e1b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="93e1b-125">Element</span></span>|<span data-ttu-id="93e1b-126">Description</span><span class="sxs-lookup"><span data-stu-id="93e1b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93e1b-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="93e1b-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="93e1b-128">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="93e1b-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93e1b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93e1b-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="93e1b-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="93e1b-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="93e1b-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="93e1b-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
