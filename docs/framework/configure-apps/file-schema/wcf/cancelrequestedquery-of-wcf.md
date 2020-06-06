---
title: <cancelRequestedQuery>de WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850052"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="69aa9-102">\<cancelRequestedQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="69aa9-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="69aa9-103">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="69aa9-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="69aa9-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="69aa9-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="69aa9-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="69aa9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="69aa9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69aa9-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69aa9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="69aa9-107">Attributes and elements</span></span>

<span data-ttu-id="69aa9-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="69aa9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="69aa9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="69aa9-109">Attributes</span></span>  
  
|<span data-ttu-id="69aa9-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="69aa9-110">Attribute</span></span>|<span data-ttu-id="69aa9-111">Description</span><span class="sxs-lookup"><span data-stu-id="69aa9-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="69aa9-112">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="69aa9-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="69aa9-113">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="69aa9-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69aa9-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="69aa9-114">Child elements</span></span>

<span data-ttu-id="69aa9-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="69aa9-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="69aa9-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="69aa9-116">Parent elements</span></span>
  
|<span data-ttu-id="69aa9-117">Élément</span><span class="sxs-lookup"><span data-stu-id="69aa9-117">Element</span></span>|<span data-ttu-id="69aa9-118">Description</span><span class="sxs-lookup"><span data-stu-id="69aa9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="69aa9-119">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="69aa9-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69aa9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69aa9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="69aa9-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="69aa9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="69aa9-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="69aa9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
