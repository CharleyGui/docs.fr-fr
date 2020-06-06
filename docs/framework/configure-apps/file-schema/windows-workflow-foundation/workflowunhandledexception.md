---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398566"
---
# \<workflowUnhandledException>
<span data-ttu-id="231cb-101">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="231cb-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="231cb-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="231cb-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="231cb-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="231cb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="231cb-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="231cb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="231cb-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="231cb-105">Attributes</span></span>  
  
|<span data-ttu-id="231cb-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="231cb-106">Attribute</span></span>|<span data-ttu-id="231cb-107">Description</span><span class="sxs-lookup"><span data-stu-id="231cb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="231cb-108">action</span><span class="sxs-lookup"><span data-stu-id="231cb-108">action</span></span>|<span data-ttu-id="231cb-109">Chaîne qui spécifie l'action à entreprendre lorsqu'une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="231cb-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="231cb-110">Cet attribut est de type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="231cb-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="231cb-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="231cb-111">Child Elements</span></span>  
 <span data-ttu-id="231cb-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="231cb-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="231cb-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="231cb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="231cb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="231cb-114">Element</span></span>|<span data-ttu-id="231cb-115">Description</span><span class="sxs-lookup"><span data-stu-id="231cb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="231cb-116">\<behavior>of\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="231cb-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="231cb-117">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="231cb-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="231cb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="231cb-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
