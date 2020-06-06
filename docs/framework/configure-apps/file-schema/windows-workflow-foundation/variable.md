---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397766"
---
# \<variable>
<span data-ttu-id="16989-101">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="16989-101">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="16989-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="16989-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**  
  
## <a name="syntax"></a><span data-ttu-id="16989-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16989-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16989-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16989-104">Attributes and Elements</span></span>  
 <span data-ttu-id="16989-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16989-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16989-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="16989-106">Attributes</span></span>  
  
|<span data-ttu-id="16989-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="16989-107">Attribute</span></span>|<span data-ttu-id="16989-108">Description</span><span class="sxs-lookup"><span data-stu-id="16989-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16989-109">name</span><span class="sxs-lookup"><span data-stu-id="16989-109">name</span></span>|<span data-ttu-id="16989-110">Chaîne qui spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="16989-110">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16989-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16989-111">Child Elements</span></span>  
 <span data-ttu-id="16989-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16989-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16989-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16989-113">Parent Elements</span></span>  
  
|<span data-ttu-id="16989-114">Élément</span><span class="sxs-lookup"><span data-stu-id="16989-114">Element</span></span>|<span data-ttu-id="16989-115">Description</span><span class="sxs-lookup"><span data-stu-id="16989-115">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="16989-116">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="16989-116">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16989-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="16989-117">Remarks</span></span>  
 <span data-ttu-id="16989-118">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="16989-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="16989-119">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="16989-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="16989-120">Vous pouvez utiliser les [\<arguments>](arguments.md) [\<states>](states.md) éléments, et [\<states>](states.md) pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="16989-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="16989-121">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="16989-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="16989-122">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide de [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="16989-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16989-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16989-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="16989-124">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="16989-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="16989-125">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="16989-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
