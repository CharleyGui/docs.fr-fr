---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151843"
---
# \<workflowIdle>
<span data-ttu-id="8b5d2-101">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="8b5d2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b5d2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b5d2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8b5d2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8b5d2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b5d2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b5d2-105">Attributes</span></span>  
  
|<span data-ttu-id="8b5d2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="8b5d2-106">Attribute</span></span>|<span data-ttu-id="8b5d2-107">Description</span><span class="sxs-lookup"><span data-stu-id="8b5d2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b5d2-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="8b5d2-108">timeToPersist</span></span>|<span data-ttu-id="8b5d2-109">Valeur Timespan qui spécifie la durée entre le moment où le flux de travail devient inactif et celui où il est rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="8b5d2-110">La valeur par défaut est TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="8b5d2-111">La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="8b5d2-112">Cet attribut s'avère utile si vous souhaitez rendre une instance de flux de travail persistante de manière plus agressive tout en conservant quand même l'instance dans la mémoire aussi longtemps que possible.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="8b5d2-113">Cet attribut est valide uniquement si sa valeur est inférieure à l’attribut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="8b5d2-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="8b5d2-114">Si elle est supérieure, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="8b5d2-115">Si cet attribut s’écoule avant la valeur spécifiée par l’attribut **TimeToUnload** , la persistance doit se terminer avant que le flux de travail ne soit déchargé.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="8b5d2-116">Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="8b5d2-117">La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="8b5d2-118">Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8b5d2-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="8b5d2-119">timeToUnload</span></span>|<span data-ttu-id="8b5d2-120">Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="8b5d2-121">La valeur par défaut est égale à 1 minute.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="8b5d2-122">Le déchargement d'un flux de travail implique qu'il soit également rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="8b5d2-123">Si cet attribut a la valeur zéro, l'instance de flux de travail est rendue persistante et immédiatement déchargée une fois que le flux de travail devient inactif.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="8b5d2-124">Affecter à cet attribut la valeur TimeSpan.MaxValue désactive l'opération de déchargement.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="8b5d2-125">Les instances de flux de travail inactives ne sont jamais déchargées.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b5d2-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b5d2-126">Child Elements</span></span>  
 <span data-ttu-id="8b5d2-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b5d2-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b5d2-128">Parent Elements</span></span>  
  
|<span data-ttu-id="8b5d2-129">Élément</span><span class="sxs-lookup"><span data-stu-id="8b5d2-129">Element</span></span>|<span data-ttu-id="8b5d2-130">Description</span><span class="sxs-lookup"><span data-stu-id="8b5d2-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b5d2-131">\<behavior>of\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8b5d2-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8b5d2-132">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="8b5d2-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b5d2-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b5d2-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
