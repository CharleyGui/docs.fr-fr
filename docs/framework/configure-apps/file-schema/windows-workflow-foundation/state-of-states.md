---
title: <state> de <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 391e552bce34d637a324c78702cb0e7121f2c999
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398649"
---
# <a name="state-of-states"></a><span data-ttu-id="c73a3-102">\<state> de \<states></span><span class="sxs-lookup"><span data-stu-id="c73a3-102">\<state> of \<states></span></span>
<span data-ttu-id="c73a3-103">Élément de configuration qui contient l'état de l'activité faisant l'objet d'un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="c73a3-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="c73a3-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c73a3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="c73a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c73a3-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c73a3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c73a3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c73a3-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c73a3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c73a3-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c73a3-108">Attributes</span></span>  
  
|<span data-ttu-id="c73a3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c73a3-109">Attribute</span></span>|<span data-ttu-id="c73a3-110">Description</span><span class="sxs-lookup"><span data-stu-id="c73a3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c73a3-111">name</span><span class="sxs-lookup"><span data-stu-id="c73a3-111">name</span></span>|<span data-ttu-id="c73a3-112">Chaîne qui spécifie l'état de l'activité faisant l'objet d'un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="c73a3-112">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c73a3-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c73a3-113">Child Elements</span></span>  
 <span data-ttu-id="c73a3-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c73a3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c73a3-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c73a3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c73a3-116">Élément</span><span class="sxs-lookup"><span data-stu-id="c73a3-116">Element</span></span>|<span data-ttu-id="c73a3-117">Description</span><span class="sxs-lookup"><span data-stu-id="c73a3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="c73a3-118">Collection d’éléments de configuration qui contiennent les états de l’activité faisant l’objet d’un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="c73a3-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c73a3-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="c73a3-119">Remarks</span></span>  
 <span data-ttu-id="c73a3-120">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="c73a3-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="c73a3-121">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="c73a3-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="c73a3-122">Vous pouvez utiliser les [\<arguments>](arguments.md) [\<states>](states.md) éléments, et [\<states>](states.md) pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="c73a3-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="c73a3-123">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="c73a3-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="c73a3-124">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide de [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="c73a3-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c73a3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c73a3-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c73a3-126">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c73a3-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c73a3-127">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="c73a3-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
