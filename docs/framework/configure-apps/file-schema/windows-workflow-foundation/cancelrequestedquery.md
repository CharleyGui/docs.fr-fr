---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152285"
---
# \<cancelRequestedQuery>
<span data-ttu-id="c9cee-101">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="c9cee-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c9cee-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="c9cee-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c9cee-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c9cee-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="c9cee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9cee-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9cee-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c9cee-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c9cee-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c9cee-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9cee-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c9cee-107">Attributes</span></span>  
  
|<span data-ttu-id="c9cee-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c9cee-108">Attribute</span></span>|<span data-ttu-id="c9cee-109">Description</span><span class="sxs-lookup"><span data-stu-id="c9cee-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9cee-110">activityName</span><span class="sxs-lookup"><span data-stu-id="c9cee-110">activityName</span></span>|<span data-ttu-id="c9cee-111">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="c9cee-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="c9cee-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="c9cee-112">childActivityName</span></span>|<span data-ttu-id="c9cee-113">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="c9cee-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9cee-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c9cee-114">Child Elements</span></span>  
 <span data-ttu-id="c9cee-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c9cee-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9cee-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c9cee-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c9cee-117">Élément</span><span class="sxs-lookup"><span data-stu-id="c9cee-117">Element</span></span>|<span data-ttu-id="c9cee-118">Description</span><span class="sxs-lookup"><span data-stu-id="c9cee-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="c9cee-119">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="c9cee-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c9cee-120">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="c9cee-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9cee-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9cee-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9cee-122">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c9cee-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9cee-123">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="c9cee-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
