---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398715"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="885d5-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="885d5-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="885d5-102">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="885d5-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="885d5-103">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="885d5-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="885d5-104">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="885d5-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="885d5-105">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="885d5-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="885d5-106">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="885d5-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="885d5-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="885d5-108">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="885d5-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="885d5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="885d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="885d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="885d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="885d5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="885d5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="885d5-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="885d5-114">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="885d5-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="885d5-115">Attributes and Elements</span></span>

<span data-ttu-id="885d5-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="885d5-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="885d5-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="885d5-117">Attributes</span></span>

|<span data-ttu-id="885d5-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="885d5-118">Attribute</span></span>|<span data-ttu-id="885d5-119">Description</span><span class="sxs-lookup"><span data-stu-id="885d5-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="885d5-120">activityName</span><span class="sxs-lookup"><span data-stu-id="885d5-120">activityName</span></span>|<span data-ttu-id="885d5-121">Chaîne qui spécifie le nom de l’activité de gestionnaire d’erreur qui a propagé l’erreur.</span><span class="sxs-lookup"><span data-stu-id="885d5-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="885d5-122">La valeur par défaut est \*, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="885d5-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="885d5-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="885d5-123">faultHandlerActivityName</span></span>|<span data-ttu-id="885d5-124">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="885d5-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="885d5-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="885d5-125">Child Elements</span></span>

<span data-ttu-id="885d5-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="885d5-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="885d5-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="885d5-127">Parent Elements</span></span>

|<span data-ttu-id="885d5-128">Élément</span><span class="sxs-lookup"><span data-stu-id="885d5-128">Element</span></span>|<span data-ttu-id="885d5-129">Description</span><span class="sxs-lookup"><span data-stu-id="885d5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="885d5-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="885d5-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="885d5-131">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="885d5-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="885d5-132">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="885d5-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="885d5-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="885d5-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="885d5-134">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="885d5-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="885d5-135">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="885d5-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
