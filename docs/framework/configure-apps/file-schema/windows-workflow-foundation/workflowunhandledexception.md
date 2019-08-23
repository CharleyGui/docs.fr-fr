---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: c46d1fb9eb853e57c7ad1b97eb9a22556cdfb7d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913097"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="e24f5-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="e24f5-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="e24f5-102">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="e24f5-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="e24f5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e24f5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e24f5-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="e24f5-104">\<behaviors></span></span>  
<span data-ttu-id="e24f5-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e24f5-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e24f5-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="e24f5-106">\<behavior></span></span>  
<span data-ttu-id="e24f5-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="e24f5-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24f5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24f5-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e24f5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e24f5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e24f5-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e24f5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e24f5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e24f5-111">Attributes</span></span>  
  
|<span data-ttu-id="e24f5-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="e24f5-112">Attribute</span></span>|<span data-ttu-id="e24f5-113">Description</span><span class="sxs-lookup"><span data-stu-id="e24f5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e24f5-114">action</span><span class="sxs-lookup"><span data-stu-id="e24f5-114">action</span></span>|<span data-ttu-id="e24f5-115">Chaîne qui spécifie l'action à entreprendre lorsqu'une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="e24f5-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="e24f5-116">Cet attribut est de type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="e24f5-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e24f5-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e24f5-117">Child Elements</span></span>  
 <span data-ttu-id="e24f5-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e24f5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e24f5-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e24f5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e24f5-120">Élément</span><span class="sxs-lookup"><span data-stu-id="e24f5-120">Element</span></span>|<span data-ttu-id="e24f5-121">Description</span><span class="sxs-lookup"><span data-stu-id="e24f5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e24f5-122">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="e24f5-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e24f5-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="e24f5-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e24f5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e24f5-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
