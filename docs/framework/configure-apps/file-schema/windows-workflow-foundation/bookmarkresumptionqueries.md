---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398866"
---
# \<bookmarkResumptionQueries>
<span data-ttu-id="fc9dd-101">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fc9dd-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="fc9dd-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fc9dd-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="fc9dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc9dd-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc9dd-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fc9dd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc9dd-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc9dd-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="fc9dd-107">Attributes</span></span>  
 <span data-ttu-id="fc9dd-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc9dd-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fc9dd-109">Child Elements</span></span>  
  
|<span data-ttu-id="fc9dd-110">Élément</span><span class="sxs-lookup"><span data-stu-id="fc9dd-110">Element</span></span>|<span data-ttu-id="fc9dd-111">Description</span><span class="sxs-lookup"><span data-stu-id="fc9dd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="fc9dd-112">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fc9dd-113">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc9dd-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fc9dd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fc9dd-115">Élément</span><span class="sxs-lookup"><span data-stu-id="fc9dd-115">Element</span></span>|<span data-ttu-id="fc9dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="fc9dd-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="fc9dd-117">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="fc9dd-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc9dd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc9dd-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fc9dd-119">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="fc9dd-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fc9dd-120">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="fc9dd-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
