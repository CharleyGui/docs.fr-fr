---
title: <cancelRequestedQueries> de WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 205399330c1aa69b332c2149ee32d9b6098ccdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151166"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="d6ff7-102">\<cancelRequestedQueries> de WCF</span><span class="sxs-lookup"><span data-stu-id="d6ff7-102">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="d6ff7-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d6ff7-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="d6ff7-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d6ff7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="d6ff7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6ff7-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6ff7-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6ff7-107">Attributes and elements</span></span>  

<span data-ttu-id="d6ff7-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6ff7-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6ff7-109">Attributes</span></span>

<span data-ttu-id="d6ff7-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d6ff7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6ff7-111">Child elements</span></span>
  
|<span data-ttu-id="d6ff7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d6ff7-112">Element</span></span>|<span data-ttu-id="d6ff7-113">Description</span><span class="sxs-lookup"><span data-stu-id="d6ff7-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="d6ff7-114">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6ff7-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6ff7-115">Parent elements</span></span>  
  
|<span data-ttu-id="d6ff7-116">Élément</span><span class="sxs-lookup"><span data-stu-id="d6ff7-116">Element</span></span>|<span data-ttu-id="d6ff7-117">Description</span><span class="sxs-lookup"><span data-stu-id="d6ff7-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="d6ff7-118">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId>.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6ff7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6ff7-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="d6ff7-120">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="d6ff7-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d6ff7-121">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="d6ff7-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
