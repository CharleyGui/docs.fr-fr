---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: cb1f96cb6ba2643e28552c354bdd5caf4d43285c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189641"
---
# \<arguments>

<span data-ttu-id="8e24b-101">Représente une collection d'arguments associés à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="8e24b-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="8e24b-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8e24b-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="8e24b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e24b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e24b-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8e24b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8e24b-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8e24b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e24b-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="8e24b-106">Attributes</span></span>  

 <span data-ttu-id="8e24b-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8e24b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e24b-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8e24b-108">Child Elements</span></span>  
  
|<span data-ttu-id="8e24b-109">Élément</span><span class="sxs-lookup"><span data-stu-id="8e24b-109">Element</span></span>|<span data-ttu-id="8e24b-110">Description</span><span class="sxs-lookup"><span data-stu-id="8e24b-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="8e24b-111">Argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="8e24b-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e24b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8e24b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8e24b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="8e24b-113">Element</span></span>|<span data-ttu-id="8e24b-114">Description</span><span class="sxs-lookup"><span data-stu-id="8e24b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="8e24b-115">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="8e24b-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8e24b-116">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="8e24b-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e24b-117">Notes</span><span class="sxs-lookup"><span data-stu-id="8e24b-117">Remarks</span></span>  

 <span data-ttu-id="8e24b-118">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="8e24b-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="8e24b-119">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="8e24b-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="8e24b-120">Vous pouvez utiliser les [\<arguments>](arguments.md) [\<states>](states.md) éléments, et [\<states>](states.md) pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="8e24b-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="8e24b-121">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="8e24b-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8e24b-122">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide de [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="8e24b-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e24b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e24b-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8e24b-124">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="8e24b-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8e24b-125">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="8e24b-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
