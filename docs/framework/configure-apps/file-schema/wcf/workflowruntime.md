---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399085"
---
# \<workflowRuntime>
<span data-ttu-id="958f4-101">Spécifie les paramètres d’une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="958f4-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="958f4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="958f4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="958f4-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="958f4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="958f4-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="958f4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="958f4-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="958f4-105">Attributes</span></span>  
  
|<span data-ttu-id="958f4-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="958f4-106">Attribute</span></span>|<span data-ttu-id="958f4-107">Description</span><span class="sxs-lookup"><span data-stu-id="958f4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="958f4-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="958f4-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="958f4-109">Valeur <xref:System.TimeSpan> facultative qui définit la durée maximale pendant laquelle une instance de workflow reste en mémoire en ayant l'état inactif avant d'être déchargée ou annulée.</span><span class="sxs-lookup"><span data-stu-id="958f4-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="958f4-110">Si le workflowruntime contient `PersistenceService` qui exécute unloadOnIdle, cet attribut est ignoré.</span><span class="sxs-lookup"><span data-stu-id="958f4-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="958f4-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="958f4-111">enablePerformanceCounters</span></span>|<span data-ttu-id="958f4-112">Valeur booléenne facultative indiquant si les compteurs de performance sont activés.</span><span class="sxs-lookup"><span data-stu-id="958f4-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="958f4-113">Les compteurs de performance fournissent des informations sur différentes statistiques concernant le workflow, mais ils entraînent une altération des performances lorsque le moteur d'exécution de workflow démarre et lorsque les instances de workflow s'exécutent.</span><span class="sxs-lookup"><span data-stu-id="958f4-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="958f4-114">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="958f4-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="958f4-115">name</span><span class="sxs-lookup"><span data-stu-id="958f4-115">name</span></span>|<span data-ttu-id="958f4-116">Chaîne contenant le nom du moteur d'exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="958f4-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="958f4-117">Ce nom est utilisé dans la sortie pour distinguer ce runtime d'autres runtime qui peuvent s'exécuter sur le système, par exemple, dans les compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="958f4-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="958f4-118">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="958f4-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="958f4-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="958f4-119">validateOnCreate</span></span>|<span data-ttu-id="958f4-120">Valeur booléenne facultative indiquant si la validation de la définition de workflow aura lieu lors de l'ouverture de WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="958f4-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="958f4-121">Si cet attribut a la valeur `true`, la validation du workflow est exécutée à chaque appel de `WorkflowServiceHost.Open`.</span><span class="sxs-lookup"><span data-stu-id="958f4-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="958f4-122">En cas d'erreurs de validation, une erreur <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> est générée.</span><span class="sxs-lookup"><span data-stu-id="958f4-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="958f4-123">Lorsque cette propriété a la valeur `false`, aucune validation de la définition du Workflow n'a lieu.</span><span class="sxs-lookup"><span data-stu-id="958f4-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="958f4-124">La valeur par défaut de cette propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="958f4-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="958f4-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="958f4-125">Child Elements</span></span>  
  
|<span data-ttu-id="958f4-126">Élément</span><span class="sxs-lookup"><span data-stu-id="958f4-126">Element</span></span>|<span data-ttu-id="958f4-127">Description</span><span class="sxs-lookup"><span data-stu-id="958f4-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="958f4-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="958f4-128">commonParameters</span></span>|<span data-ttu-id="958f4-129">Collection de paramètres communs utilisée par les services.</span><span class="sxs-lookup"><span data-stu-id="958f4-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="958f4-130">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="958f4-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="958f4-131">services</span><span class="sxs-lookup"><span data-stu-id="958f4-131">services</span></span>|<span data-ttu-id="958f4-132">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="958f4-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="958f4-133">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="958f4-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="958f4-134">Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="958f4-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="958f4-135">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="958f4-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="958f4-136">Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="958f4-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="958f4-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="958f4-137">Parent Elements</span></span>  
  
|<span data-ttu-id="958f4-138">Élément</span><span class="sxs-lookup"><span data-stu-id="958f4-138">Element</span></span>|<span data-ttu-id="958f4-139">Description</span><span class="sxs-lookup"><span data-stu-id="958f4-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="958f4-140">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="958f4-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="958f4-141">Remarques</span><span class="sxs-lookup"><span data-stu-id="958f4-141">Remarks</span></span>  
 <span data-ttu-id="958f4-142">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler le comportement d’un <xref:System.Workflow.Runtime.WorkflowRuntime> objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="958f4-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="958f4-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="958f4-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="958f4-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="958f4-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="958f4-145">[Fichiers de configuration du workflow](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="958f4-145">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
