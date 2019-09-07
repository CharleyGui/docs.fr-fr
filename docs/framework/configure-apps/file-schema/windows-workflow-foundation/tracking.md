---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 28d73bb74c4a49052589040adc26194b1300668c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397601"
---
# <a name="tracking"></a><span data-ttu-id="476c8-101">\<tracking></span><span class="sxs-lookup"><span data-stu-id="476c8-101">\<tracking></span></span>
<span data-ttu-id="476c8-102">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="476c8-103">Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflows](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi pour un workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="476c8-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="476c8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="476c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="476c8-105">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="476c8-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="476c8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<suivi des >**</span><span class="sxs-lookup"><span data-stu-id="476c8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="476c8-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="476c8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="476c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="476c8-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="476c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="476c8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="476c8-110">Attributes</span></span>  
 <span data-ttu-id="476c8-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="476c8-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="476c8-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="476c8-112">Child Elements</span></span>  
  
|<span data-ttu-id="476c8-113">Élément</span><span class="sxs-lookup"><span data-stu-id="476c8-113">Element</span></span>|<span data-ttu-id="476c8-114">Description</span><span class="sxs-lookup"><span data-stu-id="476c8-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="476c8-115">\<participants></span><span class="sxs-lookup"><span data-stu-id="476c8-115">\<participants></span></span>](participants.md)|<span data-ttu-id="476c8-116">Collection d’éléments de configuration qui définissent des participants qui s’abonnent à des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="476c8-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="476c8-117">Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi (par exemple, ils peuvent choisir d'écrire dans un fichier).</span><span class="sxs-lookup"><span data-stu-id="476c8-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="476c8-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="476c8-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="476c8-119">Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="476c8-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="476c8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="476c8-121">Élément</span><span class="sxs-lookup"><span data-stu-id="476c8-121">Element</span></span>|<span data-ttu-id="476c8-122">Description</span><span class="sxs-lookup"><span data-stu-id="476c8-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="476c8-123">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="476c8-123">system.ServiceModel</span></span>|<span data-ttu-id="476c8-124">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="476c8-125">Notes</span><span class="sxs-lookup"><span data-stu-id="476c8-125">Remarks</span></span>  
 <span data-ttu-id="476c8-126">Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="476c8-127">L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="476c8-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="476c8-128">Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="476c8-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="476c8-129">Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="476c8-130">Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="476c8-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="476c8-131">En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="476c8-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476c8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="476c8-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="476c8-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="476c8-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
