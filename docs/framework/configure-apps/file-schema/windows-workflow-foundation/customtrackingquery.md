---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9605f5d050baf046ff3c549c19191934299a65e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945752"
---
# <a name="customtrackingquery"></a><span data-ttu-id="d7346-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d7346-101">\<customTrackingQuery></span></span>
<span data-ttu-id="d7346-102">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="d7346-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d7346-103">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d7346-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d7346-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d7346-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d7346-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d7346-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d7346-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d7346-106">\<tracking></span></span>  
<span data-ttu-id="d7346-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d7346-107">\<trackingProfile></span></span>  
<span data-ttu-id="d7346-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d7346-108">\<workflow></span></span>  
<span data-ttu-id="d7346-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d7346-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="d7346-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d7346-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7346-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7346-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7346-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d7346-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d7346-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d7346-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7346-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d7346-114">Attributes</span></span>  
  
|<span data-ttu-id="d7346-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d7346-115">Attribute</span></span>|<span data-ttu-id="d7346-116">Description</span><span class="sxs-lookup"><span data-stu-id="d7346-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7346-117">activityName</span><span class="sxs-lookup"><span data-stu-id="d7346-117">activityName</span></span>|<span data-ttu-id="d7346-118">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="d7346-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d7346-119">name</span><span class="sxs-lookup"><span data-stu-id="d7346-119">name</span></span>|<span data-ttu-id="d7346-120">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="d7346-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7346-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d7346-121">Child Elements</span></span>  
 <span data-ttu-id="d7346-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d7346-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7346-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d7346-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d7346-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d7346-124">Element</span></span>|<span data-ttu-id="d7346-125">Description</span><span class="sxs-lookup"><span data-stu-id="d7346-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7346-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d7346-126">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="d7346-127">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="d7346-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7346-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7346-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d7346-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="d7346-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d7346-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="d7346-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
