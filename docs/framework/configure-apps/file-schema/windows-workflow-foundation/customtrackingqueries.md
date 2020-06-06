---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152259"
---
# \<customTrackingQueries>
<span data-ttu-id="f48f7-101">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="f48f7-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f48f7-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f48f7-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f48f7-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f48f7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="f48f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f48f7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f48f7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f48f7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f48f7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f48f7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f48f7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f48f7-107">Attributes</span></span>  
 <span data-ttu-id="f48f7-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f48f7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f48f7-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f48f7-109">Child Elements</span></span>  
  
|<span data-ttu-id="f48f7-110">Élément</span><span class="sxs-lookup"><span data-stu-id="f48f7-110">Element</span></span>|<span data-ttu-id="f48f7-111">Description</span><span class="sxs-lookup"><span data-stu-id="f48f7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="f48f7-112">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="f48f7-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f48f7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f48f7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f48f7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f48f7-114">Element</span></span>|<span data-ttu-id="f48f7-115">Description</span><span class="sxs-lookup"><span data-stu-id="f48f7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="f48f7-116">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="f48f7-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f48f7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f48f7-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f48f7-118">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f48f7-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f48f7-119">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f48f7-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
