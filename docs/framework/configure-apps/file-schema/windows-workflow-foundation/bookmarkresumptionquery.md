---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398853"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="6973c-101">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6973c-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6973c-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="6973c-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="6973c-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6973c-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="6973c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6973c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6973c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6973c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6973c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6973c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6973c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6973c-107">Attributes</span></span>  
  
|<span data-ttu-id="6973c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6973c-108">Attribute</span></span>|<span data-ttu-id="6973c-109">Description</span><span class="sxs-lookup"><span data-stu-id="6973c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6973c-110">name</span><span class="sxs-lookup"><span data-stu-id="6973c-110">name</span></span>|<span data-ttu-id="6973c-111">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="6973c-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6973c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6973c-112">Child Elements</span></span>  
 <span data-ttu-id="6973c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6973c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6973c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6973c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6973c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="6973c-115">Element</span></span>|<span data-ttu-id="6973c-116">Description</span><span class="sxs-lookup"><span data-stu-id="6973c-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="6973c-117">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6973c-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6973c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6973c-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6973c-119">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="6973c-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6973c-120">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="6973c-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
