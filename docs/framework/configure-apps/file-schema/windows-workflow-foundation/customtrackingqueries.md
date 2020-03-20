---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152259"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="358bf-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="358bf-101">\<customTrackingQueries></span></span>
<span data-ttu-id="358bf-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="358bf-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="358bf-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="358bf-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="358bf-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="358bf-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="358bf-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="358bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="358bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="358bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="358bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="358bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span><span class="sxs-lookup"><span data-stu-id="358bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358bf-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="358bf-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="358bf-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="358bf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="358bf-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="358bf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="358bf-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="358bf-114">Attributes</span></span>  
 <span data-ttu-id="358bf-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="358bf-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="358bf-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="358bf-116">Child Elements</span></span>  
  
|<span data-ttu-id="358bf-117">Élément</span><span class="sxs-lookup"><span data-stu-id="358bf-117">Element</span></span>|<span data-ttu-id="358bf-118">Description</span><span class="sxs-lookup"><span data-stu-id="358bf-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358bf-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="358bf-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="358bf-120">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="358bf-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="358bf-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="358bf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="358bf-122">Élément</span><span class="sxs-lookup"><span data-stu-id="358bf-122">Element</span></span>|<span data-ttu-id="358bf-123">Description</span><span class="sxs-lookup"><span data-stu-id="358bf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358bf-124">\<flux de travail></span><span class="sxs-lookup"><span data-stu-id="358bf-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="358bf-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **activitéDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="358bf-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="358bf-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="358bf-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="358bf-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="358bf-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="358bf-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="358bf-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
