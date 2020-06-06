---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398290"
---
# <a name="add-of-services"></a><span data-ttu-id="9be9f-102">\<add> de \<services></span><span class="sxs-lookup"><span data-stu-id="9be9f-102">\<add> of \<services></span></span>
<span data-ttu-id="9be9f-103">Spécifie les paramètres d’une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="9be9f-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="9be9f-104">Cet élément est de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9be9f-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9be9f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9be9f-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9be9f-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9be9f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9be9f-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9be9f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9be9f-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="9be9f-108">Attributes</span></span>  
  
|<span data-ttu-id="9be9f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="9be9f-109">Attribute</span></span>|<span data-ttu-id="9be9f-110">Description</span><span class="sxs-lookup"><span data-stu-id="9be9f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9be9f-111">type</span><span class="sxs-lookup"><span data-stu-id="9be9f-111">type</span></span>|<span data-ttu-id="9be9f-112">Chaîne indiquant le nom qualifié du type d'assembly correspondant au service à initialiser.</span><span class="sxs-lookup"><span data-stu-id="9be9f-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="9be9f-113">Les services spécifiés doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="9be9f-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9be9f-114">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="9be9f-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9be9f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9be9f-115">Child Elements</span></span>  
 <span data-ttu-id="9be9f-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9be9f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9be9f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9be9f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9be9f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="9be9f-118">Element</span></span>|<span data-ttu-id="9be9f-119">Description</span><span class="sxs-lookup"><span data-stu-id="9be9f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="9be9f-120">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="9be9f-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="9be9f-121">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9be9f-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="9be9f-122">Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="9be9f-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9be9f-123">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="9be9f-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9be9f-124">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="9be9f-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9be9f-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="9be9f-125">Remarks</span></span>  
 <span data-ttu-id="9be9f-126">Le service spécifié dans cet élément est initialisé par le moteur d'exécution de workflow et ajouté à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="9be9f-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9be9f-127">Par conséquent, le service spécifié doit suivre certaines règles en ce qui concerne les signatures de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="9be9f-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9be9f-128">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="9be9f-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be9f-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="9be9f-129">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="9be9f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9be9f-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="9be9f-131">[Fichiers de configuration du workflow](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9be9f-131">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
