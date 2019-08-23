---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915219"
---
# <a name="workflowruntime"></a><span data-ttu-id="db314-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="db314-101">\<workflowRuntime></span></span>
<span data-ttu-id="db314-102">Spécifie les paramètres d’une <xref:System.Workflow.Runtime.WorkflowRuntime> instance de pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="db314-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="db314-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db314-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="db314-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="db314-104">\<behaviors></span></span>  
<span data-ttu-id="db314-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="db314-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="db314-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="db314-106">\<behavior></span></span>  
<span data-ttu-id="db314-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="db314-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db314-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db314-108">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db314-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db314-109">Attributes and Elements</span></span>  
 <span data-ttu-id="db314-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db314-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db314-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="db314-111">Attributes</span></span>  
  
|<span data-ttu-id="db314-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="db314-112">Attribute</span></span>|<span data-ttu-id="db314-113">Description</span><span class="sxs-lookup"><span data-stu-id="db314-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db314-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="db314-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="db314-115">Valeur <xref:System.TimeSpan> facultative qui définit la durée maximale pendant laquelle une instance de workflow reste en mémoire en ayant l'état inactif avant d'être déchargée ou annulée.</span><span class="sxs-lookup"><span data-stu-id="db314-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="db314-116">Si le workflowruntime contient `PersistenceService` qui exécute unloadOnIdle, cet attribut est ignoré.</span><span class="sxs-lookup"><span data-stu-id="db314-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="db314-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="db314-117">enablePerformanceCounters</span></span>|<span data-ttu-id="db314-118">Valeur booléenne facultative indiquant si les compteurs de performance sont activés.</span><span class="sxs-lookup"><span data-stu-id="db314-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="db314-119">Les compteurs de performance fournissent des informations sur différentes statistiques concernant le workflow, mais ils entraînent une altération des performances lorsque le moteur d'exécution de workflow démarre et lorsque les instances de workflow s'exécutent.</span><span class="sxs-lookup"><span data-stu-id="db314-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="db314-120">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="db314-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="db314-121">name</span><span class="sxs-lookup"><span data-stu-id="db314-121">name</span></span>|<span data-ttu-id="db314-122">Chaîne contenant le nom du moteur d'exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="db314-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="db314-123">Ce nom est utilisé dans la sortie pour distinguer ce runtime d'autres runtime qui peuvent s'exécuter sur le système, par exemple, dans les compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="db314-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="db314-124">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="db314-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="db314-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="db314-125">validateOnCreate</span></span>|<span data-ttu-id="db314-126">Valeur booléenne facultative indiquant si la validation de la définition de workflow aura lieu lors de l'ouverture de WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="db314-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="db314-127">Si cet attribut a la valeur `true`, la validation du workflow est exécutée à chaque appel de `WorkflowServiceHost.Open`.</span><span class="sxs-lookup"><span data-stu-id="db314-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="db314-128">En cas d'erreurs de validation, une erreur <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> est générée.</span><span class="sxs-lookup"><span data-stu-id="db314-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="db314-129">Lorsque cette propriété a la valeur `false`, aucune validation de la définition du Workflow n'a lieu.</span><span class="sxs-lookup"><span data-stu-id="db314-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="db314-130">La valeur par défaut de cette propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="db314-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db314-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db314-131">Child Elements</span></span>  
  
|<span data-ttu-id="db314-132">Élément</span><span class="sxs-lookup"><span data-stu-id="db314-132">Element</span></span>|<span data-ttu-id="db314-133">Description</span><span class="sxs-lookup"><span data-stu-id="db314-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db314-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="db314-134">commonParameters</span></span>|<span data-ttu-id="db314-135">Collection de paramètres communs utilisée par les services.</span><span class="sxs-lookup"><span data-stu-id="db314-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="db314-136">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="db314-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="db314-137">services</span><span class="sxs-lookup"><span data-stu-id="db314-137">services</span></span>|<span data-ttu-id="db314-138">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="db314-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="db314-139">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="db314-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="db314-140">Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="db314-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="db314-141">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="db314-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="db314-142">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="db314-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db314-143">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db314-143">Parent Elements</span></span>  
  
|<span data-ttu-id="db314-144">Élément</span><span class="sxs-lookup"><span data-stu-id="db314-144">Element</span></span>|<span data-ttu-id="db314-145">Description</span><span class="sxs-lookup"><span data-stu-id="db314-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db314-146">\<behavior></span><span class="sxs-lookup"><span data-stu-id="db314-146">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="db314-147">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="db314-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db314-148">Notes</span><span class="sxs-lookup"><span data-stu-id="db314-148">Remarks</span></span>  
 <span data-ttu-id="db314-149">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler <xref:System.Workflow.Runtime.WorkflowRuntime> le comportement d’un objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="db314-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db314-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="db314-150">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="db314-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db314-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="db314-152">[Fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="db314-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
