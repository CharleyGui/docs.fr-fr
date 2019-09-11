---
title: <customTrackingQueries>de WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855432"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="6fe0c-102">\<> customTrackingQueries de WCF</span><span class="sxs-lookup"><span data-stu-id="6fe0c-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="6fe0c-103">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6fe0c-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="6fe0c-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6fe0c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="6fe0c-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6fe0c-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6fe0c-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6fe0c-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6fe0c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6fe0c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="6fe0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="6fe0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="6fe0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6fe0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="6fe0c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6fe0c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="6fe0c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="6fe0c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6fe0c-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fe0c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fe0c-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6fe0c-114">Attributes and elements</span></span>

<span data-ttu-id="6fe0c-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fe0c-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="6fe0c-116">Attributes</span></span>

<span data-ttu-id="6fe0c-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6fe0c-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6fe0c-118">Child elements</span></span>
  
|<span data-ttu-id="6fe0c-119">Élément</span><span class="sxs-lookup"><span data-stu-id="6fe0c-119">Element</span></span>|<span data-ttu-id="6fe0c-120">Description</span><span class="sxs-lookup"><span data-stu-id="6fe0c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fe0c-121">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="6fe0c-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="6fe0c-122">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fe0c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6fe0c-123">Parent elements</span></span>  
  
|<span data-ttu-id="6fe0c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6fe0c-124">Element</span></span>|<span data-ttu-id="6fe0c-125">Description</span><span class="sxs-lookup"><span data-stu-id="6fe0c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fe0c-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6fe0c-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6fe0c-127">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="6fe0c-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fe0c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fe0c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6fe0c-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="6fe0c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6fe0c-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="6fe0c-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
