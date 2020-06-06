---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152409"
---
# \<activityScheduledQuery>
<span data-ttu-id="1356e-101">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="1356e-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1356e-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="1356e-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="1356e-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1356e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="1356e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1356e-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1356e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1356e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1356e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1356e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1356e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1356e-107">Attributes</span></span>  
  
|<span data-ttu-id="1356e-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1356e-108">Attribute</span></span>|<span data-ttu-id="1356e-109">Description</span><span class="sxs-lookup"><span data-stu-id="1356e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1356e-110">activityName</span><span class="sxs-lookup"><span data-stu-id="1356e-110">activityName</span></span>|<span data-ttu-id="1356e-111">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="1356e-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="1356e-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="1356e-112">childActivityName</span></span>|<span data-ttu-id="1356e-113">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="1356e-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1356e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1356e-114">Child Elements</span></span>  
 <span data-ttu-id="1356e-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1356e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1356e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1356e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1356e-117">Élément</span><span class="sxs-lookup"><span data-stu-id="1356e-117">Element</span></span>|<span data-ttu-id="1356e-118">Description</span><span class="sxs-lookup"><span data-stu-id="1356e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="1356e-119">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="1356e-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1356e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1356e-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1356e-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="1356e-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1356e-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="1356e-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
