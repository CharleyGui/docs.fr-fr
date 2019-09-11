---
title: <customTrackingQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855422"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="c3d67-102">\<> customTrackingQuery de WCF</span><span class="sxs-lookup"><span data-stu-id="c3d67-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="c3d67-103">Représente une requête utilisée pour suivre les événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="c3d67-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="c3d67-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c3d67-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="c3d67-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c3d67-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c3d67-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c3d67-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="c3d67-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="c3d67-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="c3d67-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="c3d67-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="c3d67-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c3d67-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="c3d67-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="c3d67-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d67-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3d67-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3d67-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c3d67-115">Attributes and elements</span></span>  

<span data-ttu-id="c3d67-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c3d67-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3d67-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="c3d67-117">Attributes</span></span>  
  
|<span data-ttu-id="c3d67-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="c3d67-118">Attribute</span></span>|<span data-ttu-id="c3d67-119">Description</span><span class="sxs-lookup"><span data-stu-id="c3d67-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="c3d67-120">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="c3d67-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="c3d67-121">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="c3d67-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3d67-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c3d67-122">Child elements</span></span>

<span data-ttu-id="c3d67-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c3d67-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3d67-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c3d67-124">Parent elements</span></span>

|<span data-ttu-id="c3d67-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c3d67-125">Element</span></span>|<span data-ttu-id="c3d67-126">Description</span><span class="sxs-lookup"><span data-stu-id="c3d67-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3d67-127">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="c3d67-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="c3d67-128">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="c3d67-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="c3d67-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3d67-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c3d67-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c3d67-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c3d67-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="c3d67-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
