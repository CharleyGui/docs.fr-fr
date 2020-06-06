---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397691"
---
# \<net.tcp>
Spécifie les paramètres de configuration du service de partage de port NET.TCP, qui permet à plusieurs processus de partager le même port TCP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`listenBacklog`|Entier qui spécifie le nombre maximal de connexions en attente qui sont acceptées à partir de la connexion partagée, mais qui ne sont pas encore distribuées aux services Windows Communication Foundation (WCF). La valeur par défaut est de 10.|  
|`maxPendingAccepts`|Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage. La valeur par défaut est 2.|  
|`MaxPendingConnections`|Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application. Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation. Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions. Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota. La valeur par défaut est de 10.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes. La valeur par défaut est « 00:00:10 ».|  
|`teredoEnabled`|Valeur booléenne qui indique si le service de partage de port utilise le service Microsoft Teredo pour écouter les ports TCP pour le compte des services WCF. Par défaut, il s’agit de `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur le partage de ports, consultez [partage de port Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md). Pour comprendre comment configurer le service de partage de port, consultez [configuration du service de partage de ports net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Partage de ports Net.TCP](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [Configuration du service de partage de ports Net.TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
