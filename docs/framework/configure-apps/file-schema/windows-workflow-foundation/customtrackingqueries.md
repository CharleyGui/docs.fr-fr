---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 398b018ce407aee0687c95037753f3affa07aa9b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398779"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="cb20b-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="cb20b-101">\<customTrackingQueries></span></span>
<span data-ttu-id="cb20b-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="cb20b-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="cb20b-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="cb20b-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="cb20b-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cb20b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb20b-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cb20b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cb20b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cb20b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cb20b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cb20b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="cb20b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb20b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb20b-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb20b-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb20b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cb20b-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cb20b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb20b-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb20b-114">Attributes</span></span>  
 <span data-ttu-id="cb20b-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cb20b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb20b-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb20b-116">Child Elements</span></span>  
  
|<span data-ttu-id="cb20b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="cb20b-117">Element</span></span>|<span data-ttu-id="cb20b-118">Description</span><span class="sxs-lookup"><span data-stu-id="cb20b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb20b-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="cb20b-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="cb20b-120">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="cb20b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb20b-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb20b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cb20b-122">Élément</span><span class="sxs-lookup"><span data-stu-id="cb20b-122">Element</span></span>|<span data-ttu-id="cb20b-123">Description</span><span class="sxs-lookup"><span data-stu-id="cb20b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb20b-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cb20b-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cb20b-125">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="cb20b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb20b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb20b-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cb20b-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="cb20b-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cb20b-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="cb20b-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
