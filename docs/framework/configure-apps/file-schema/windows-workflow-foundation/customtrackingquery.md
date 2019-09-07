---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 695fccf88ac0d8a672e710ccc632ea58dd2fc693
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398766"
---
# <a name="customtrackingquery"></a><span data-ttu-id="babb3-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="babb3-101">\<customTrackingQuery></span></span>
<span data-ttu-id="babb3-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="babb3-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="babb3-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="babb3-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="babb3-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="babb3-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="babb3-106">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="babb3-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="babb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="babb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="babb3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="babb3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="babb3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="babb3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babb3-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="babb3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="babb3-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="babb3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="babb3-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="babb3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="babb3-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="babb3-115">Attributes</span></span>  
  
|<span data-ttu-id="babb3-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="babb3-116">Attribute</span></span>|<span data-ttu-id="babb3-117">Description</span><span class="sxs-lookup"><span data-stu-id="babb3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="babb3-118">activityName</span><span class="sxs-lookup"><span data-stu-id="babb3-118">activityName</span></span>|<span data-ttu-id="babb3-119">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="babb3-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="babb3-120">name</span><span class="sxs-lookup"><span data-stu-id="babb3-120">name</span></span>|<span data-ttu-id="babb3-121">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="babb3-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="babb3-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="babb3-122">Child Elements</span></span>  
 <span data-ttu-id="babb3-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="babb3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="babb3-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="babb3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="babb3-125">Élément</span><span class="sxs-lookup"><span data-stu-id="babb3-125">Element</span></span>|<span data-ttu-id="babb3-126">Description</span><span class="sxs-lookup"><span data-stu-id="babb3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="babb3-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="babb3-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="babb3-128">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="babb3-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="babb3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="babb3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="babb3-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="babb3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="babb3-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="babb3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
