---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 70f7452a22ae08d6eccd7d3644bdc8df45087ae0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423188"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Spécifie les paramètres du pool du canal pour une liaison personnalisée.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<oneWay>  
\<channelPoolSettings>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`idleTimeout`|<xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité des canaux du pool avant leur déconnexion. La valeur par défaut est 00:02:00.|  
|`leaseTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps après lequel un canal, lorsqu'il est retourné au pool, est fermé. La valeur par défaut est 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Entier positif qui spécifie le nombre maximal de canaux qui peuvent être stockés dans le pool pour chaque point de terminaison distant. La valeur par défaut est 10.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Active le routage de paquets pour une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
 Les quotas sont utilisés comme un mécanisme de stratégie pour empêcher une consommation excessive de ressources. Ils empêchent les attaques par déni de service (DOS) qui sont malveillantes ou involontaires. Utilisez cet élément lors de la définition de quotas de canal sur un canal personnalisé.  
  
 `ChannelPoolSettings` spécifie trois quotas :  
  
- Le quota `idleTimeout` est utilisé pour atténuer des attaques par déni de service (DOS) sur le serveur qui monopolise des ressources sur une longue période. Sur le client, la définition de la valeur correcte peut augmenter la fiabilité de la connexion avec le service. La valeur par défaut est basée sur une allocation habituellement modeste de ressources. Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation. Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.  
  
- Le quota `leaseTimeout` est utilisé pour l’intégration avec les programmes d’équilibrage de charge et pour l’amélioration de la fiabilité. La valeur par défaut est basée sur une allocation classique de ressources. Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation. Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.  
  
- Le quota `maxOutboundChannelsPerEndpoint` définit des limites de cache sur le serveur et le client et est utilisé pour améliorer la fiabilité. La valeur par défaut est basée $$sur une allocation habituellement modeste des ressources qui sont appropriées pour un environnement de développement et de petits scénarios d'installation. Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [Liaisons](../../../../../docs/framework/wcf/bindings.md)
- [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
