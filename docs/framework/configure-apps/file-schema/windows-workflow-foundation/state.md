---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 169fa900b5be9a9577818b68b540184afd4a6681
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169724"
---
# \<state>

<span data-ttu-id="de135-101">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="de135-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="de135-102">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="de135-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="de135-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de135-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de135-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de135-104">Attributes and Elements</span></span>  

 <span data-ttu-id="de135-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de135-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de135-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="de135-106">Attributes</span></span>  
  
|<span data-ttu-id="de135-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="de135-107">Attribute</span></span>|<span data-ttu-id="de135-108">Description</span><span class="sxs-lookup"><span data-stu-id="de135-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de135-109">name</span><span class="sxs-lookup"><span data-stu-id="de135-109">name</span></span>|<span data-ttu-id="de135-110">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="de135-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de135-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de135-111">Child Elements</span></span>  

 <span data-ttu-id="de135-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="de135-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de135-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de135-113">Parent Elements</span></span>  
  
|<span data-ttu-id="de135-114">Élément</span><span class="sxs-lookup"><span data-stu-id="de135-114">Element</span></span>|<span data-ttu-id="de135-115">Description</span><span class="sxs-lookup"><span data-stu-id="de135-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="de135-116">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="de135-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de135-117">Notes</span><span class="sxs-lookup"><span data-stu-id="de135-117">Remarks</span></span>  

 <span data-ttu-id="de135-118">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="de135-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="de135-119">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="de135-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="de135-120">État</span><span class="sxs-lookup"><span data-stu-id="de135-120">State</span></span>|<span data-ttu-id="de135-121">Description</span><span class="sxs-lookup"><span data-stu-id="de135-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de135-122">Abandonné</span><span class="sxs-lookup"><span data-stu-id="de135-122">Aborted</span></span>|<span data-ttu-id="de135-123">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="de135-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="de135-124">Effectué</span><span class="sxs-lookup"><span data-stu-id="de135-124">Completed</span></span>|<span data-ttu-id="de135-125">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="de135-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="de135-126">Deleted</span><span class="sxs-lookup"><span data-stu-id="de135-126">Deleted</span></span>|<span data-ttu-id="de135-127">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="de135-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="de135-128">Idle</span><span class="sxs-lookup"><span data-stu-id="de135-128">Idle</span></span>|<span data-ttu-id="de135-129">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="de135-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="de135-130">Persistant</span><span class="sxs-lookup"><span data-stu-id="de135-130">Persisted</span></span>|<span data-ttu-id="de135-131">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="de135-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="de135-132">Repris</span><span class="sxs-lookup"><span data-stu-id="de135-132">Resumed</span></span>|<span data-ttu-id="de135-133">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="de135-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="de135-134">Démarré</span><span class="sxs-lookup"><span data-stu-id="de135-134">Started</span></span>|<span data-ttu-id="de135-135">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="de135-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="de135-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="de135-136">UnhandledException</span></span>|<span data-ttu-id="de135-137">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="de135-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="de135-138">Unloaded</span><span class="sxs-lookup"><span data-stu-id="de135-138">Unloaded</span></span>|<span data-ttu-id="de135-139">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="de135-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="de135-140">Opération annulée</span><span class="sxs-lookup"><span data-stu-id="de135-140">Canceled</span></span>|<span data-ttu-id="de135-141">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="de135-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="de135-142">Interrompu</span><span class="sxs-lookup"><span data-stu-id="de135-142">Suspended</span></span>|<span data-ttu-id="de135-143">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="de135-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="de135-144">Terminé</span><span class="sxs-lookup"><span data-stu-id="de135-144">Terminated</span></span>|<span data-ttu-id="de135-145">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="de135-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="de135-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="de135-146">Unsuspended</span></span>|<span data-ttu-id="de135-147">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="de135-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de135-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="de135-148">Example</span></span>  

 <span data-ttu-id="de135-149">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="de135-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de135-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de135-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="de135-151">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="de135-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de135-152">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="de135-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
