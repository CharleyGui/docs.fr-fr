---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 3a666b7c7affda06fbf03515b045eddf2a1f6af5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175887"
---
# \<customTrackingQueries>

<span data-ttu-id="c2a1e-101">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="c2a1e-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c2a1e-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c2a1e-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c2a1e-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c2a1e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="c2a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2a1e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2a1e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c2a1e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c2a1e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c2a1e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2a1e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c2a1e-107">Attributes</span></span>  

 <span data-ttu-id="c2a1e-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c2a1e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2a1e-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c2a1e-109">Child Elements</span></span>  
  
|<span data-ttu-id="c2a1e-110">Élément</span><span class="sxs-lookup"><span data-stu-id="c2a1e-110">Element</span></span>|<span data-ttu-id="c2a1e-111">Description</span><span class="sxs-lookup"><span data-stu-id="c2a1e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="c2a1e-112">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="c2a1e-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2a1e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c2a1e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c2a1e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c2a1e-114">Element</span></span>|<span data-ttu-id="c2a1e-115">Description</span><span class="sxs-lookup"><span data-stu-id="c2a1e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="c2a1e-116">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="c2a1e-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2a1e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2a1e-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c2a1e-118">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c2a1e-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c2a1e-119">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="c2a1e-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
