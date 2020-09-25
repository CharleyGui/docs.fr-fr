---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 31a4d2a5a3baf3d53cf18ab6e37edfaf7acb8540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204981"
---
# <a name="add-of-services"></a><span data-ttu-id="5b25b-102">\<add> de \<services></span><span class="sxs-lookup"><span data-stu-id="5b25b-102">\<add> of \<services></span></span>

<span data-ttu-id="5b25b-103">Spécifie les paramètres d’une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="5b25b-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="5b25b-104">Cet élément est de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5b25b-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5b25b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b25b-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b25b-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5b25b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5b25b-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5b25b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b25b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="5b25b-108">Attributes</span></span>  
  
|<span data-ttu-id="5b25b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b25b-109">Attribute</span></span>|<span data-ttu-id="5b25b-110">Description</span><span class="sxs-lookup"><span data-stu-id="5b25b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b25b-111">type</span><span class="sxs-lookup"><span data-stu-id="5b25b-111">type</span></span>|<span data-ttu-id="5b25b-112">Chaîne indiquant le nom qualifié du type d'assembly correspondant au service à initialiser.</span><span class="sxs-lookup"><span data-stu-id="5b25b-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="5b25b-113">Les services spécifiés doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="5b25b-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="5b25b-114">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="5b25b-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b25b-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5b25b-115">Child Elements</span></span>  

 <span data-ttu-id="5b25b-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5b25b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b25b-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5b25b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5b25b-118">Élément</span><span class="sxs-lookup"><span data-stu-id="5b25b-118">Element</span></span>|<span data-ttu-id="5b25b-119">Description</span><span class="sxs-lookup"><span data-stu-id="5b25b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="5b25b-120">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="5b25b-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="5b25b-121">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5b25b-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="5b25b-122">Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="5b25b-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="5b25b-123">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="5b25b-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="5b25b-124">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="5b25b-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b25b-125">Notes</span><span class="sxs-lookup"><span data-stu-id="5b25b-125">Remarks</span></span>  

 <span data-ttu-id="5b25b-126">Le service spécifié dans cet élément est initialisé par le moteur d'exécution de workflow et ajouté à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="5b25b-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="5b25b-127">Par conséquent, le service spécifié doit suivre certaines règles en ce qui concerne les signatures de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="5b25b-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="5b25b-128">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="5b25b-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b25b-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b25b-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b25b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b25b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="5b25b-131">[Fichiers de configuration du workflow](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5b25b-131">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
