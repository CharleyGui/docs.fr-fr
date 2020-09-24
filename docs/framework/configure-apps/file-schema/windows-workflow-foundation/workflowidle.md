---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 790e852eb515e19afc324f6e1c25db81ed22999c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148670"
---
# \<workflowIdle>

Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|timeToPersist|Valeur Timespan qui spécifie la durée entre le moment où le flux de travail devient inactif et celui où il est rendu persistant. La valeur par défaut est TimeSpan.MaxValue.<br /><br /> La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive. Cet attribut s'avère utile si vous souhaitez rendre une instance de flux de travail persistante de manière plus agressive tout en conservant quand même l'instance dans la mémoire aussi longtemps que possible. Cet attribut est valide uniquement si sa valeur est inférieure à l’attribut **TimeToUnload** . Si elle est supérieure, elle est ignorée. Si cet attribut s’écoule avant la valeur spécifiée par l’attribut **TimeToUnload** , la persistance doit se terminer avant que le flux de travail ne soit déchargé. Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant. La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables. Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.|  
|timeToUnload|Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail. La valeur par défaut est égale à 1 minute.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant. Si cet attribut a la valeur zéro, l'instance de flux de travail est rendue persistante et immédiatement déchargée une fois que le flux de travail devient inactif. Affecter à cet attribut la valeur TimeSpan.MaxValue désactive l'opération de déchargement. Les instances de flux de travail inactives ne sont jamais déchargées.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior> of \<serviceBehaviors>](behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
