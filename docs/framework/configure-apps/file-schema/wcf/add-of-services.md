---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 38dec132626b97accacea1b7007d914edcab0abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926660"
---
# <a name="add-of-services"></a><span data-ttu-id="a142d-102">\<Ajouter > de \<services ></span><span class="sxs-lookup"><span data-stu-id="a142d-102">\<add> of \<services></span></span>
<span data-ttu-id="a142d-103">Spécifie les paramètres d’une <xref:System.Workflow.Runtime.WorkflowRuntime> instance de pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="a142d-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="a142d-104">Cet élément est de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a142d-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="a142d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a142d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a142d-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a142d-106">\<behaviors></span></span>  
<span data-ttu-id="a142d-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a142d-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="a142d-108">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="a142d-108">\<behavior></span></span>  
<span data-ttu-id="a142d-109">\<services></span><span class="sxs-lookup"><span data-stu-id="a142d-109">\<services></span></span>  
<span data-ttu-id="a142d-110">\<add></span><span class="sxs-lookup"><span data-stu-id="a142d-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a142d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a142d-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a142d-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a142d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a142d-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a142d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a142d-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="a142d-114">Attributes</span></span>  
  
|<span data-ttu-id="a142d-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="a142d-115">Attribute</span></span>|<span data-ttu-id="a142d-116">Description</span><span class="sxs-lookup"><span data-stu-id="a142d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a142d-117">type</span><span class="sxs-lookup"><span data-stu-id="a142d-117">type</span></span>|<span data-ttu-id="a142d-118">Chaîne indiquant le nom qualifié du type d'assembly correspondant au service à initialiser.</span><span class="sxs-lookup"><span data-stu-id="a142d-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="a142d-119">Les services spécifiés doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="a142d-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a142d-120">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a142d-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a142d-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a142d-121">Child Elements</span></span>  
 <span data-ttu-id="a142d-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a142d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a142d-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a142d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a142d-124">Élément</span><span class="sxs-lookup"><span data-stu-id="a142d-124">Element</span></span>|<span data-ttu-id="a142d-125">Description</span><span class="sxs-lookup"><span data-stu-id="a142d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a142d-126">\<services></span><span class="sxs-lookup"><span data-stu-id="a142d-126">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="a142d-127">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="a142d-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="a142d-128">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a142d-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="a142d-129">Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="a142d-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="a142d-130">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="a142d-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a142d-131">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a142d-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a142d-132">Notes</span><span class="sxs-lookup"><span data-stu-id="a142d-132">Remarks</span></span>  
 <span data-ttu-id="a142d-133">Le service spécifié dans cet élément est initialisé par le moteur d'exécution de workflow et ajouté à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="a142d-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="a142d-134">Par conséquent, le service spécifié doit suivre certaines règles en ce qui concerne les signatures de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="a142d-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a142d-135">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a142d-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a142d-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="a142d-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a142d-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a142d-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="a142d-138">[Fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a142d-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
