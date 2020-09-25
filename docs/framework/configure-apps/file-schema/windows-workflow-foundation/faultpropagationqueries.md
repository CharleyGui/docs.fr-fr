---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 24e9136729df1352ebb1e665d1ebaf0ce9dc28a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175835"
---
# \<faultPropagationQueries>

<span data-ttu-id="5497b-101">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="5497b-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5497b-102">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="5497b-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5497b-103">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="5497b-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5497b-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5497b-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="5497b-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5497b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="5497b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5497b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5497b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5497b-107">Attributes and Elements</span></span>  

 <span data-ttu-id="5497b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5497b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5497b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5497b-109">Attributes</span></span>  

 <span data-ttu-id="5497b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5497b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5497b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5497b-111">Child Elements</span></span>  
  
|<span data-ttu-id="5497b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5497b-112">Element</span></span>|<span data-ttu-id="5497b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5497b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="5497b-114">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="5497b-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5497b-115">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="5497b-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5497b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5497b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5497b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="5497b-117">Element</span></span>|<span data-ttu-id="5497b-118">Description</span><span class="sxs-lookup"><span data-stu-id="5497b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="5497b-119">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="5497b-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5497b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5497b-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5497b-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="5497b-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5497b-122">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="5497b-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
