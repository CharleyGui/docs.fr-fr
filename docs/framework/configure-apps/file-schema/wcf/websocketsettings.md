---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399134"
---
# <a name="websocketsettings"></a>\<webSocketSettings>
Élément de configuration utilisé pour spécifier des paramètres WebSocket.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|createNotificationOnConnection|Spécifie si une notification est envoyée lors de la connexion.|  
|disablePayloadMasking|Spécifie si le masquage WebSocket est désactivé.|  
|keepAliveInterval|Spécifie l'intervalle de maintien de l'activité.|  
|maxPendingConnections|Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.|  
|receiveBufferSize|Spécifie la taille de la mémoire tampon de réception.|  
|sendBufferSize|Spécifie la taille de la mémoire tampon d'envoi.|  
|subProtocol|Spécifie le sous-protocole WebSocket.|  
|transportUsage|Spécifie quand utiliser WebSocket.|  
  
## <a name="transportusage-attribute"></a>Attribut transportUsage  
  
|`Value`|Description|  
|-----------|-----------------|  
|WhenDuplex|Utilisez le protocole WebSocket lorsque le contrat est en duplex.|  
|Always|Utilisez toujours le protocole WebSocket indépendamment du contrat.|  
|Never|N'utilisez jamais le protocole WebSocket.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<netHttpBinding>|Spécifie le NetHttpBinding|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l' \<élément webSocketSettings >.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
