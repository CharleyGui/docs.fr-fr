---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151843"
---
# <a name="workflowidle"></a>\<workflowIdle>
Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportements>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportement>**](behavior-of-servicebehaviors-of-workflow.md)\
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
|timeToPersist|Valeur Timespan qui spécifie la durée entre le moment où le flux de travail devient inactif et celui où il est rendu persistant. La valeur par défaut est TimeSpan.MaxValue.<br /><br /> La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive. Cet attribut s'avère utile si vous souhaitez rendre une instance de flux de travail persistante de manière plus agressive tout en conservant quand même l'instance dans la mémoire aussi longtemps que possible. Cet attribut n’est valable que si sa valeur est inférieure à l’attribut **timeToUnload.** Si elle est supérieure, elle est ignorée. Si cet attribut s’écoule avant la valeur spécifiée par **l’attribut DeUnload,** la persistance doit se terminer avant que le flux de travail ne soit déchargé. Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant. La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables. Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.|  
|timeToUnload|Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail. La valeur par défaut est égale à 1 minute.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant. Si cet attribut a la valeur zéro, l'instance de flux de travail est rendue persistante et immédiatement déchargée une fois que le flux de travail devient inactif. Affecter à cet attribut la valeur TimeSpan.MaxValue désactive l'opération de déchargement. Les instances de flux de travail inactives ne sont jamais déchargées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement> de \<serviceBehaviors>](behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
