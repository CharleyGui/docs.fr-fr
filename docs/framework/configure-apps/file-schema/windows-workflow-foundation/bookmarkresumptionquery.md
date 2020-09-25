---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: efd1e4e54223ff9f5d60b4087fbe5b6bebf1af2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189588"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="beed9-101">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="beed9-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="beed9-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="beed9-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="beed9-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="beed9-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="beed9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beed9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beed9-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="beed9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="beed9-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="beed9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beed9-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="beed9-107">Attributes</span></span>  
  
|<span data-ttu-id="beed9-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="beed9-108">Attribute</span></span>|<span data-ttu-id="beed9-109">Description</span><span class="sxs-lookup"><span data-stu-id="beed9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="beed9-110">name</span><span class="sxs-lookup"><span data-stu-id="beed9-110">name</span></span>|<span data-ttu-id="beed9-111">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="beed9-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beed9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="beed9-112">Child Elements</span></span>  

 <span data-ttu-id="beed9-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="beed9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="beed9-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="beed9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="beed9-115">Élément</span><span class="sxs-lookup"><span data-stu-id="beed9-115">Element</span></span>|<span data-ttu-id="beed9-116">Description</span><span class="sxs-lookup"><span data-stu-id="beed9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="beed9-117">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="beed9-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="beed9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="beed9-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="beed9-119">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="beed9-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="beed9-120">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="beed9-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
