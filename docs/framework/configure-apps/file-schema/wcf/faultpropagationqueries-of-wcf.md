---
title: <faultPropagationQueries>de WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855264"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="f58a2-102">\<> faultPropagationQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="f58a2-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="f58a2-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="f58a2-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f58a2-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="f58a2-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f58a2-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="f58a2-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f58a2-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f58a2-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="f58a2-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f58a2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f58a2-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f58a2-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f58a2-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f58a2-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f58a2-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f58a2-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="f58a2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="f58a2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="f58a2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f58a2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="f58a2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f58a2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="f58a2-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="f58a2-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58a2-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f58a2-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f58a2-116">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f58a2-116">Attributes and elements</span></span>

<span data-ttu-id="f58a2-117">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f58a2-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="f58a2-118">Attributs</span><span class="sxs-lookup"><span data-stu-id="f58a2-118">Attributes</span></span>

<span data-ttu-id="f58a2-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f58a2-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="f58a2-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f58a2-120">Child elements</span></span>

|<span data-ttu-id="f58a2-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f58a2-121">Element</span></span>|<span data-ttu-id="f58a2-122">Description</span><span class="sxs-lookup"><span data-stu-id="f58a2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f58a2-123">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f58a2-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="f58a2-124">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="f58a2-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f58a2-125">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="f58a2-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f58a2-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f58a2-126">Parent elements</span></span>  
  
|<span data-ttu-id="f58a2-127">Élément</span><span class="sxs-lookup"><span data-stu-id="f58a2-127">Element</span></span>|<span data-ttu-id="f58a2-128">Description</span><span class="sxs-lookup"><span data-stu-id="f58a2-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f58a2-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f58a2-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="f58a2-130">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="f58a2-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f58a2-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f58a2-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f58a2-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f58a2-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f58a2-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f58a2-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
