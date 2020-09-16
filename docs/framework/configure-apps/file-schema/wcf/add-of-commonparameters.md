---
title: <add> de <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 8328b6d08c1b57ad7a899c8cb489e07037e5af09
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558159"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="cd1e3-102">\<add> de \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="cd1e3-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="cd1e3-103">Spécifie une paire nom-valeur de paramètres utilisés globalement dans plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="cd1e3-104">Ce paramètre inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cd1e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd1e3-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1e3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cd1e3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="cd1e3-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1e3-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="cd1e3-108">Attributes</span></span>  
  
|<span data-ttu-id="cd1e3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cd1e3-109">Attribute</span></span>|<span data-ttu-id="cd1e3-110">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd1e3-111">name</span><span class="sxs-lookup"><span data-stu-id="cd1e3-111">name</span></span>|<span data-ttu-id="cd1e3-112">Nom du paramètre spécifié pour un service.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="cd1e3-113">value</span><span class="sxs-lookup"><span data-stu-id="cd1e3-113">value</span></span>|<span data-ttu-id="cd1e3-114">Valeur du paramètre spécifié pour un service.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1e3-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cd1e3-115">Child Elements</span></span>  
 <span data-ttu-id="cd1e3-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1e3-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cd1e3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1e3-118">Élément</span><span class="sxs-lookup"><span data-stu-id="cd1e3-118">Element</span></span>|<span data-ttu-id="cd1e3-119">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="cd1e3-120">Collection de paramètres communs utilisée par les services.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="cd1e3-121">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd1e3-122">Notes</span><span class="sxs-lookup"><span data-stu-id="cd1e3-122">Remarks</span></span>  
 <span data-ttu-id="cd1e3-123">L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="cd1e3-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="cd1e3-124">Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cd1e3-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="cd1e3-125">Notez que le `EnableRetries` paramètre peut être défini à un niveau global (comme indiqué dans la section *paramètres_courants* ) ou pour des services individuels qui prennent en charge `EnableRetries` (comme indiqué dans la section *services* ).</span><span class="sxs-lookup"><span data-stu-id="cd1e3-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="cd1e3-126">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler le comportement d’un <xref:System.Workflow.Runtime.WorkflowRuntime> objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="cd1e3-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1e3-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd1e3-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="cd1e3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd1e3-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="cd1e3-129">[Fichiers de configuration du workflow](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cd1e3-129">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
