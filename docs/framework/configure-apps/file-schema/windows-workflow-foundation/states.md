---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398621"
---
# <a name="states"></a><span data-ttu-id="7383d-101">\<states></span><span class="sxs-lookup"><span data-stu-id="7383d-101">\<states></span></span>
<span data-ttu-id="7383d-102">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="7383d-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="7383d-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7383d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7383d-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7383d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7383d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7383d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7383d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="7383d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="7383d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="7383d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<États >**</span><span class="sxs-lookup"><span data-stu-id="7383d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7383d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7383d-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7383d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7383d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7383d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7383d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7383d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="7383d-115">Attributes</span></span>  
 <span data-ttu-id="7383d-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7383d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7383d-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7383d-117">Child Elements</span></span>  
  
|<span data-ttu-id="7383d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="7383d-118">Element</span></span>|<span data-ttu-id="7383d-119">Description</span><span class="sxs-lookup"><span data-stu-id="7383d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7383d-120">\<state></span><span class="sxs-lookup"><span data-stu-id="7383d-120">\<state></span></span>](states.md)|<span data-ttu-id="7383d-121">État faisant l'objet d'un abonnement de l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="7383d-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7383d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7383d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7383d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="7383d-123">Element</span></span>|<span data-ttu-id="7383d-124">Description</span><span class="sxs-lookup"><span data-stu-id="7383d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7383d-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7383d-125">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="7383d-126">Requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="7383d-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7383d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="7383d-127">Remarks</span></span>  
 <span data-ttu-id="7383d-128">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="7383d-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="7383d-129">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="7383d-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="7383d-130">État</span><span class="sxs-lookup"><span data-stu-id="7383d-130">State</span></span>|<span data-ttu-id="7383d-131">Description</span><span class="sxs-lookup"><span data-stu-id="7383d-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7383d-132">Abandonné</span><span class="sxs-lookup"><span data-stu-id="7383d-132">Aborted</span></span>|<span data-ttu-id="7383d-133">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="7383d-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="7383d-134">Terminé</span><span class="sxs-lookup"><span data-stu-id="7383d-134">Completed</span></span>|<span data-ttu-id="7383d-135">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="7383d-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="7383d-136">Supprimé</span><span class="sxs-lookup"><span data-stu-id="7383d-136">Deleted</span></span>|<span data-ttu-id="7383d-137">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="7383d-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="7383d-138">Inactif</span><span class="sxs-lookup"><span data-stu-id="7383d-138">Idle</span></span>|<span data-ttu-id="7383d-139">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="7383d-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="7383d-140">Persistant</span><span class="sxs-lookup"><span data-stu-id="7383d-140">Persisted</span></span>|<span data-ttu-id="7383d-141">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="7383d-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="7383d-142">Repris</span><span class="sxs-lookup"><span data-stu-id="7383d-142">Resumed</span></span>|<span data-ttu-id="7383d-143">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="7383d-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="7383d-144">Démarré</span><span class="sxs-lookup"><span data-stu-id="7383d-144">Started</span></span>|<span data-ttu-id="7383d-145">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="7383d-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="7383d-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="7383d-146">UnhandledException</span></span>|<span data-ttu-id="7383d-147">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="7383d-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="7383d-148">Non chargé</span><span class="sxs-lookup"><span data-stu-id="7383d-148">Unloaded</span></span>|<span data-ttu-id="7383d-149">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="7383d-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="7383d-150">Canceled</span><span class="sxs-lookup"><span data-stu-id="7383d-150">Canceled</span></span>|<span data-ttu-id="7383d-151">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="7383d-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="7383d-152">Interrompu</span><span class="sxs-lookup"><span data-stu-id="7383d-152">Suspended</span></span>|<span data-ttu-id="7383d-153">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="7383d-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="7383d-154">Arrêté</span><span class="sxs-lookup"><span data-stu-id="7383d-154">Terminated</span></span>|<span data-ttu-id="7383d-155">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="7383d-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="7383d-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="7383d-156">Unsuspended</span></span>|<span data-ttu-id="7383d-157">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="7383d-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7383d-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="7383d-158">Example</span></span>  
 <span data-ttu-id="7383d-159">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="7383d-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7383d-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7383d-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7383d-161">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="7383d-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7383d-162">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="7383d-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
