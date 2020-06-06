---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398715"
---
# \<faultPropagationQuery>

<span data-ttu-id="e140e-101">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e140e-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e140e-102">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e140e-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e140e-103">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e140e-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e140e-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e140e-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="e140e-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e140e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="e140e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e140e-106">Syntax</span></span>

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e140e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e140e-107">Attributes and Elements</span></span>

<span data-ttu-id="e140e-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e140e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e140e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e140e-109">Attributes</span></span>

|<span data-ttu-id="e140e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e140e-110">Attribute</span></span>|<span data-ttu-id="e140e-111">Description</span><span class="sxs-lookup"><span data-stu-id="e140e-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e140e-112">activityName</span><span class="sxs-lookup"><span data-stu-id="e140e-112">activityName</span></span>|<span data-ttu-id="e140e-113">Chaîne qui spécifie le nom de l’activité de gestionnaire d’erreur qui a propagé l’erreur.</span><span class="sxs-lookup"><span data-stu-id="e140e-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e140e-114">La valeur par défaut est \*, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="e140e-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="e140e-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="e140e-115">faultHandlerActivityName</span></span>|<span data-ttu-id="e140e-116">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="e140e-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e140e-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e140e-117">Child Elements</span></span>

<span data-ttu-id="e140e-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e140e-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e140e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e140e-119">Parent Elements</span></span>

|<span data-ttu-id="e140e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="e140e-120">Element</span></span>|<span data-ttu-id="e140e-121">Description</span><span class="sxs-lookup"><span data-stu-id="e140e-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="e140e-122">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e140e-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e140e-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e140e-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e140e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e140e-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e140e-125">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e140e-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e140e-126">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e140e-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
