---
title: <faultPropagationQuery>de WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855330"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="1ea14-102">\<faultPropagationQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="1ea14-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="1ea14-103">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="1ea14-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1ea14-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="1ea14-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="1ea14-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="1ea14-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1ea14-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1ea14-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="1ea14-107">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1ea14-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="1ea14-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ea14-108">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ea14-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1ea14-109">Attributes and elements</span></span>

<span data-ttu-id="1ea14-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1ea14-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ea14-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1ea14-111">Attributes</span></span>

|<span data-ttu-id="1ea14-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="1ea14-112">Attribute</span></span>|<span data-ttu-id="1ea14-113">Description</span><span class="sxs-lookup"><span data-stu-id="1ea14-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="1ea14-114">Chaîne qui spécifie le nom de l’activité de gestionnaire d’erreur qui a propagé l’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ea14-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="1ea14-115">La valeur par défaut est, ce qui \* indique que les enregistrements de propagation d’erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="1ea14-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="1ea14-116">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="1ea14-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1ea14-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1ea14-117">Child elements</span></span>

<span data-ttu-id="1ea14-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1ea14-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ea14-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1ea14-119">Parent elements</span></span>

|<span data-ttu-id="1ea14-120">Élément</span><span class="sxs-lookup"><span data-stu-id="1ea14-120">Element</span></span>|<span data-ttu-id="1ea14-121">Description</span><span class="sxs-lookup"><span data-stu-id="1ea14-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="1ea14-122">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="1ea14-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1ea14-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="1ea14-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1ea14-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ea14-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1ea14-125">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="1ea14-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1ea14-126">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="1ea14-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
