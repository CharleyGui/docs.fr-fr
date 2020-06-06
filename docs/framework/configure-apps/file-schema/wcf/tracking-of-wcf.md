---
title: <tracking>de WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399416"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="e363a-102">\<tracking>de WCF</span><span class="sxs-lookup"><span data-stu-id="e363a-102">\<tracking> of WCF</span></span>
<span data-ttu-id="e363a-103">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="e363a-104">Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflows](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi pour un workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e363a-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="e363a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e363a-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
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
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e363a-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e363a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e363a-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e363a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e363a-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e363a-108">Attributes</span></span>  
 <span data-ttu-id="e363a-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e363a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e363a-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e363a-110">Child Elements</span></span>  
  
|<span data-ttu-id="e363a-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e363a-111">Element</span></span>|<span data-ttu-id="e363a-112">Description</span><span class="sxs-lookup"><span data-stu-id="e363a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="e363a-113">Collection d'éléments de configuration qui définissent des participants qui s'abonnent à des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="e363a-113">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="e363a-114">Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi (par exemple, ils peuvent choisir d'écrire dans un fichier).</span><span class="sxs-lookup"><span data-stu-id="e363a-114">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="e363a-115">Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-115">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e363a-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e363a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e363a-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e363a-117">Element</span></span>|<span data-ttu-id="e363a-118">Description</span><span class="sxs-lookup"><span data-stu-id="e363a-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e363a-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e363a-119">system.ServiceModel</span></span>|<span data-ttu-id="e363a-120">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-120">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e363a-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="e363a-121">Remarks</span></span>  
 <span data-ttu-id="e363a-122">Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-122">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="e363a-123">L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e363a-123">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="e363a-124">Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="e363a-124">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="e363a-125">Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-125">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="e363a-126">Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="e363a-126">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="e363a-127">En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e363a-127">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e363a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e363a-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="e363a-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e363a-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
