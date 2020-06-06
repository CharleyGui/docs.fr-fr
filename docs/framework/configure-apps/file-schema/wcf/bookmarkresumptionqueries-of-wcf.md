---
title: <bookmarkResumptionQueries>de WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850126"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="e84c9-102">\<bookmarkResumptionQueries>de WCF</span><span class="sxs-lookup"><span data-stu-id="e84c9-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="e84c9-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e84c9-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e84c9-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="e84c9-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="e84c9-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e84c9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="e84c9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e84c9-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e84c9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e84c9-107">Attributes and elements</span></span>  
  
<span data-ttu-id="e84c9-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e84c9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e84c9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e84c9-109">Attributes</span></span>  
  
<span data-ttu-id="e84c9-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e84c9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e84c9-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e84c9-111">Child elements</span></span>  
  
|<span data-ttu-id="e84c9-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e84c9-112">Element</span></span>|<span data-ttu-id="e84c9-113">Description</span><span class="sxs-lookup"><span data-stu-id="e84c9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="e84c9-114">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e84c9-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e84c9-115">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="e84c9-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e84c9-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e84c9-116">Parent elements</span></span>  
  
|<span data-ttu-id="e84c9-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e84c9-117">Element</span></span>|<span data-ttu-id="e84c9-118">Description</span><span class="sxs-lookup"><span data-stu-id="e84c9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e84c9-119">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="e84c9-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e84c9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e84c9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e84c9-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e84c9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e84c9-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e84c9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
