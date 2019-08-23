---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936275"
---
# <a name="servicediscovery"></a>\<serviceDiscovery>
Spécifie la fonctionnalité de découverte des points de terminaison de service.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<serviceDiscovery>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|Collection de points de terminaison d’annonce. Cette section permet de spécifier les points de terminaison à utiliser pour l'envoi de messages d'annonce.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Collection de points de terminaison de découverte. Cette section permet de spécifier les points de terminaison sur lesquels écouter les messages de découverte.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration rend tous les points de terminaison de ce service détectables. Vous pouvez configurer davantage les fonctionnalités de découverte de tels points de terminaison à [ \<](discoveryendpoint.md) l’aide des éléments enfants DiscoveryEndpoint > ou [ \<announcementEndpoint >](announcementendpoint.md) . Utilisez la [ \<section announcementEndpoint >](announcementendpoint.md) pour configurer les annonces en spécifiant la configuration de point de terminaison à utiliser pour envoyer les annonces de service (Online/Hello et offline/Bye). Utilisez la [ \<section DiscoveryEndpoint >](discoveryendpoint.md) pour spécifier manuellement le point de terminaison sur lequel écouter les messages de découverte.  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant spécifie que CalculatorService doit être détectable et indique éventuellement le point de terminaison d'annonce à utiliser.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
