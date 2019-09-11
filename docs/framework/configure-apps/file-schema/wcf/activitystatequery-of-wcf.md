---
title: <activityStateQuery>de WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 233bd3a2fa161222977902cc1053f964e8171173
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850488"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="0021d-102">\<> activityStateQuery de WCF</span><span class="sxs-lookup"><span data-stu-id="0021d-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="0021d-103">Représente une requête qui permet d'effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="0021d-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="0021d-104">Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="0021d-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="0021d-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="0021d-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="0021d-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="0021d-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="0021d-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0021d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="0021d-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0021d-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0021d-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="0021d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="0021d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="0021d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="0021d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="0021d-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0021d-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="0021d-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="0021d-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0021d-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0021d-116">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0021d-117">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0021d-117">Attributes and elements</span></span>  

<span data-ttu-id="0021d-118">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0021d-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0021d-119">Attributs</span><span class="sxs-lookup"><span data-stu-id="0021d-119">Attributes</span></span>  
  
|<span data-ttu-id="0021d-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="0021d-120">Attribute</span></span>|<span data-ttu-id="0021d-121">Description</span><span class="sxs-lookup"><span data-stu-id="0021d-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0021d-122">activityName</span><span class="sxs-lookup"><span data-stu-id="0021d-122">activityName</span></span>|<span data-ttu-id="0021d-123">Chaîne qui spécifie le nom de l'activité sur lequel filtrer des instances <xref:System.Activities.Tracking.ActivityStateRecord>.</span><span class="sxs-lookup"><span data-stu-id="0021d-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0021d-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0021d-124">Child elements</span></span>  
  
|<span data-ttu-id="0021d-125">Élément</span><span class="sxs-lookup"><span data-stu-id="0021d-125">Element</span></span>|<span data-ttu-id="0021d-126">Description</span><span class="sxs-lookup"><span data-stu-id="0021d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0021d-127">\<arguments></span><span class="sxs-lookup"><span data-stu-id="0021d-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="0021d-128">Collection d’arguments associés à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="0021d-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="0021d-129">\<states></span><span class="sxs-lookup"><span data-stu-id="0021d-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="0021d-130">Collection d’éléments de configuration qui contiennent les états de l’activité faisant l’objet d’un abonnement pour laquelle un enregistrement de suivi doit être émis.</span><span class="sxs-lookup"><span data-stu-id="0021d-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="0021d-131">\<states></span><span class="sxs-lookup"><span data-stu-id="0021d-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="0021d-132">Collection de variables associées à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="0021d-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0021d-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0021d-133">Parent elements</span></span>  
  
|<span data-ttu-id="0021d-134">Élément</span><span class="sxs-lookup"><span data-stu-id="0021d-134">Element</span></span>|<span data-ttu-id="0021d-135">Description</span><span class="sxs-lookup"><span data-stu-id="0021d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0021d-136">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0021d-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="0021d-137">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="0021d-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0021d-138">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="0021d-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0021d-139">Notes</span><span class="sxs-lookup"><span data-stu-id="0021d-139">Remarks</span></span>

<span data-ttu-id="0021d-140">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="0021d-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="0021d-141">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="0021d-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="0021d-142">Vous pouvez utiliser les [ \<arguments >](../windows-workflow-foundation/arguments.md), [ \<States >](../windows-workflow-foundation/states.md) et [ \<States >](../windows-workflow-foundation/states.md) Elements pour extraire une variable ou un argument d’une activité dans un Workflow. L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et des arguments lorsque `Closed` l’enregistrement de suivi de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="0021d-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="0021d-143">Les variables et les arguments peuvent être extraits uniquement avec un ActivityStateRecord et sont donc abonnés à dans un modèle de suivi à l’aide [ \<de activityStateQuery >](../windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="0021d-143">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="0021d-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0021d-144">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="0021d-145">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="0021d-145">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0021d-146">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="0021d-146">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
