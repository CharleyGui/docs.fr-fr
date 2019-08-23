---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: c46d1fb9eb853e57c7ad1b97eb9a22556cdfb7d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913097"
---
# <a name="workflowunhandledexception"></a>\<workflowUnhandledException>
Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.  
  
\<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<workflowUnhandledException>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|action|Chaîne qui spécifie l'action à entreprendre lorsqu'une exception non gérée se produit. Cet attribut est de type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<> de comportement \<de la > serviceBehaviors](behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
