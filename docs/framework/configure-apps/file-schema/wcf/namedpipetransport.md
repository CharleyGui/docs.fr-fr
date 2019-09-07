---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e5f1d49e0e3bb5f52c5e18577d556d25539434a9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400163"
---
# <a name="namedpipetransport"></a>\<namedPipeTransport>
Définit un transport qui entraîne un canal à transférer des messages à l’aide de canaux nommés lorsqu’il est inclus dans une liaison personnalisée.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedPipeTransport >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Obtient ou définit une <xref:System.TimeSpan> valeur qui détermine la durée maximale pendant laquelle un canal peut être dans l’état d’initialisation avant d’être déconnecté.|  
|ConnectionBufferSize|Obtient ou définit la taille de la mémoire tampon utilisée pour transmettre un bloc du message sérialisé sur le câble depuis le client ou le service.|  
|hostNameComparisonMode|Obtient ou définit une valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.|  
|manualAddressing|Obtient ou définit une valeur qui indique si l'adressage manuel du message est requis.|  
|maxBufferPoolSize|Obtient ou définit la taille maximale, en octets, des pools de mémoires tampons utilisés par le transport.|  
|maxBufferSize|Obtient ou définit la taille maximale de la mémoire tampon à utiliser. Pour les messages diffusés en continu, cette valeur doit être au moins égale à la taille maximale possible des en-têtes de message, qui sont lus en mode mémoire tampon.|  
|maxOutputDelay|Obtient ou définit la durée maximale pendant laquelle un bloc d'un message ou un message complet peut être conservé dans la mémoire tampon avant d'être expédié.|  
|maxPendingAccepts|Obtient ou définit le nombre maximal de canaux qu’un service peut avoir en attente sur un écouteur pour traiter les connexions entrantes au service.|  
|maxPendingConnections|Obtient ou définit le nombre maximal de connexions en attente de distribution sur le service.|  
|maxReceivedMessageSize|Obtient et définit la taille maximale autorisée pour le message, en octets, qui peut être reçue.|  
|transferMode|Obtient ou définit une valeur qui indique si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.|  
|[\<connectionPoolSettings> of \<namedPipeTransport>](connectionpoolsettings.md)|Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
Ce transport utilise des URI au format "net.pipe://nom_hôte/chemin". Les autres composants URI sont facultatifs.  
  
L’élément `namedPipeTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport des canaux nommés. Ce transport est utilisé pour la communication entre WCF (Windows Communication Foundation) et WCF sur des ordinateurs.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transports](../../../wcf/feature-details/transports.md)
- [Choix d’un transport](../../../wcf/feature-details/choosing-a-transport.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
