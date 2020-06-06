---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398911"
---
# \<arguments>
<span data-ttu-id="d439c-101">Représente une collection d'arguments associés à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="d439c-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="d439c-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d439c-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="d439c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d439c-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d439c-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d439c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d439c-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d439c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d439c-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="d439c-106">Attributes</span></span>  
 <span data-ttu-id="d439c-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d439c-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d439c-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d439c-108">Child Elements</span></span>  
  
|<span data-ttu-id="d439c-109">Élément</span><span class="sxs-lookup"><span data-stu-id="d439c-109">Element</span></span>|<span data-ttu-id="d439c-110">Description</span><span class="sxs-lookup"><span data-stu-id="d439c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="d439c-111">Argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="d439c-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d439c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d439c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d439c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d439c-113">Element</span></span>|<span data-ttu-id="d439c-114">Description</span><span class="sxs-lookup"><span data-stu-id="d439c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="d439c-115">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="d439c-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d439c-116">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="d439c-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d439c-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="d439c-117">Remarks</span></span>  
 <span data-ttu-id="d439c-118">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d439c-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d439c-119">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="d439c-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d439c-120">Vous pouvez utiliser les [\<arguments>](arguments.md) [\<states>](states.md) éléments, et [\<states>](states.md) pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="d439c-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d439c-121">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="d439c-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d439c-122">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide de [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="d439c-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d439c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d439c-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d439c-124">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="d439c-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d439c-125">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="d439c-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
