---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 0b00780dedc15fe90163145f23c57f62369c401f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198741"
---
# \<tracking>

<span data-ttu-id="bad5f-101">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="bad5f-102">Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflows](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi pour un workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="bad5f-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="bad5f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bad5f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bad5f-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bad5f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bad5f-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bad5f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bad5f-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="bad5f-106">Attributes</span></span>  

 <span data-ttu-id="bad5f-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bad5f-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bad5f-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bad5f-108">Child Elements</span></span>  
  
|<span data-ttu-id="bad5f-109">Élément</span><span class="sxs-lookup"><span data-stu-id="bad5f-109">Element</span></span>|<span data-ttu-id="bad5f-110">Description</span><span class="sxs-lookup"><span data-stu-id="bad5f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="bad5f-111">Collection d'éléments de configuration qui définissent des participants qui s'abonnent à des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="bad5f-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="bad5f-112">Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi (par exemple, ils peuvent choisir d'écrire dans un fichier).</span><span class="sxs-lookup"><span data-stu-id="bad5f-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="bad5f-113">Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bad5f-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bad5f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bad5f-115">Élément</span><span class="sxs-lookup"><span data-stu-id="bad5f-115">Element</span></span>|<span data-ttu-id="bad5f-116">Description</span><span class="sxs-lookup"><span data-stu-id="bad5f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bad5f-117">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bad5f-117">system.ServiceModel</span></span>|<span data-ttu-id="bad5f-118">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad5f-119">Notes</span><span class="sxs-lookup"><span data-stu-id="bad5f-119">Remarks</span></span>  

 <span data-ttu-id="bad5f-120">Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="bad5f-121">L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="bad5f-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="bad5f-122">Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="bad5f-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="bad5f-123">Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="bad5f-124">Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="bad5f-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="bad5f-125">En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bad5f-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad5f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bad5f-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="bad5f-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="bad5f-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
