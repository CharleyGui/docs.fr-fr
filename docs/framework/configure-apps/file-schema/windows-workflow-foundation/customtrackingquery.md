---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152207"
---
# \<customTrackingQuery>
<span data-ttu-id="025e8-101">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="025e8-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="025e8-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="025e8-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="025e8-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="025e8-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="025e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="025e8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="025e8-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="025e8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="025e8-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="025e8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="025e8-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="025e8-107">Attributes</span></span>  
  
|<span data-ttu-id="025e8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="025e8-108">Attribute</span></span>|<span data-ttu-id="025e8-109">Description</span><span class="sxs-lookup"><span data-stu-id="025e8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="025e8-110">activityName</span><span class="sxs-lookup"><span data-stu-id="025e8-110">activityName</span></span>|<span data-ttu-id="025e8-111">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="025e8-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="025e8-112">name</span><span class="sxs-lookup"><span data-stu-id="025e8-112">name</span></span>|<span data-ttu-id="025e8-113">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="025e8-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="025e8-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="025e8-114">Child Elements</span></span>  
 <span data-ttu-id="025e8-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="025e8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="025e8-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="025e8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="025e8-117">Élément</span><span class="sxs-lookup"><span data-stu-id="025e8-117">Element</span></span>|<span data-ttu-id="025e8-118">Description</span><span class="sxs-lookup"><span data-stu-id="025e8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="025e8-119">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="025e8-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="025e8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="025e8-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="025e8-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="025e8-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="025e8-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="025e8-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
