---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 936267f7d61dfd09af45ddb96b4406c92c30b3b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148774"
---
# \<activityScheduledQueries>

<span data-ttu-id="f1257-101">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="f1257-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f1257-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="f1257-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="f1257-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f1257-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="f1257-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1257-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1257-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f1257-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f1257-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f1257-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1257-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f1257-107">Attributes</span></span>  

 <span data-ttu-id="f1257-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f1257-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1257-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f1257-109">Child Elements</span></span>  
  
|<span data-ttu-id="f1257-110">Élément</span><span class="sxs-lookup"><span data-stu-id="f1257-110">Element</span></span>|<span data-ttu-id="f1257-111">Description</span><span class="sxs-lookup"><span data-stu-id="f1257-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="f1257-112">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="f1257-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1257-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f1257-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f1257-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f1257-114">Element</span></span>|<span data-ttu-id="f1257-115">Description</span><span class="sxs-lookup"><span data-stu-id="f1257-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="f1257-116">Élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par la propriété **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="f1257-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1257-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1257-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f1257-118">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f1257-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f1257-119">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="f1257-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
