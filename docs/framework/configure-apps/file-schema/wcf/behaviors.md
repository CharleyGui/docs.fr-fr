---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400595"
---
# <a name="behaviors"></a>\<behaviors>
Cet élément définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services. Chaque élément de comportement est identifié par son attribut `name` unique. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<comportements >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Cette section de configuration représente tous les comportements définis pour un point de terminaison spécifique.|  
|[\<serviceBehaviors>](servicebehaviors.md)|Cette section de configuration représente tous les comportements définis pour un service spécifique.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser l’élément `<remove>` pour supprimer un comportement particulier de la collection. Pour cela, fournissez le nom du comportement à supprimer dans l'attribut `name` de l'élément `<remove>`.  Vous pouvez également utiliser l’élément `<clear>` pour vous assurer qu’une collection de comportements est vide au démarrage en supprimant tout le contenu de la collection.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Configuration et extension de l’exécution à l’aide de comportements](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Configuration des comportements clients](../../../wcf/configuring-client-behaviors.md)
- [Spécification du comportement du client au moment de l’exécution](../../../wcf/specifying-client-run-time-behavior.md)
- [Spécification du comportement du service au moment de l’exécution](../../../wcf/specifying-service-run-time-behavior.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
