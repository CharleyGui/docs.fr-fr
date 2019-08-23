---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 563ce96f61bbb39f1590ca0f43c163ea2d3d7961
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947242"
---
# <a name="variables"></a><span data-ttu-id="e7da7-101">\<variables></span><span class="sxs-lookup"><span data-stu-id="e7da7-101">\<variables></span></span>
<span data-ttu-id="e7da7-102">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="e7da7-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="e7da7-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e7da7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e7da7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e7da7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e7da7-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e7da7-105">\<tracking></span></span>  
<span data-ttu-id="e7da7-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e7da7-106">\<trackingProfile></span></span>  
<span data-ttu-id="e7da7-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e7da7-107">\<workflow></span></span>  
<span data-ttu-id="e7da7-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="e7da7-108">\<activityStateQueries></span></span>  
<span data-ttu-id="e7da7-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e7da7-109">\<activityStateQuery></span></span>  
<span data-ttu-id="e7da7-110">\<variables></span><span class="sxs-lookup"><span data-stu-id="e7da7-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7da7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7da7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7da7-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7da7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e7da7-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7da7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7da7-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7da7-114">Attributes</span></span>  
 <span data-ttu-id="e7da7-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7da7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7da7-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7da7-116">Child Elements</span></span>  
  
|<span data-ttu-id="e7da7-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e7da7-117">Element</span></span>|<span data-ttu-id="e7da7-118">Description</span><span class="sxs-lookup"><span data-stu-id="e7da7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7da7-119">\<variable></span><span class="sxs-lookup"><span data-stu-id="e7da7-119">\<variable></span></span>](variable.md)|<span data-ttu-id="e7da7-120">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="e7da7-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7da7-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7da7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e7da7-122">Élément</span><span class="sxs-lookup"><span data-stu-id="e7da7-122">Element</span></span>|<span data-ttu-id="e7da7-123">Description</span><span class="sxs-lookup"><span data-stu-id="e7da7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7da7-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e7da7-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="e7da7-125">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="e7da7-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e7da7-126">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="e7da7-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7da7-127">Notes</span><span class="sxs-lookup"><span data-stu-id="e7da7-127">Remarks</span></span>  
 <span data-ttu-id="e7da7-128">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e7da7-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e7da7-129">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="e7da7-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e7da7-130">Vous pouvez utiliser les [ \<arguments >](arguments.md), [ \<States >](states.md) et [ \<States >](states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="e7da7-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e7da7-131">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="e7da7-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e7da7-132">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e7da7-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7da7-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7da7-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e7da7-134">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e7da7-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7da7-135">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e7da7-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
