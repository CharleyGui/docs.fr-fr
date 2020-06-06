---
title: <bookmarkResumptionQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834003"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="da893-102">\<bookmarkResumptionQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="da893-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="da893-103">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="da893-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="da893-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="da893-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="da893-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="da893-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="da893-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da893-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da893-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="da893-107">Attributes and elements</span></span>

<span data-ttu-id="da893-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="da893-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da893-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="da893-109">Attributes</span></span>  
  
|<span data-ttu-id="da893-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="da893-110">Attribute</span></span>|<span data-ttu-id="da893-111">Description</span><span class="sxs-lookup"><span data-stu-id="da893-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="da893-112">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="da893-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da893-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="da893-113">Child elements</span></span>

<span data-ttu-id="da893-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="da893-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="da893-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="da893-115">Parent elements</span></span>  
  
|<span data-ttu-id="da893-116">Élément</span><span class="sxs-lookup"><span data-stu-id="da893-116">Element</span></span>|<span data-ttu-id="da893-117">Description</span><span class="sxs-lookup"><span data-stu-id="da893-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="da893-118">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="da893-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da893-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da893-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="da893-120">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="da893-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="da893-121">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="da893-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
