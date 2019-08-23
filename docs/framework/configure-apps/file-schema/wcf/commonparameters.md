---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a92a81062e92f832be78af2bfd75270390eaac3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919495"
---
# <a name="commonparameters"></a><span data-ttu-id="efde9-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="efde9-101">\<commonParameters></span></span>
<span data-ttu-id="efde9-102">Représente une collection de paramètres utilisés globalement dans plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="efde9-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="efde9-103">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="efde9-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="efde9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="efde9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="efde9-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="efde9-105">\<behaviors></span></span>  
<span data-ttu-id="efde9-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="efde9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="efde9-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="efde9-107">\<behavior></span></span>  
<span data-ttu-id="efde9-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="efde9-108">\<workflowRuntime></span></span>  
<span data-ttu-id="efde9-109">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="efde9-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efde9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efde9-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efde9-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="efde9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="efde9-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="efde9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efde9-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="efde9-113">Attributes</span></span>  
 <span data-ttu-id="efde9-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="efde9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="efde9-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="efde9-115">Child Elements</span></span>  
  
|<span data-ttu-id="efde9-116">Élément</span><span class="sxs-lookup"><span data-stu-id="efde9-116">Element</span></span>|<span data-ttu-id="efde9-117">Description</span><span class="sxs-lookup"><span data-stu-id="efde9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efde9-118">\<add></span><span class="sxs-lookup"><span data-stu-id="efde9-118">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="efde9-119">Ajoute à la collection une paire nom-valeur de paramètres communs utilisés par les services.</span><span class="sxs-lookup"><span data-stu-id="efde9-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efde9-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="efde9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="efde9-121">Élément</span><span class="sxs-lookup"><span data-stu-id="efde9-121">Element</span></span>|<span data-ttu-id="efde9-122">Description</span><span class="sxs-lookup"><span data-stu-id="efde9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efde9-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="efde9-123">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="efde9-124">Spécifie les paramètres d’une <xref:System.Workflow.Runtime.WorkflowRuntime> instance de pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="efde9-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efde9-125">Notes</span><span class="sxs-lookup"><span data-stu-id="efde9-125">Remarks</span></span>  
 <span data-ttu-id="efde9-126">L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="efde9-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efde9-127">Le service de suivi SQL n'utilise pas toujours la valeur `ConnectionString` si elle est spécifiée dans la section `<commonParameters>`.</span><span class="sxs-lookup"><span data-stu-id="efde9-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="efde9-128">En effet, certaines de ses opérations, comme la récupération de la propriété `StateMachineWorkflowInstance.StateHistory`, peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="efde9-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="efde9-129">Pour résoudre ce problème, spécifiez l'attribut `ConnectionString` dans la section de configuration pour le fournisseur de suivi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="efde9-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="efde9-130">Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="efde9-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="efde9-131">Notez que le `EnableRetries` paramètre peut être défini à un niveau global (comme indiqué dans la section *paramètres_courants* ) ou pour des services individuels qui prennent `EnableRetries` en charge (comme indiqué dans la section *services* ).</span><span class="sxs-lookup"><span data-stu-id="efde9-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="efde9-132">L'exemple de code suivant indique comment modifier les paramètres communs par programme.</span><span class="sxs-lookup"><span data-stu-id="efde9-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="efde9-133">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler <xref:System.Workflow.Runtime.WorkflowRuntime> le comportement d’un objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="efde9-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="efde9-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="efde9-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="efde9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efde9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="efde9-136">[Fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="efde9-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="efde9-137">\<add></span><span class="sxs-lookup"><span data-stu-id="efde9-137">\<add></span></span>](add-of-commonparameters.md)
