---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 72a2d6f8439e720bb7bf236bd942552224e85501
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189725"
---
# \<argument>

<span data-ttu-id="42c8a-101">Élément de configuration qui représente un argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="42c8a-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="42c8a-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="42c8a-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="42c8a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c8a-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42c8a-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="42c8a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="42c8a-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="42c8a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42c8a-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="42c8a-106">Attributes</span></span>  
  
|<span data-ttu-id="42c8a-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="42c8a-107">Attribute</span></span>|<span data-ttu-id="42c8a-108">Description</span><span class="sxs-lookup"><span data-stu-id="42c8a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42c8a-109">name</span><span class="sxs-lookup"><span data-stu-id="42c8a-109">name</span></span>|<span data-ttu-id="42c8a-110">Chaîne qui spécifie le nom de l'argument.</span><span class="sxs-lookup"><span data-stu-id="42c8a-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42c8a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="42c8a-111">Child Elements</span></span>  

 <span data-ttu-id="42c8a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="42c8a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42c8a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="42c8a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="42c8a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="42c8a-114">Element</span></span>|<span data-ttu-id="42c8a-115">Description</span><span class="sxs-lookup"><span data-stu-id="42c8a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="42c8a-116">Collection d’arguments associés à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="42c8a-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42c8a-117">Notes</span><span class="sxs-lookup"><span data-stu-id="42c8a-117">Remarks</span></span>  

 <span data-ttu-id="42c8a-118">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="42c8a-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="42c8a-119">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="42c8a-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="42c8a-120">Vous pouvez utiliser les [\<arguments>](arguments.md) [\<states>](states.md) éléments, et [\<states>](states.md) pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="42c8a-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="42c8a-121">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="42c8a-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="42c8a-122">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide de [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="42c8a-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42c8a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42c8a-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="42c8a-124">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="42c8a-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="42c8a-125">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="42c8a-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
