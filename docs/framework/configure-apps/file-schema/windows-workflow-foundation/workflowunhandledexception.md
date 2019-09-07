---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398566"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="9c6c3-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="9c6c3-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="9c6c3-102">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="9c6c3-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="9c6c3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c6c3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c6c3-104">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9c6c3-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9c6c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9c6c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9c6c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9c6c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9c6c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9c6c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9c6c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowUnhandledException >**</span><span class="sxs-lookup"><span data-stu-id="9c6c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6c3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c6c3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c6c3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c6c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c6c3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c6c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c6c3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c6c3-112">Attributes</span></span>  
  
|<span data-ttu-id="9c6c3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9c6c3-113">Attribute</span></span>|<span data-ttu-id="9c6c3-114">Description</span><span class="sxs-lookup"><span data-stu-id="9c6c3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c6c3-115">action</span><span class="sxs-lookup"><span data-stu-id="9c6c3-115">action</span></span>|<span data-ttu-id="9c6c3-116">Chaîne qui spécifie l'action à entreprendre lorsqu'une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="9c6c3-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="9c6c3-117">Cet attribut est de type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="9c6c3-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c6c3-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c6c3-118">Child Elements</span></span>  
 <span data-ttu-id="9c6c3-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c6c3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c6c3-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c6c3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9c6c3-121">Élément</span><span class="sxs-lookup"><span data-stu-id="9c6c3-121">Element</span></span>|<span data-ttu-id="9c6c3-122">Description</span><span class="sxs-lookup"><span data-stu-id="9c6c3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c6c3-123">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="9c6c3-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9c6c3-124">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="9c6c3-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c6c3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c6c3-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
