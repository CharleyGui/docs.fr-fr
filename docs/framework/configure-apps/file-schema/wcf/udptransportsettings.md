---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: ed59a139ac21e7cfb4400d17f1fc6a0fa3096641
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183674"
---
# \<udpTransportSettings>

Cet élément de configuration expose les paramètres de transport UDP pour [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Entier qui spécifie le nombre maximal de hachages de messages utilisés par le transport pour l'identification des messages dupliqués.  La détection des doublons est effectuée au niveau de TransportManager. Si cette propriété a la valeur 0, la détection des doublons est désactivée.<br /><br /> Cet attribut permet aux administrateurs système ou aux développeurs de désactiver les algorithmes de détection des messages dupliqués. Cela peut s'avérer utile si vous souhaitez implémenter votre propre algorithme de détection de doublons.<br /><br /> La valeur par défaut est 4112.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale des pools de mémoires tampons utilisés par le transport.|  
|maxMulticastRetransmitCount|Entier qui spécifie le nombre maximal de retransmissions du message (en plus du premier envoi).<br /><br /> La valeur par défaut est 2.|  
|maxPendingMessageCount|Entier qui spécifie le nombre maximal de messages reçus qui n'ont pas encore été supprimés dans InputQueue pour une instance de canal individuelle.  Si InputQueue a atteint sa limite du nombre de messages en attente, le message est supprimé.<br /><br /> La valeur par défaut est 32.|  
|maxReceivedMessageSize|Entier qui spécifie la taille maximale d'un message pouvant être traité par la liaison.<br /><br /> La valeur par défaut est 65507.|  
|maxUnicastRetransmitCount|Entier qui spécifie le nombre maximal de retransmissions du message (en plus du premier envoi).  Si le message est envoyé à une adresse unicast et qu'un message de réponse est reçu avec un en-tête RelatesTo correspondant, la retransmission peut se terminer de manière précoce (avant le nombre de retransmissions configuré).<br /><br /> La valeur par défaut est 1.|  
|multicastInterfaceId|Chaîne qui identifie de manière unique la carte réseau à utiliser lors de l'envoi et de la réception du trafic multidiffusion sur des ordinateurs multirésidents. Au moment de l'exécution, le transport utilise cette valeur d'attribut pour rechercher l'index d'interface, qui permet ensuite de définir les options de socket `IP_MULTICAST_IF` et `IPV6_MULTICAST_IF`.  Le même index d'interface est utilisé pour rejoindre un groupe de multidiffusion (le cas échéant).<br /><br /> La valeur par défaut est `null`.|  
|socketReceiveBufferSize|Entier qui spécifie la taille du tampon de réception pour le socket WinSock sous-jacent.<br /><br /> Tout utilisateur d’un canal de réception peut se servir de cet attribut sur la liaison pour contrôler le comportement du système lorsqu’il reçoit des données.  Par exemple, si une application consomme des messages WCF entrants au seuil maximal, l'utilisation d'une valeur supérieure pour cet attribut permettrait aux messages de s'empiler dans la mémoire tampon Winsock en attendant que l'application puisse les traiter.  L’utilisation d’une valeur inférieure dans la même situation provoquerait le dépôt des messages. Cet attribut expose l’option de socket WinSock sous-jacente `SO_RCVBUF` . Cette valeur d’attribut doit être au moins égale à la taille de `maxReceivedMessageSize` .   Si vous affectez une valeur inférieure à `maxReceivedMessageSize` , une exception d’exécution est générée.<br /><br /> La valeur par défaut est 65536.|  
|timeToLive|Entier qui spécifie le nombre de tronçons de segments réseau pouvant être traversés par un paquet multidiffusion.  Cette propriété expose la fonctionnalité associée aux options de socket `IP_MULTICAST_TTL` et `IP_TTL`.<br /><br /> La valeur par défaut est 1.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|Point de terminaison standard qui a un contrat de découverte fixe et une liaison de transport UDP.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
