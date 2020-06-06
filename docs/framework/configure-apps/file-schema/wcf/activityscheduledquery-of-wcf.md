---
title: <activityScheduledQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850467"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="2dffd-102">\<activityScheduledQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="2dffd-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="2dffd-103">Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="2dffd-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2dffd-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="2dffd-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="2dffd-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2dffd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="2dffd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dffd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dffd-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2dffd-107">Attributes and elements</span></span>  

<span data-ttu-id="2dffd-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2dffd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dffd-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2dffd-109">Attributes</span></span>  
  
|<span data-ttu-id="2dffd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2dffd-110">Attribute</span></span>|<span data-ttu-id="2dffd-111">Description</span><span class="sxs-lookup"><span data-stu-id="2dffd-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2dffd-112">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="2dffd-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="2dffd-113">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="2dffd-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2dffd-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2dffd-114">Child elements</span></span>

<span data-ttu-id="2dffd-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2dffd-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2dffd-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2dffd-116">Parent elements</span></span>  
  
|<span data-ttu-id="2dffd-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2dffd-117">Element</span></span>|<span data-ttu-id="2dffd-118">Description</span><span class="sxs-lookup"><span data-stu-id="2dffd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="2dffd-119">Collection de requêtes qui permettent d’effectuer le suivi d’une activité planifiée pour être exécutée par une activité parente.</span><span class="sxs-lookup"><span data-stu-id="2dffd-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2dffd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dffd-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="2dffd-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="2dffd-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2dffd-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="2dffd-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
