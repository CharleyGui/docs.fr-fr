---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152129"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="e45a6-101">\<fautePropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e45a6-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="e45a6-102">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e45a6-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e45a6-103">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e45a6-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e45a6-104">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e45a6-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e45a6-105">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e45a6-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e45a6-106">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e45a6-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e45a6-107">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e45a6-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e45a6-108">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e45a6-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e45a6-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e45a6-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e45a6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e45a6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e45a6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e45a6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e45a6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<fautePropagationQueries>**</span><span class="sxs-lookup"><span data-stu-id="e45a6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e45a6-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e45a6-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e45a6-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e45a6-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e45a6-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e45a6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e45a6-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="e45a6-116">Attributes</span></span>  
 <span data-ttu-id="e45a6-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e45a6-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e45a6-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e45a6-118">Child Elements</span></span>  
  
|<span data-ttu-id="e45a6-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e45a6-119">Element</span></span>|<span data-ttu-id="e45a6-120">Description</span><span class="sxs-lookup"><span data-stu-id="e45a6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e45a6-121">\<fautePropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e45a6-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e45a6-122">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e45a6-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e45a6-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e45a6-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e45a6-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e45a6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e45a6-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e45a6-125">Element</span></span>|<span data-ttu-id="e45a6-126">Description</span><span class="sxs-lookup"><span data-stu-id="e45a6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e45a6-127">\<flux de travail></span><span class="sxs-lookup"><span data-stu-id="e45a6-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e45a6-128">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **activitéDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="e45a6-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e45a6-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e45a6-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e45a6-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e45a6-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e45a6-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e45a6-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
