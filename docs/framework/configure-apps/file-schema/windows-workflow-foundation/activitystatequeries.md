---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 4663ccedcafb6b151de75568afd3743c83c75224
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189823"
---
# \<activityStateQueries>

<span data-ttu-id="46029-101">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="46029-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="46029-102">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="46029-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="46029-103">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="46029-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="46029-104">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="46029-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="46029-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="46029-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="46029-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46029-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46029-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46029-107">Attributes and Elements</span></span>  

 <span data-ttu-id="46029-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46029-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46029-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="46029-109">Attributes</span></span>  

 <span data-ttu-id="46029-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46029-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46029-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46029-111">Child Elements</span></span>  
  
|<span data-ttu-id="46029-112">Élément</span><span class="sxs-lookup"><span data-stu-id="46029-112">Element</span></span>|<span data-ttu-id="46029-113">Description</span><span class="sxs-lookup"><span data-stu-id="46029-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="46029-114">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="46029-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="46029-115">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="46029-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46029-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46029-116">Parent Elements</span></span>  
  
|<span data-ttu-id="46029-117">Élément</span><span class="sxs-lookup"><span data-stu-id="46029-117">Element</span></span>|<span data-ttu-id="46029-118">Description</span><span class="sxs-lookup"><span data-stu-id="46029-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="46029-119">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="46029-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46029-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46029-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="46029-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="46029-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="46029-122">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="46029-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
