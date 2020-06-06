---
title: <state>de WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854953"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="42610-102">\<state>de WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="42610-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="42610-103">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="42610-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="42610-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="42610-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="42610-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42610-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42610-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="42610-106">Attributes and elements</span></span>

<span data-ttu-id="42610-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="42610-107">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="42610-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="42610-108">Attributes</span></span>

|<span data-ttu-id="42610-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="42610-109">Attribute</span></span>|<span data-ttu-id="42610-110">Description</span><span class="sxs-lookup"><span data-stu-id="42610-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="42610-111">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="42610-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42610-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="42610-112">Child elements</span></span>

<span data-ttu-id="42610-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="42610-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42610-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="42610-114">Parent elements</span></span>

|<span data-ttu-id="42610-115">Élément</span><span class="sxs-lookup"><span data-stu-id="42610-115">Element</span></span>|<span data-ttu-id="42610-116">Description</span><span class="sxs-lookup"><span data-stu-id="42610-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="42610-117">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="42610-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42610-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="42610-118">Remarks</span></span>  

<span data-ttu-id="42610-119">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="42610-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="42610-120">Les valeurs d’État possibles sont décrites dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="42610-120">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="42610-121">État</span><span class="sxs-lookup"><span data-stu-id="42610-121">State</span></span>|<span data-ttu-id="42610-122">Description</span><span class="sxs-lookup"><span data-stu-id="42610-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="42610-123">Abandonné</span><span class="sxs-lookup"><span data-stu-id="42610-123">Aborted</span></span>|<span data-ttu-id="42610-124">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="42610-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="42610-125">Effectué</span><span class="sxs-lookup"><span data-stu-id="42610-125">Completed</span></span>|<span data-ttu-id="42610-126">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="42610-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="42610-127">Deleted</span><span class="sxs-lookup"><span data-stu-id="42610-127">Deleted</span></span>|<span data-ttu-id="42610-128">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="42610-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="42610-129">Idle</span><span class="sxs-lookup"><span data-stu-id="42610-129">Idle</span></span>|<span data-ttu-id="42610-130">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="42610-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="42610-131">Persistant</span><span class="sxs-lookup"><span data-stu-id="42610-131">Persisted</span></span>|<span data-ttu-id="42610-132">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="42610-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="42610-133">Repris</span><span class="sxs-lookup"><span data-stu-id="42610-133">Resumed</span></span>|<span data-ttu-id="42610-134">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="42610-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="42610-135">Démarré</span><span class="sxs-lookup"><span data-stu-id="42610-135">Started</span></span>|<span data-ttu-id="42610-136">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="42610-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="42610-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="42610-137">UnhandledException</span></span>|<span data-ttu-id="42610-138">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="42610-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="42610-139">Unloaded</span><span class="sxs-lookup"><span data-stu-id="42610-139">Unloaded</span></span>|<span data-ttu-id="42610-140">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="42610-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="42610-141">Opération annulée</span><span class="sxs-lookup"><span data-stu-id="42610-141">Canceled</span></span>|<span data-ttu-id="42610-142">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="42610-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="42610-143">Interrompu</span><span class="sxs-lookup"><span data-stu-id="42610-143">Suspended</span></span>|<span data-ttu-id="42610-144">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="42610-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="42610-145">Arrêté</span><span class="sxs-lookup"><span data-stu-id="42610-145">Terminated</span></span>|<span data-ttu-id="42610-146">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="42610-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="42610-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="42610-147">Unsuspended</span></span>|<span data-ttu-id="42610-148">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="42610-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42610-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="42610-149">Example</span></span>

<span data-ttu-id="42610-150">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="42610-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="42610-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42610-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="42610-152">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="42610-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="42610-153">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="42610-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
