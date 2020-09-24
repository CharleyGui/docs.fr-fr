---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 6d4302e1840f58e2daad855942493cc96b7d5e34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158667"
---
# \<tcpTransport>

Définit un transport TCP qui peut être utilisé par un canal pour transférer des messages pour une liaison personnalisée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
              connectionBufferSize="Integer"
              hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
              listenBacklog="Integer"
              manualAddressing="Boolean"
              maxBufferPoolSize="Integer"
              maxBufferSize="Integer"
              maxOutputDelay="TimeSpan"
              maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              maxReceivedMessageSize="Integer"
              portSharingEnabled="Boolean"
              teredoEnabled="Boolean"
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|channelInitializationTimeout|Obtient ou définit la limite de temps pour initialiser un canal à accepter.  Durée maximale de l'état d'initialisation du canal avant sa déconnexion (en secondes). Ce quota comprend le temps qu’une connexion TCP peut effectuer pour s’authentifier à l’aide du protocole de tramage de message .NET. Un client doit envoyer des données initiales avant que le serveur dispose de suffisamment d'informations pour exécuter l'authentification. La valeur par défaut est 30 secondes.|  
|connectionBufferSize|Obtient ou définit la taille de la mémoire tampon utilisée pour transmettre un bloc du message sérialisé sur le câble depuis le client ou le service.|  
|hostNameComparisonMode|Obtient ou définit une valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.|  
|listenBacklog|Nombre maximal de demandes de connexion en file d'attente pouvant être en attente pour un service Web. L'attribut `connectionLeaseTimeout` limite la durée d'attente d'un client pour être connecté avant de lever une exception de connexion. Il s'agit d'une propriété de niveau socket qui contrôle le nombre maximal de demandes de connexion en file d'attente qui peuvent être en attente pour un service Web. Lorsque ListenBacklog est trop faible, WCF cesse d’accepter les requêtes et, par conséquent, abandonne les nouvelles connexions jusqu’à ce que le serveur accuse réception de certaines des connexions mises en file d’attente existantes. La valeur par défaut est 16 * nombre de processeurs.|  
|manualAddressing|Obtient ou définit une valeur qui indique si l'adressage manuel du message est requis.|  
|maxBufferPoolSize|Obtient ou définit la taille maximale des pools de mémoires tampons utilisés par le transport.|  
|maxBufferSize|Obtient ou définit la taille maximale de la mémoire tampon à utiliser. Pour les messages diffusés en continu, cette valeur doit être au moins égale à la taille maximale possible des en-têtes de message, qui sont lus en mode mémoire tampon.|  
|maxOutputDelay|Obtient ou définit la durée maximale pendant laquelle un bloc d'un message ou un message complet peut être conservé dans la mémoire tampon avant d'être expédié.|  
|maxPendingAccepts|Obtient ou définit le nombre maximal d'opérations d'acception asynchrones en attente qui sont disponibles pour traiter les connexions entrantes au service.|  
|maxPendingConnections|Obtient ou définit le nombre maximal de connexions en attente de distribution sur le service.|  
|maxReceivedMessageSize|Obtient et définit la taille de message maximale autorisée qui peut être reçue.|  
|portSharingEnabled|Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion. Si la valeur affectée est `false`, chaque liaison utilisera son propre port exclusif. Par défaut, il s’agit de `false`.<br /><br /> Ce paramètre ne concerne que les services. Les clients ne sont pas affectés.<br /><br /> L'utilisation de ce paramètre requiert l'activation du service de partage de port TCP de Windows Communication Foundation (WCF) en modifiant son type de démarrage sur Manuel ou Automatique|  
|teredoEnabled|Valeur booléenne qui spécifie si Teredo (technologie d'adressage de clients placés derrière des pare-feu) est activé. Par défaut, il s’agit de `false`.<br /><br /> Cette propriété active Teredo pour le socket TCP sous-jacent. Pour plus d’informations, voir [vue d’ensemble de Teredo](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).<br /><br /> Cette propriété s’applique uniquement à Windows XP SP2 et Windows Server 2003. Windows Vista possède une option de configuration au niveau de l’ordinateur pour Teredo. par conséquent, lors de l’exécution de Vista, cette propriété est ignorée. Pour que Teredo fonctionne, la pile Microsoft IPv6 doit être installée et configurée correctement sur les ordinateurs clients et de service.|  
|transferMode|Obtient ou définit une valeur qui indique si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.|  
|connectionPoolSettings|Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  

 Ce transport utilise des URI au format "net.tcp://nom_hôte:port/chemin". Les autres composants URI sont facultatifs.  
  
 L'élément `tcpTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport TCP. Ce transport est optimisé pour les communications entre WCF et WCF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transports](../../../wcf/feature-details/transports.md)
- [Choix d'un transport](../../../wcf/feature-details/choosing-a-transport.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
