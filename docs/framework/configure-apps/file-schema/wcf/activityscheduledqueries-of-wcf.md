---
title: <activityScheduledQueries>de WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850496"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="b60c4-102">\<activityScheduledQueries>de WCF</span><span class="sxs-lookup"><span data-stu-id="b60c4-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="b60c4-103">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="b60c4-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b60c4-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="b60c4-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="b60c4-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b60c4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b60c4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b60c4-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b60c4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b60c4-107">Attributes and elements</span></span>  

<span data-ttu-id="b60c4-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b60c4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b60c4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b60c4-109">Attributes</span></span>  

<span data-ttu-id="b60c4-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b60c4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b60c4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b60c4-111">Child elements</span></span>  
  
|<span data-ttu-id="b60c4-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b60c4-112">Element</span></span>|<span data-ttu-id="b60c4-113">Description</span><span class="sxs-lookup"><span data-stu-id="b60c4-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="b60c4-114">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="b60c4-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b60c4-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b60c4-115">Parent elements</span></span>  
  
|<span data-ttu-id="b60c4-116">Élément</span><span class="sxs-lookup"><span data-stu-id="b60c4-116">Element</span></span>|<span data-ttu-id="b60c4-117">Description</span><span class="sxs-lookup"><span data-stu-id="b60c4-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b60c4-118">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="b60c4-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b60c4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b60c4-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="b60c4-120">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="b60c4-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b60c4-121">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="b60c4-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
