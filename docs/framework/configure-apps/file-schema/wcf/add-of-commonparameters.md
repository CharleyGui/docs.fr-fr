---
title: <add> de <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400668"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="1db58-102">\<Ajouter > de \<la > paramètres_courants</span><span class="sxs-lookup"><span data-stu-id="1db58-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="1db58-103">Spécifie une paire nom-valeur de paramètres utilisés globalement dans plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="1db58-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="1db58-104">Ce paramètre inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="1db58-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="1db58-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1db58-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1db58-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1db58-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="1db58-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="1db58-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="1db58-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Paramètres_courants**](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="1db58-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="1db58-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="1db58-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db58-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db58-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db58-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1db58-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1db58-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1db58-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db58-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="1db58-116">Attributes</span></span>  
  
|<span data-ttu-id="1db58-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="1db58-117">Attribute</span></span>|<span data-ttu-id="1db58-118">Description</span><span class="sxs-lookup"><span data-stu-id="1db58-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1db58-119">name</span><span class="sxs-lookup"><span data-stu-id="1db58-119">name</span></span>|<span data-ttu-id="1db58-120">Nom du paramètre spécifié pour un service.</span><span class="sxs-lookup"><span data-stu-id="1db58-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="1db58-121">value</span><span class="sxs-lookup"><span data-stu-id="1db58-121">value</span></span>|<span data-ttu-id="1db58-122">Valeur du paramètre spécifié pour un service.</span><span class="sxs-lookup"><span data-stu-id="1db58-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1db58-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1db58-123">Child Elements</span></span>  
 <span data-ttu-id="1db58-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1db58-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1db58-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1db58-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1db58-126">Élément</span><span class="sxs-lookup"><span data-stu-id="1db58-126">Element</span></span>|<span data-ttu-id="1db58-127">Description</span><span class="sxs-lookup"><span data-stu-id="1db58-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1db58-128">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="1db58-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="1db58-129">Collection de paramètres communs utilisée par les services.</span><span class="sxs-lookup"><span data-stu-id="1db58-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="1db58-130">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="1db58-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db58-131">Notes</span><span class="sxs-lookup"><span data-stu-id="1db58-131">Remarks</span></span>  
 <span data-ttu-id="1db58-132">L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="1db58-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="1db58-133">Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1db58-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="1db58-134">Notez que le `EnableRetries` paramètre peut être défini à un niveau global (comme indiqué dans la section *paramètres_courants* ) ou pour des services individuels qui prennent `EnableRetries` en charge (comme indiqué dans la section *services* ).</span><span class="sxs-lookup"><span data-stu-id="1db58-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="1db58-135">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler <xref:System.Workflow.Runtime.WorkflowRuntime> le comportement d’un objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1db58-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db58-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="1db58-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="1db58-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1db58-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="1db58-138">[Fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1db58-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="1db58-139">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="1db58-139">\<commonParameters></span></span>](commonparameters.md)
