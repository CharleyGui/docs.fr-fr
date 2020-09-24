---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 59a76ea772dc8d06c390e3bca9d531df5f11e5f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148722"
---
# \<customTrackingQuery>

<span data-ttu-id="db4b4-101">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="db4b4-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="db4b4-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="db4b4-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="db4b4-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="db4b4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="db4b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db4b4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db4b4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db4b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="db4b4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db4b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db4b4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="db4b4-107">Attributes</span></span>  
  
|<span data-ttu-id="db4b4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="db4b4-108">Attribute</span></span>|<span data-ttu-id="db4b4-109">Description</span><span class="sxs-lookup"><span data-stu-id="db4b4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db4b4-110">activityName</span><span class="sxs-lookup"><span data-stu-id="db4b4-110">activityName</span></span>|<span data-ttu-id="db4b4-111">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="db4b4-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="db4b4-112">name</span><span class="sxs-lookup"><span data-stu-id="db4b4-112">name</span></span>|<span data-ttu-id="db4b4-113">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="db4b4-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db4b4-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db4b4-114">Child Elements</span></span>  

 <span data-ttu-id="db4b4-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db4b4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db4b4-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db4b4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="db4b4-117">Élément</span><span class="sxs-lookup"><span data-stu-id="db4b4-117">Element</span></span>|<span data-ttu-id="db4b4-118">Description</span><span class="sxs-lookup"><span data-stu-id="db4b4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="db4b4-119">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="db4b4-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db4b4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db4b4-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="db4b4-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="db4b4-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="db4b4-122">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="db4b4-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
