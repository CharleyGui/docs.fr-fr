---
title: <workflowInstanceQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854728"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="f32eb-102">\<workflowInstanceQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="f32eb-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="f32eb-103">Représente une requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début et la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="f32eb-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f32eb-104">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f32eb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="f32eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f32eb-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f32eb-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f32eb-106">Attributes and elements</span></span>  

<span data-ttu-id="f32eb-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f32eb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f32eb-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="f32eb-108">Attributes</span></span>  

<span data-ttu-id="f32eb-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f32eb-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f32eb-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f32eb-110">Child elements</span></span>  
  
|<span data-ttu-id="f32eb-111">Élément</span><span class="sxs-lookup"><span data-stu-id="f32eb-111">Element</span></span>|<span data-ttu-id="f32eb-112">Description</span><span class="sxs-lookup"><span data-stu-id="f32eb-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f32eb-113">Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="f32eb-113">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f32eb-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f32eb-114">Parent elements</span></span>  
  
|<span data-ttu-id="f32eb-115">Élément</span><span class="sxs-lookup"><span data-stu-id="f32eb-115">Element</span></span>|<span data-ttu-id="f32eb-116">Description</span><span class="sxs-lookup"><span data-stu-id="f32eb-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="f32eb-117">Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="f32eb-117">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f32eb-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="f32eb-118">Remarks</span></span>  

<span data-ttu-id="f32eb-119">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="f32eb-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f32eb-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="f32eb-120">Example</span></span>  

<span data-ttu-id="f32eb-121">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="f32eb-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f32eb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f32eb-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f32eb-123">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f32eb-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f32eb-124">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f32eb-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
