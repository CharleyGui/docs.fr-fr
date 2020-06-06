---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398641"
---
# \<state>
<span data-ttu-id="8756d-101">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="8756d-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="8756d-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8756d-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="8756d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8756d-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8756d-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8756d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="8756d-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8756d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8756d-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="8756d-106">Attributes</span></span>  
  
|<span data-ttu-id="8756d-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="8756d-107">Attribute</span></span>|<span data-ttu-id="8756d-108">Description</span><span class="sxs-lookup"><span data-stu-id="8756d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8756d-109">name</span><span class="sxs-lookup"><span data-stu-id="8756d-109">name</span></span>|<span data-ttu-id="8756d-110">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="8756d-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8756d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8756d-111">Child Elements</span></span>  
 <span data-ttu-id="8756d-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8756d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8756d-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8756d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="8756d-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8756d-114">Element</span></span>|<span data-ttu-id="8756d-115">Description</span><span class="sxs-lookup"><span data-stu-id="8756d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="8756d-116">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="8756d-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8756d-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="8756d-117">Remarks</span></span>  
 <span data-ttu-id="8756d-118">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="8756d-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="8756d-119">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8756d-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="8756d-120">État</span><span class="sxs-lookup"><span data-stu-id="8756d-120">State</span></span>|<span data-ttu-id="8756d-121">Description</span><span class="sxs-lookup"><span data-stu-id="8756d-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8756d-122">Abandonné</span><span class="sxs-lookup"><span data-stu-id="8756d-122">Aborted</span></span>|<span data-ttu-id="8756d-123">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="8756d-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8756d-124">Effectué</span><span class="sxs-lookup"><span data-stu-id="8756d-124">Completed</span></span>|<span data-ttu-id="8756d-125">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="8756d-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="8756d-126">Deleted</span><span class="sxs-lookup"><span data-stu-id="8756d-126">Deleted</span></span>|<span data-ttu-id="8756d-127">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="8756d-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="8756d-128">Idle</span><span class="sxs-lookup"><span data-stu-id="8756d-128">Idle</span></span>|<span data-ttu-id="8756d-129">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="8756d-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="8756d-130">Persistant</span><span class="sxs-lookup"><span data-stu-id="8756d-130">Persisted</span></span>|<span data-ttu-id="8756d-131">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="8756d-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="8756d-132">Repris</span><span class="sxs-lookup"><span data-stu-id="8756d-132">Resumed</span></span>|<span data-ttu-id="8756d-133">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="8756d-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="8756d-134">Démarré</span><span class="sxs-lookup"><span data-stu-id="8756d-134">Started</span></span>|<span data-ttu-id="8756d-135">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="8756d-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="8756d-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="8756d-136">UnhandledException</span></span>|<span data-ttu-id="8756d-137">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="8756d-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="8756d-138">Unloaded</span><span class="sxs-lookup"><span data-stu-id="8756d-138">Unloaded</span></span>|<span data-ttu-id="8756d-139">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="8756d-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="8756d-140">Opération annulée</span><span class="sxs-lookup"><span data-stu-id="8756d-140">Canceled</span></span>|<span data-ttu-id="8756d-141">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="8756d-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="8756d-142">Interrompu</span><span class="sxs-lookup"><span data-stu-id="8756d-142">Suspended</span></span>|<span data-ttu-id="8756d-143">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="8756d-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="8756d-144">Arrêté</span><span class="sxs-lookup"><span data-stu-id="8756d-144">Terminated</span></span>|<span data-ttu-id="8756d-145">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="8756d-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="8756d-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="8756d-146">Unsuspended</span></span>|<span data-ttu-id="8756d-147">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="8756d-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8756d-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="8756d-148">Example</span></span>  
 <span data-ttu-id="8756d-149">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="8756d-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8756d-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8756d-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8756d-151">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="8756d-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8756d-152">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="8756d-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
