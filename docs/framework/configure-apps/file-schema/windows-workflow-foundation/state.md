---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398641"
---
# <a name="state"></a><span data-ttu-id="87195-101">\<state></span><span class="sxs-lookup"><span data-stu-id="87195-101">\<state></span></span>
<span data-ttu-id="87195-102">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="87195-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="87195-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="87195-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="87195-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87195-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87195-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="87195-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="87195-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="87195-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="87195-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="87195-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="87195-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="87195-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="87195-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="87195-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="87195-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="87195-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="87195-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<États >** ](states.md)</span><span class="sxs-lookup"><span data-stu-id="87195-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="87195-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> d’État**</span><span class="sxs-lookup"><span data-stu-id="87195-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87195-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87195-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87195-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="87195-114">Attributes and Elements</span></span>  
 <span data-ttu-id="87195-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="87195-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87195-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="87195-116">Attributes</span></span>  
  
|<span data-ttu-id="87195-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="87195-117">Attribute</span></span>|<span data-ttu-id="87195-118">Description</span><span class="sxs-lookup"><span data-stu-id="87195-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87195-119">name</span><span class="sxs-lookup"><span data-stu-id="87195-119">name</span></span>|<span data-ttu-id="87195-120">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="87195-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87195-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="87195-121">Child Elements</span></span>  
 <span data-ttu-id="87195-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="87195-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87195-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="87195-123">Parent Elements</span></span>  
  
|<span data-ttu-id="87195-124">Élément</span><span class="sxs-lookup"><span data-stu-id="87195-124">Element</span></span>|<span data-ttu-id="87195-125">Description</span><span class="sxs-lookup"><span data-stu-id="87195-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87195-126">\<states></span><span class="sxs-lookup"><span data-stu-id="87195-126">\<states></span></span>](states.md)|<span data-ttu-id="87195-127">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="87195-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87195-128">Notes</span><span class="sxs-lookup"><span data-stu-id="87195-128">Remarks</span></span>  
 <span data-ttu-id="87195-129">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="87195-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="87195-130">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="87195-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="87195-131">État</span><span class="sxs-lookup"><span data-stu-id="87195-131">State</span></span>|<span data-ttu-id="87195-132">Description</span><span class="sxs-lookup"><span data-stu-id="87195-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="87195-133">Abandonné</span><span class="sxs-lookup"><span data-stu-id="87195-133">Aborted</span></span>|<span data-ttu-id="87195-134">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="87195-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="87195-135">Terminé</span><span class="sxs-lookup"><span data-stu-id="87195-135">Completed</span></span>|<span data-ttu-id="87195-136">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="87195-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="87195-137">Supprimé</span><span class="sxs-lookup"><span data-stu-id="87195-137">Deleted</span></span>|<span data-ttu-id="87195-138">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="87195-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="87195-139">Inactif</span><span class="sxs-lookup"><span data-stu-id="87195-139">Idle</span></span>|<span data-ttu-id="87195-140">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="87195-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="87195-141">Persistant</span><span class="sxs-lookup"><span data-stu-id="87195-141">Persisted</span></span>|<span data-ttu-id="87195-142">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="87195-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="87195-143">Repris</span><span class="sxs-lookup"><span data-stu-id="87195-143">Resumed</span></span>|<span data-ttu-id="87195-144">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="87195-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="87195-145">Démarré</span><span class="sxs-lookup"><span data-stu-id="87195-145">Started</span></span>|<span data-ttu-id="87195-146">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="87195-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="87195-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="87195-147">UnhandledException</span></span>|<span data-ttu-id="87195-148">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="87195-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="87195-149">Non chargé</span><span class="sxs-lookup"><span data-stu-id="87195-149">Unloaded</span></span>|<span data-ttu-id="87195-150">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="87195-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="87195-151">Canceled</span><span class="sxs-lookup"><span data-stu-id="87195-151">Canceled</span></span>|<span data-ttu-id="87195-152">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="87195-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="87195-153">Interrompu</span><span class="sxs-lookup"><span data-stu-id="87195-153">Suspended</span></span>|<span data-ttu-id="87195-154">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="87195-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="87195-155">Arrêté</span><span class="sxs-lookup"><span data-stu-id="87195-155">Terminated</span></span>|<span data-ttu-id="87195-156">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="87195-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="87195-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="87195-157">Unsuspended</span></span>|<span data-ttu-id="87195-158">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="87195-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87195-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="87195-159">Example</span></span>  
 <span data-ttu-id="87195-160">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="87195-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87195-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87195-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="87195-162">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="87195-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="87195-163">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="87195-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
