---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 43cdec2403e8d80256279388a1adf7cf3cedbb73
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558782"
---
# \<workflowRuntime>
Spécifie les paramètres d’une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour l’hébergement de services WCF (Windows Communication Foundation basés sur le flux de travail).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|cachedInstanceExpiration|Valeur <xref:System.TimeSpan> facultative qui définit la durée maximale pendant laquelle une instance de workflow reste en mémoire en ayant l'état inactif avant d'être déchargée ou annulée. Si le workflowruntime contient `PersistenceService` qui exécute unloadOnIdle, cet attribut est ignoré.|  
|enablePerformanceCounters|Valeur booléenne facultative indiquant si les compteurs de performance sont activés. Les compteurs de performance fournissent des informations sur différentes statistiques concernant le workflow, mais ils entraînent une altération des performances lorsque le moteur d'exécution de workflow démarre et lorsque les instances de workflow s'exécutent. La valeur par défaut est `true`.|  
|name|Chaîne contenant le nom du moteur d'exécution de workflow. Ce nom est utilisé dans la sortie pour distinguer ce runtime d'autres runtime qui peuvent s'exécuter sur le système, par exemple, dans les compteurs de performance.<br /><br /> La valeur par défaut est une chaîne vide.|  
|validateOnCreate|Valeur booléenne facultative indiquant si la validation de la définition de workflow aura lieu lors de l'ouverture de WorkflowServiceHost.  Si cet attribut a la valeur `true`, la validation du workflow est exécutée à chaque appel de `WorkflowServiceHost.Open`. En cas d'erreurs de validation, une erreur <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> est générée.<br /><br /> Lorsque cette propriété a la valeur `false`, aucune validation de la définition du Workflow n'a lieu.<br /><br /> La valeur par défaut de cette propriété est `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|commonParameters|Collection de paramètres communs utilisée par les services. Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.|  
|services|Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>. Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Les services spécifiés dans la collection sont initialisés par le moteur d’exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé. Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs. Consultez la rubrique <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> (éventuellement en anglais) pour plus d'informations.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler le comportement d’un <xref:System.Workflow.Runtime.WorkflowRuntime> objet d’une application hôte Windows Workflow Foundation, consultez [fichiers de configuration de flux de travail](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Fichiers de configuration du workflow](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
