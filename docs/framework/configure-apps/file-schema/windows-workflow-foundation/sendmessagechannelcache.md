---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: ac38a43b39496bdeee59a591f7b8f5bc4dd30de0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398698"
---
# <a name="sendmessagechannelcache"></a>\<sendMessageChannelCache>
Comportement de service qui permet la personnalisation des niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux pour les flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’activités de messagerie d’envoi.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sendMessageChannelCache >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|allowUnsafeCaching|Valeur booléenne qui indique s'il faut activer la mise en cache. Si le service de flux de travail comporte des liaisons ou des comportements personnalisés, la mise en cache pourrait être non sécurisée et donc désactivée par défaut. Toutefois, si vous souhaitez activer la mise en cache, affectez la valeur **true**à cette propriété.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|Spécifie les paramètres du cache de canaux.|  
|[\<factorySettings>](factorysettings.md)|Spécifie les paramètres du cache de la fabrique de canaux.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<> de comportement \<de la > serviceBehaviors](behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Notes  
 Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service. Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.  
  
 Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte). Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance). La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.  
  
 Pour plus d’informations sur la modification des niveaux de partage de cache par défaut et des paramètres de cache pour la fabrique de canaux et le cache de canaux, consultez [modification des niveaux de partage du cache pour les activités d’envoi](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
## <a name="example"></a>Exemple  
 Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application. Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service. L’exemple suivant montre le contenu d’un fichier de configuration qui contient `MyChannelCacheBehavior` le comportement de service avec les paramètres du cache de fabrique personnalisé et du cache de canaux. Ce comportement de service est ajouté au service via l' `behaviorConfiguration` attribut.  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [Modification des niveaux de partage du cache pour les activités d’envoi](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
