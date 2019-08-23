---
title: <behaviors>de flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945993"
---
# <a name="behaviors-of-workflow"></a>\<comportements > du flux de travail
Cet élément contient la collection **serviceBehaviors** .  Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail. Chaque élément de comportement est identifié par son attribut de **nom** unique.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|Élément racine de tous les éléments de configuration de flux de travail.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Configuration et extension de l’exécution à l’aide de comportements](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
