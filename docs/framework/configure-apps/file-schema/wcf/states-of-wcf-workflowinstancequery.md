---
title: <states>de WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: ef4ce4b6fa6e60ead10b196b10a7c1489e15ac25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938980"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="55447-102">\<États > de WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="55447-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="55447-103">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="55447-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="55447-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="55447-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="55447-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="55447-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="55447-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="55447-106">\<profiles></span></span>  
<span data-ttu-id="55447-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="55447-107">\<trackingProfile></span></span>  
<span data-ttu-id="55447-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="55447-108">\<workflow></span></span>  
<span data-ttu-id="55447-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="55447-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="55447-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="55447-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="55447-111">\<states></span><span class="sxs-lookup"><span data-stu-id="55447-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55447-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55447-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55447-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55447-113">Attributes and elements</span></span>

<span data-ttu-id="55447-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55447-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55447-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="55447-115">Attributes</span></span>  

<span data-ttu-id="55447-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55447-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55447-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55447-117">Child elements</span></span>
  
|<span data-ttu-id="55447-118">Élément</span><span class="sxs-lookup"><span data-stu-id="55447-118">Element</span></span>|<span data-ttu-id="55447-119">Description</span><span class="sxs-lookup"><span data-stu-id="55447-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55447-120">\<states></span><span class="sxs-lookup"><span data-stu-id="55447-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="55447-121">État faisant l'objet d'un abonnement de l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="55447-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55447-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55447-122">Parent elements</span></span>  
  
|<span data-ttu-id="55447-123">Élément</span><span class="sxs-lookup"><span data-stu-id="55447-123">Element</span></span>|<span data-ttu-id="55447-124">Description</span><span class="sxs-lookup"><span data-stu-id="55447-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55447-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="55447-125">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="55447-126">Requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="55447-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55447-127">Notes</span><span class="sxs-lookup"><span data-stu-id="55447-127">Remarks</span></span>

<span data-ttu-id="55447-128">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="55447-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="55447-129">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="55447-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="55447-130">État</span><span class="sxs-lookup"><span data-stu-id="55447-130">State</span></span>|<span data-ttu-id="55447-131">Description</span><span class="sxs-lookup"><span data-stu-id="55447-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55447-132">Abandonné</span><span class="sxs-lookup"><span data-stu-id="55447-132">Aborted</span></span>|<span data-ttu-id="55447-133">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="55447-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="55447-134">Terminé</span><span class="sxs-lookup"><span data-stu-id="55447-134">Completed</span></span>|<span data-ttu-id="55447-135">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="55447-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="55447-136">Supprimé</span><span class="sxs-lookup"><span data-stu-id="55447-136">Deleted</span></span>|<span data-ttu-id="55447-137">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="55447-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="55447-138">Inactif</span><span class="sxs-lookup"><span data-stu-id="55447-138">Idle</span></span>|<span data-ttu-id="55447-139">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="55447-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="55447-140">Persistant</span><span class="sxs-lookup"><span data-stu-id="55447-140">Persisted</span></span>|<span data-ttu-id="55447-141">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="55447-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="55447-142">Repris</span><span class="sxs-lookup"><span data-stu-id="55447-142">Resumed</span></span>|<span data-ttu-id="55447-143">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="55447-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="55447-144">Démarré</span><span class="sxs-lookup"><span data-stu-id="55447-144">Started</span></span>|<span data-ttu-id="55447-145">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="55447-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="55447-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="55447-146">UnhandledException</span></span>|<span data-ttu-id="55447-147">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="55447-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="55447-148">Non chargé</span><span class="sxs-lookup"><span data-stu-id="55447-148">Unloaded</span></span>|<span data-ttu-id="55447-149">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="55447-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="55447-150">Canceled</span><span class="sxs-lookup"><span data-stu-id="55447-150">Canceled</span></span>|<span data-ttu-id="55447-151">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="55447-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="55447-152">Interrompu</span><span class="sxs-lookup"><span data-stu-id="55447-152">Suspended</span></span>|<span data-ttu-id="55447-153">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="55447-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="55447-154">Arrêté</span><span class="sxs-lookup"><span data-stu-id="55447-154">Terminated</span></span>|<span data-ttu-id="55447-155">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="55447-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="55447-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="55447-156">Unsuspended</span></span>|<span data-ttu-id="55447-157">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="55447-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55447-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="55447-158">Example</span></span>

<span data-ttu-id="55447-159">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="55447-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="55447-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55447-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="55447-161">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="55447-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="55447-162">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="55447-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
