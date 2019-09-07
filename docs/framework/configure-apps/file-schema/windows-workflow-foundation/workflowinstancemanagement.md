---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397522"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="b6fce-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="b6fce-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="b6fce-102">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="b6fce-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="b6fce-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6fce-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6fce-104">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b6fce-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b6fce-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b6fce-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b6fce-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b6fce-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b6fce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b6fce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b6fce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceManagement >**</span><span class="sxs-lookup"><span data-stu-id="b6fce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6fce-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6fce-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6fce-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6fce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6fce-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6fce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6fce-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6fce-112">Attributes</span></span>  
  
|<span data-ttu-id="b6fce-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b6fce-113">Attribute</span></span>|<span data-ttu-id="b6fce-114">Description</span><span class="sxs-lookup"><span data-stu-id="b6fce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6fce-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="b6fce-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="b6fce-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6fce-116">Child Elements</span></span>  
 <span data-ttu-id="b6fce-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6fce-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6fce-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6fce-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b6fce-119">Élément</span><span class="sxs-lookup"><span data-stu-id="b6fce-119">Element</span></span>|<span data-ttu-id="b6fce-120">Description</span><span class="sxs-lookup"><span data-stu-id="b6fce-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6fce-121">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="b6fce-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b6fce-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="b6fce-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6fce-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6fce-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
