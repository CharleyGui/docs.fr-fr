---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152207"
---
# <a name="customtrackingquery"></a><span data-ttu-id="4fa0b-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="4fa0b-101">\<customTrackingQuery></span></span>
<span data-ttu-id="4fa0b-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="4fa0b-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="4fa0b-104">Pour plus d’informations sur les requêtes de profil de suivi, voir [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4fa0b-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4fa0b-106">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4fa0b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="4fa0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<suiviProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="4fa0b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<flux de travail>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="4fa0b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="4fa0b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span><span class="sxs-lookup"><span data-stu-id="4fa0b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa0b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fa0b-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fa0b-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4fa0b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4fa0b-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fa0b-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="4fa0b-115">Attributes</span></span>  
  
|<span data-ttu-id="4fa0b-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="4fa0b-116">Attribute</span></span>|<span data-ttu-id="4fa0b-117">Description</span><span class="sxs-lookup"><span data-stu-id="4fa0b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fa0b-118">activityName</span><span class="sxs-lookup"><span data-stu-id="4fa0b-118">activityName</span></span>|<span data-ttu-id="4fa0b-119">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="4fa0b-120">name</span><span class="sxs-lookup"><span data-stu-id="4fa0b-120">name</span></span>|<span data-ttu-id="4fa0b-121">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fa0b-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4fa0b-122">Child Elements</span></span>  
 <span data-ttu-id="4fa0b-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fa0b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4fa0b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4fa0b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="4fa0b-125">Element</span></span>|<span data-ttu-id="4fa0b-126">Description</span><span class="sxs-lookup"><span data-stu-id="4fa0b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fa0b-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="4fa0b-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="4fa0b-128">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fa0b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fa0b-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4fa0b-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="4fa0b-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4fa0b-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="4fa0b-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
