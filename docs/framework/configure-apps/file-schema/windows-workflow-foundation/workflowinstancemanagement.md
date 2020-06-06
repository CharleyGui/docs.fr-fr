---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397522"
---
# \<workflowInstanceManagement>
<span data-ttu-id="92493-101">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="92493-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="92493-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92493-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92493-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="92493-103">Attributes and Elements</span></span>  
 <span data-ttu-id="92493-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="92493-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92493-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="92493-105">Attributes</span></span>  
  
|<span data-ttu-id="92493-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="92493-106">Attribute</span></span>|<span data-ttu-id="92493-107">Description</span><span class="sxs-lookup"><span data-stu-id="92493-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92493-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="92493-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="92493-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="92493-109">Child Elements</span></span>  
 <span data-ttu-id="92493-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="92493-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92493-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="92493-111">Parent Elements</span></span>  
  
|<span data-ttu-id="92493-112">Élément</span><span class="sxs-lookup"><span data-stu-id="92493-112">Element</span></span>|<span data-ttu-id="92493-113">Description</span><span class="sxs-lookup"><span data-stu-id="92493-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92493-114">\<behavior>of\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="92493-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="92493-115">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="92493-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92493-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92493-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
