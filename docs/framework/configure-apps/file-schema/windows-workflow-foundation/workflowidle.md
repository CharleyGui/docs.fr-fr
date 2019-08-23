---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 16a485b6d0ba2584cccd08a36506582fd3930f71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947166"
---
# <a name="workflowidle"></a><span data-ttu-id="8c73c-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="8c73c-101">\<workflowIdle></span></span>
<span data-ttu-id="8c73c-102">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="8c73c-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="8c73c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c73c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c73c-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="8c73c-104">\<behaviors></span></span>  
<span data-ttu-id="8c73c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8c73c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8c73c-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="8c73c-106">\<behavior></span></span>  
<span data-ttu-id="8c73c-107">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="8c73c-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c73c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c73c-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c73c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8c73c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8c73c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8c73c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c73c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8c73c-111">Attributes</span></span>  
  
|<span data-ttu-id="8c73c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="8c73c-112">Attribute</span></span>|<span data-ttu-id="8c73c-113">Description</span><span class="sxs-lookup"><span data-stu-id="8c73c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c73c-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="8c73c-114">timeToPersist</span></span>|<span data-ttu-id="8c73c-115">Valeur TimeSpan qui spécifie la durée entre le moment où le workflow devient inactif et celui où il est rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8c73c-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="8c73c-116">La valeur par défaut est TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="8c73c-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="8c73c-117">La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive.</span><span class="sxs-lookup"><span data-stu-id="8c73c-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="8c73c-118">Cet attribut est utile si vous souhaitez conserver une instance de workflow de manière plus agressive tout en conservant la mémoire de l’instance aussi longtemps que possible.</span><span class="sxs-lookup"><span data-stu-id="8c73c-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="8c73c-119">Cet attribut est valide uniquement si sa valeur est inférieure à l’attribut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="8c73c-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="8c73c-120">Si elle est supérieure, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="8c73c-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="8c73c-121">Si cet attribut s’écoule avant la valeur spécifiée par l’attribut **TimeToUnload** , la persistance doit se terminer avant que le flux de travail ne soit déchargé.</span><span class="sxs-lookup"><span data-stu-id="8c73c-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="8c73c-122">Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8c73c-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="8c73c-123">La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables.</span><span class="sxs-lookup"><span data-stu-id="8c73c-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="8c73c-124">Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="8c73c-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8c73c-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="8c73c-125">timeToUnload</span></span>|<span data-ttu-id="8c73c-126">Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="8c73c-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="8c73c-127">La valeur par défaut est égale à 1 minute.</span><span class="sxs-lookup"><span data-stu-id="8c73c-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="8c73c-128">Le déchargement d'un flux de travail implique qu'il soit également rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8c73c-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="8c73c-129">Si cet attribut a la valeur zéro, l’instance de workflow est persistante et déchargée immédiatement après que le flux de travail devient inactif.</span><span class="sxs-lookup"><span data-stu-id="8c73c-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="8c73c-130">L’affectation de la valeur TimeSpan. MaxValue à cet attribut désactive efficacement l’opération de déchargement.</span><span class="sxs-lookup"><span data-stu-id="8c73c-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="8c73c-131">Les instances de flux de travail inactives ne sont jamais déchargées.</span><span class="sxs-lookup"><span data-stu-id="8c73c-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c73c-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8c73c-132">Child Elements</span></span>  
 <span data-ttu-id="8c73c-133">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8c73c-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c73c-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8c73c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8c73c-135">Élément</span><span class="sxs-lookup"><span data-stu-id="8c73c-135">Element</span></span>|<span data-ttu-id="8c73c-136">Description</span><span class="sxs-lookup"><span data-stu-id="8c73c-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c73c-137">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="8c73c-137">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8c73c-138">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="8c73c-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c73c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c73c-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
