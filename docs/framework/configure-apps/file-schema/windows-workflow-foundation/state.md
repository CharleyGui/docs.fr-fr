---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 9ffe9f9f69f68b6f47cbc3a75200b2867aae2384
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947441"
---
# <a name="state"></a><span data-ttu-id="74251-101">\<state></span><span class="sxs-lookup"><span data-stu-id="74251-101">\<state></span></span>
<span data-ttu-id="74251-102">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="74251-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="74251-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="74251-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="74251-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74251-104">\<system.serviceModel></span></span>  
<span data-ttu-id="74251-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="74251-105">\<tracking></span></span>  
<span data-ttu-id="74251-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="74251-106">\<trackingProfile></span></span>  
<span data-ttu-id="74251-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="74251-107">\<workflow></span></span>  
<span data-ttu-id="74251-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="74251-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="74251-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="74251-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="74251-110">\<states></span><span class="sxs-lookup"><span data-stu-id="74251-110">\<states></span></span>  
<span data-ttu-id="74251-111">\<state></span><span class="sxs-lookup"><span data-stu-id="74251-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74251-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74251-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74251-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="74251-113">Attributes and Elements</span></span>  
 <span data-ttu-id="74251-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="74251-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74251-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="74251-115">Attributes</span></span>  
  
|<span data-ttu-id="74251-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="74251-116">Attribute</span></span>|<span data-ttu-id="74251-117">Description</span><span class="sxs-lookup"><span data-stu-id="74251-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74251-118">name</span><span class="sxs-lookup"><span data-stu-id="74251-118">name</span></span>|<span data-ttu-id="74251-119">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="74251-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74251-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="74251-120">Child Elements</span></span>  
 <span data-ttu-id="74251-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="74251-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74251-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="74251-122">Parent Elements</span></span>  
  
|<span data-ttu-id="74251-123">Élément</span><span class="sxs-lookup"><span data-stu-id="74251-123">Element</span></span>|<span data-ttu-id="74251-124">Description</span><span class="sxs-lookup"><span data-stu-id="74251-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74251-125">\<states></span><span class="sxs-lookup"><span data-stu-id="74251-125">\<states></span></span>](states.md)|<span data-ttu-id="74251-126">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="74251-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74251-127">Notes</span><span class="sxs-lookup"><span data-stu-id="74251-127">Remarks</span></span>  
 <span data-ttu-id="74251-128">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="74251-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="74251-129">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="74251-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="74251-130">État</span><span class="sxs-lookup"><span data-stu-id="74251-130">State</span></span>|<span data-ttu-id="74251-131">Description</span><span class="sxs-lookup"><span data-stu-id="74251-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="74251-132">Abandonné</span><span class="sxs-lookup"><span data-stu-id="74251-132">Aborted</span></span>|<span data-ttu-id="74251-133">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="74251-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="74251-134">Terminé</span><span class="sxs-lookup"><span data-stu-id="74251-134">Completed</span></span>|<span data-ttu-id="74251-135">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="74251-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="74251-136">Supprimé</span><span class="sxs-lookup"><span data-stu-id="74251-136">Deleted</span></span>|<span data-ttu-id="74251-137">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="74251-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="74251-138">Inactif</span><span class="sxs-lookup"><span data-stu-id="74251-138">Idle</span></span>|<span data-ttu-id="74251-139">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="74251-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="74251-140">Persistant</span><span class="sxs-lookup"><span data-stu-id="74251-140">Persisted</span></span>|<span data-ttu-id="74251-141">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="74251-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="74251-142">Repris</span><span class="sxs-lookup"><span data-stu-id="74251-142">Resumed</span></span>|<span data-ttu-id="74251-143">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="74251-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="74251-144">Démarré</span><span class="sxs-lookup"><span data-stu-id="74251-144">Started</span></span>|<span data-ttu-id="74251-145">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="74251-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="74251-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="74251-146">UnhandledException</span></span>|<span data-ttu-id="74251-147">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="74251-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="74251-148">Non chargé</span><span class="sxs-lookup"><span data-stu-id="74251-148">Unloaded</span></span>|<span data-ttu-id="74251-149">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="74251-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="74251-150">Canceled</span><span class="sxs-lookup"><span data-stu-id="74251-150">Canceled</span></span>|<span data-ttu-id="74251-151">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="74251-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="74251-152">Interrompu</span><span class="sxs-lookup"><span data-stu-id="74251-152">Suspended</span></span>|<span data-ttu-id="74251-153">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="74251-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="74251-154">Arrêté</span><span class="sxs-lookup"><span data-stu-id="74251-154">Terminated</span></span>|<span data-ttu-id="74251-155">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="74251-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="74251-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="74251-156">Unsuspended</span></span>|<span data-ttu-id="74251-157">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="74251-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74251-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="74251-158">Example</span></span>  
 <span data-ttu-id="74251-159">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="74251-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74251-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74251-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="74251-161">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="74251-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="74251-162">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="74251-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
