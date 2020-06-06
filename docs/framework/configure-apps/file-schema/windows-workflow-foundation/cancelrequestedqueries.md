---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152305"
---
# \<cancelRequestedQueries>
<span data-ttu-id="771de-101">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="771de-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="771de-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="771de-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="771de-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="771de-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="771de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="771de-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="771de-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="771de-105">Attributes and Elements</span></span>  
 <span data-ttu-id="771de-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="771de-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="771de-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="771de-107">Attributes</span></span>  
 <span data-ttu-id="771de-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="771de-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="771de-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="771de-109">Child Elements</span></span>  
  
|<span data-ttu-id="771de-110">Élément</span><span class="sxs-lookup"><span data-stu-id="771de-110">Element</span></span>|<span data-ttu-id="771de-111">Description</span><span class="sxs-lookup"><span data-stu-id="771de-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="771de-112">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="771de-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="771de-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="771de-113">Parent Elements</span></span>  
  
|<span data-ttu-id="771de-114">Élément</span><span class="sxs-lookup"><span data-stu-id="771de-114">Element</span></span>|<span data-ttu-id="771de-115">Description</span><span class="sxs-lookup"><span data-stu-id="771de-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="771de-116">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="771de-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="771de-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="771de-117">See also</span></span>

- [<span data-ttu-id="771de-118">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="771de-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="771de-119">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="771de-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
