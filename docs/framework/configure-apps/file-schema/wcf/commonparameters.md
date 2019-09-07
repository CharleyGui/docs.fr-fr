---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 6f187e9cdcabc358ee69d65e392bc59aa38e52ca
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398176"
---
# <a name="commonparameters"></a>\<commonParameters>
Représente une collection de paramètres utilisés globalement dans plusieurs services. Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowRuntime**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Paramètres_courants**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|Ajoute à la collection une paire nom-valeur de paramètres communs utilisés par les services.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|Spécifie les paramètres d’une <xref:System.Workflow.Runtime.WorkflowRuntime> instance de pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).|  
  
## <a name="remarks"></a>Notes  
 L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
> [!NOTE]
> Le service de suivi SQL n'utilise pas toujours la valeur `ConnectionString` si elle est spécifiée dans la section `<commonParameters>`. En effet, certaines de ses opérations, comme la récupération de la propriété `StateMachineWorkflowInstance.StateHistory`, peuvent échouer. Pour résoudre ce problème, spécifiez l'attribut `ConnectionString` dans la section de configuration pour le fournisseur de suivi, comme indiqué dans l'exemple suivant.  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :  
  
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
  
 Notez que le `EnableRetries` paramètre peut être défini à un niveau global (comme indiqué dans la section *paramètres_courants* ) ou pour des services individuels qui prennent `EnableRetries` en charge (comme indiqué dans la section *services* ).  
  
 L'exemple de code suivant indique comment modifier les paramètres communs par programme.  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler <xref:System.Workflow.Runtime.WorkflowRuntime> le comportement d’un objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Exemples  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Fichiers de configuration de flux de travail](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<add>](add-of-commonparameters.md)
