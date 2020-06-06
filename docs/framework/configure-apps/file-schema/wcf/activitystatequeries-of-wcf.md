---
title: <activityStateQueries>de WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850573"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="2a179-102">\<activityStateQueries>de WCF</span><span class="sxs-lookup"><span data-stu-id="2a179-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="2a179-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="2a179-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="2a179-104">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="2a179-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="2a179-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="2a179-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="2a179-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="2a179-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="2a179-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2a179-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="2a179-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a179-108">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="2a179-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a179-109">Attributes and elements</span></span>

<span data-ttu-id="2a179-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a179-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="2a179-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a179-111">Attributes</span></span>  

<span data-ttu-id="2a179-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a179-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="2a179-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a179-113">Child elements</span></span>

|<span data-ttu-id="2a179-114">Élément</span><span class="sxs-lookup"><span data-stu-id="2a179-114">Element</span></span>|<span data-ttu-id="2a179-115">Description</span><span class="sxs-lookup"><span data-stu-id="2a179-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="2a179-116">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="2a179-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="2a179-117">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="2a179-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a179-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a179-118">Parent elements</span></span>

|<span data-ttu-id="2a179-119">Élément</span><span class="sxs-lookup"><span data-stu-id="2a179-119">Element</span></span>|<span data-ttu-id="2a179-120">Description</span><span class="sxs-lookup"><span data-stu-id="2a179-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="2a179-121">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="2a179-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2a179-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a179-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="2a179-123">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="2a179-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a179-124">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="2a179-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
