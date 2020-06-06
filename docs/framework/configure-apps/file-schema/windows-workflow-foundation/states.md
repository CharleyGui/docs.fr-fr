---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398621"
---
# \<states>
<span data-ttu-id="9c2c0-101">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="9c2c0-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9c2c0-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="9c2c0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c2c0-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c2c0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c2c0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9c2c0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c2c0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c2c0-106">Attributes</span></span>  
 <span data-ttu-id="9c2c0-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c2c0-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c2c0-108">Child Elements</span></span>  
  
|<span data-ttu-id="9c2c0-109">Élément</span><span class="sxs-lookup"><span data-stu-id="9c2c0-109">Element</span></span>|<span data-ttu-id="9c2c0-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c2c0-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="9c2c0-111">État faisant l'objet d'un abonnement de l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c2c0-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c2c0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9c2c0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9c2c0-113">Element</span></span>|<span data-ttu-id="9c2c0-114">Description</span><span class="sxs-lookup"><span data-stu-id="9c2c0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="9c2c0-115">Requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c2c0-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c2c0-116">Remarks</span></span>  
 <span data-ttu-id="9c2c0-117">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="9c2c0-118">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="9c2c0-119">État</span><span class="sxs-lookup"><span data-stu-id="9c2c0-119">State</span></span>|<span data-ttu-id="9c2c0-120">Description</span><span class="sxs-lookup"><span data-stu-id="9c2c0-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9c2c0-121">Abandonné</span><span class="sxs-lookup"><span data-stu-id="9c2c0-121">Aborted</span></span>|<span data-ttu-id="9c2c0-122">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9c2c0-123">Effectué</span><span class="sxs-lookup"><span data-stu-id="9c2c0-123">Completed</span></span>|<span data-ttu-id="9c2c0-124">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="9c2c0-125">Deleted</span><span class="sxs-lookup"><span data-stu-id="9c2c0-125">Deleted</span></span>|<span data-ttu-id="9c2c0-126">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="9c2c0-127">Idle</span><span class="sxs-lookup"><span data-stu-id="9c2c0-127">Idle</span></span>|<span data-ttu-id="9c2c0-128">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="9c2c0-129">Persistant</span><span class="sxs-lookup"><span data-stu-id="9c2c0-129">Persisted</span></span>|<span data-ttu-id="9c2c0-130">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="9c2c0-131">Repris</span><span class="sxs-lookup"><span data-stu-id="9c2c0-131">Resumed</span></span>|<span data-ttu-id="9c2c0-132">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="9c2c0-133">Démarré</span><span class="sxs-lookup"><span data-stu-id="9c2c0-133">Started</span></span>|<span data-ttu-id="9c2c0-134">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="9c2c0-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="9c2c0-135">UnhandledException</span></span>|<span data-ttu-id="9c2c0-136">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="9c2c0-137">Unloaded</span><span class="sxs-lookup"><span data-stu-id="9c2c0-137">Unloaded</span></span>|<span data-ttu-id="9c2c0-138">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="9c2c0-139">Opération annulée</span><span class="sxs-lookup"><span data-stu-id="9c2c0-139">Canceled</span></span>|<span data-ttu-id="9c2c0-140">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="9c2c0-141">Interrompu</span><span class="sxs-lookup"><span data-stu-id="9c2c0-141">Suspended</span></span>|<span data-ttu-id="9c2c0-142">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="9c2c0-143">Arrêté</span><span class="sxs-lookup"><span data-stu-id="9c2c0-143">Terminated</span></span>|<span data-ttu-id="9c2c0-144">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="9c2c0-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="9c2c0-145">Unsuspended</span></span>|<span data-ttu-id="9c2c0-146">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c2c0-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c2c0-147">Example</span></span>  
 <span data-ttu-id="9c2c0-148">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c2c0-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c2c0-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9c2c0-150">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="9c2c0-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9c2c0-151">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="9c2c0-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
