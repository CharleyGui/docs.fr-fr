---
title: <state>de WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854953"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="1f766-102">\<> d’état de WCF \<, workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="1f766-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="1f766-103">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="1f766-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1f766-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1f766-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f766-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f766-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="1f766-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** </span><span class="sxs-lookup"><span data-stu-id="1f766-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="1f766-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="1f766-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="1f766-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="1f766-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="1f766-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<États >** ](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="1f766-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="1f766-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> d’État**</span><span class="sxs-lookup"><span data-stu-id="1f766-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f766-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f766-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f766-116">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1f766-116">Attributes and elements</span></span>

<span data-ttu-id="1f766-117">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1f766-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="1f766-118">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f766-118">Attributes</span></span>

|<span data-ttu-id="1f766-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="1f766-119">Attribute</span></span>|<span data-ttu-id="1f766-120">Description</span><span class="sxs-lookup"><span data-stu-id="1f766-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1f766-121">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="1f766-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f766-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f766-122">Child elements</span></span>

<span data-ttu-id="1f766-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1f766-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f766-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f766-124">Parent elements</span></span>

|<span data-ttu-id="1f766-125">Élément</span><span class="sxs-lookup"><span data-stu-id="1f766-125">Element</span></span>|<span data-ttu-id="1f766-126">Description</span><span class="sxs-lookup"><span data-stu-id="1f766-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f766-127">\<states></span><span class="sxs-lookup"><span data-stu-id="1f766-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="1f766-128">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="1f766-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f766-129">Notes</span><span class="sxs-lookup"><span data-stu-id="1f766-129">Remarks</span></span>  

<span data-ttu-id="1f766-130">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="1f766-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="1f766-131">Les valeurs d’État possibles sont décrites dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="1f766-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="1f766-132">État</span><span class="sxs-lookup"><span data-stu-id="1f766-132">State</span></span>|<span data-ttu-id="1f766-133">Description</span><span class="sxs-lookup"><span data-stu-id="1f766-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f766-134">Abandonné</span><span class="sxs-lookup"><span data-stu-id="1f766-134">Aborted</span></span>|<span data-ttu-id="1f766-135">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="1f766-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1f766-136">Terminé</span><span class="sxs-lookup"><span data-stu-id="1f766-136">Completed</span></span>|<span data-ttu-id="1f766-137">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="1f766-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1f766-138">Supprimé</span><span class="sxs-lookup"><span data-stu-id="1f766-138">Deleted</span></span>|<span data-ttu-id="1f766-139">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="1f766-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1f766-140">Inactif</span><span class="sxs-lookup"><span data-stu-id="1f766-140">Idle</span></span>|<span data-ttu-id="1f766-141">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="1f766-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1f766-142">Persistant</span><span class="sxs-lookup"><span data-stu-id="1f766-142">Persisted</span></span>|<span data-ttu-id="1f766-143">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="1f766-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1f766-144">Repris</span><span class="sxs-lookup"><span data-stu-id="1f766-144">Resumed</span></span>|<span data-ttu-id="1f766-145">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="1f766-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1f766-146">Démarré</span><span class="sxs-lookup"><span data-stu-id="1f766-146">Started</span></span>|<span data-ttu-id="1f766-147">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="1f766-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1f766-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1f766-148">UnhandledException</span></span>|<span data-ttu-id="1f766-149">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="1f766-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1f766-150">Non chargé</span><span class="sxs-lookup"><span data-stu-id="1f766-150">Unloaded</span></span>|<span data-ttu-id="1f766-151">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="1f766-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1f766-152">Canceled</span><span class="sxs-lookup"><span data-stu-id="1f766-152">Canceled</span></span>|<span data-ttu-id="1f766-153">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="1f766-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1f766-154">Interrompu</span><span class="sxs-lookup"><span data-stu-id="1f766-154">Suspended</span></span>|<span data-ttu-id="1f766-155">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="1f766-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1f766-156">Arrêté</span><span class="sxs-lookup"><span data-stu-id="1f766-156">Terminated</span></span>|<span data-ttu-id="1f766-157">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="1f766-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1f766-158">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="1f766-158">Unsuspended</span></span>|<span data-ttu-id="1f766-159">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="1f766-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f766-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f766-160">Example</span></span>

<span data-ttu-id="1f766-161">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="1f766-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="1f766-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f766-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1f766-163">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="1f766-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f766-164">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="1f766-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
