---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947157"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="00ec7-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="00ec7-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="00ec7-102">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="00ec7-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="00ec7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="00ec7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="00ec7-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="00ec7-104">\<behaviors></span></span>  
<span data-ttu-id="00ec7-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="00ec7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="00ec7-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="00ec7-106">\<behavior></span></span>  
<span data-ttu-id="00ec7-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="00ec7-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ec7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00ec7-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00ec7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="00ec7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00ec7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="00ec7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00ec7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="00ec7-111">Attributes</span></span>  
  
|<span data-ttu-id="00ec7-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="00ec7-112">Attribute</span></span>|<span data-ttu-id="00ec7-113">Description</span><span class="sxs-lookup"><span data-stu-id="00ec7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00ec7-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="00ec7-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="00ec7-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00ec7-115">Child Elements</span></span>  
 <span data-ttu-id="00ec7-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="00ec7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00ec7-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00ec7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="00ec7-118">Élément</span><span class="sxs-lookup"><span data-stu-id="00ec7-118">Element</span></span>|<span data-ttu-id="00ec7-119">Description</span><span class="sxs-lookup"><span data-stu-id="00ec7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00ec7-120">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="00ec7-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="00ec7-121">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="00ec7-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00ec7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00ec7-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
