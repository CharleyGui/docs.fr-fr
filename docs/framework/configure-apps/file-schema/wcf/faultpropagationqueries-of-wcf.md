---
title: <faultPropagationQueries>de WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855264"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="72b8e-102">\<faultPropagationQueries>de WCF</span><span class="sxs-lookup"><span data-stu-id="72b8e-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="72b8e-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="72b8e-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="72b8e-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="72b8e-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="72b8e-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="72b8e-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="72b8e-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="72b8e-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="72b8e-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="72b8e-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="72b8e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72b8e-108">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72b8e-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="72b8e-109">Attributes and elements</span></span>

<span data-ttu-id="72b8e-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="72b8e-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="72b8e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="72b8e-111">Attributes</span></span>

<span data-ttu-id="72b8e-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72b8e-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="72b8e-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="72b8e-113">Child elements</span></span>

|<span data-ttu-id="72b8e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="72b8e-114">Element</span></span>|<span data-ttu-id="72b8e-115">Description</span><span class="sxs-lookup"><span data-stu-id="72b8e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="72b8e-116">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="72b8e-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="72b8e-117">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="72b8e-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72b8e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="72b8e-118">Parent elements</span></span>  
  
|<span data-ttu-id="72b8e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="72b8e-119">Element</span></span>|<span data-ttu-id="72b8e-120">Description</span><span class="sxs-lookup"><span data-stu-id="72b8e-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="72b8e-121">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="72b8e-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b8e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72b8e-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="72b8e-123">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="72b8e-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="72b8e-124">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="72b8e-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
