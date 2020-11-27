---
title: Quotas de transport
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: bcc63e6645580c1021667b278b80c09baf5700c1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261460"
---
# <a name="transport-quotas"></a>Quotas de transport

Les quotas de transport sont un mécanisme stratégique permettant de déterminer lorsqu'une connexion consomme trop de ressources. Un quota est une limite imposée qui empêche l'utilisation de ressources supplémentaires une fois la valeur du quota dépassée. Les quotas de transport permettent de lutter contre les attaques par déni de service malveillantes ou non intentionnelles.  
  
 Les transports Windows Communication Foundation (WCF) ont des valeurs de quota par défaut qui sont basées sur une allocation conservatrice des ressources. Ces valeurs par défaut sont adaptées aux environnements de développement et aux scénarios d'installation courts. Les administrateurs de service doivent examiner les quotas de transport et ajuster les valeurs de chaque quota si une installation manque de ressources ou si les connexions sont limitées malgré la disponibilité de ressources supplémentaires.  
  
## <a name="types-of-transport-quotas"></a>Types de quotas de transport  

 Les transports WCF ont trois types de quotas :  
  
- Les *délais d’attente* atténuent les attaques par déni de service qui reposent sur l’enduction des ressources pendant une période prolongée.  
  
- Les *limites d’allocation de mémoire* empêchent une connexion unique d’épuiser la mémoire système et de refuser le service à d’autres connexions.  
  
- Les *limites de taille de regroupement limitent* la consommation des ressources qui allouent indirectement de la mémoire ou qui sont en offre limitée.  
  
## <a name="transport-quota-descriptions"></a>Description des quotas de transport  

 Cette section décrit les quotas de transport disponibles pour les transports WCF standard : HTTP (S), TCP/IP et canaux nommés. Les transports personnalisés peuvent posséder des quotas configurables propres non inclus dans cette liste. Consultez la documentation relative à un transport personnalisé pour en savoir plus sur ses quotas.  
  
 Chaque paramètre de quota possède un type, une valeur minimale et une valeur par défaut. La valeur maximale d'un quota est limitée par son type. En raison des limites de l'ordinateur, il n'est pas toujours possible d'affecter à un quota sa valeur maximale.  
  
|Nom|Type|min.<br /><br /> value|Default<br /><br /> value|Description|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 graduation|5 secondes|Durée maximale à attendre pour qu'une connexion envoie le préambule pendant la lecture initiale. Ces données sont reçues avant que l'authentification ait lieu. Ce paramètre est généralement bien inférieur à la valeur de quota `ReceiveTimeout`.|  
|`CloseTimeout`|TimeSpan|0|1 minute|Durée maximale à attendre pour qu'une connexion se ferme avant que le transport ne lève une exception.|  
|`ConnectionBufferSize`|Integer|1|8 Ko|Taille, en octets, des mémoires tampon de réception et de transmission du transport sous-jacent. Augmenter la taille de la mémoire tampon peut améliorer le débit lors de l'envoi de messages volumineux.|  
|`IdleTimeout`|TimeSpan|0|2 min|Durée maximale pendant laquelle une connexion en groupe peut rester inactive avant d'être fermée.<br /><br /> Ce paramètre ne s'applique qu'aux connexions en groupe.|  
|`LeaseTimeout`|TimeSpan|0|5 minutes|Durée de vie maximale d'une connexion en groupe active. Après que la durée spécifiée s'est écoulée, la connexion se ferme une fois la requête en cours prise en charge.<br /><br /> Ce paramètre ne s'applique qu'aux connexions en groupe.|  
|`ListenBacklog`|Integer|1|10|Nombre maximal de connexions que l'écouteur n'a pas pris en charge avant que des connexions supplémentaires à ce point de terminaison soient refusées.|  
|`MaxBufferPoolSize`|Long|0|512 Ko|Mémoire maximale, en octets, que le transport consacre à regrouper des mémoires tampons de messages réutilisables. Lorsque le pool ne peut pas fournir de mémoire tampon de messages, une nouvelle mémoire tampon est allouée pour une utilisation temporaire.<br /><br /> Les installations qui créent de nombreuses fabrications de canaux ou écouteurs peuvent allouer de grandes quantités de mémoire aux pools de mémoires tampon. Dans ce scénario, la réduction de la taille de la mémoire tampon peut réduire fortement l'utilisation de la mémoire.|  
|`MaxBufferSize`|Integer|1|64 Ko|Taille maximale, en octets, d'une mémoire tampon utilisée pour diffuser en continu des données. Si ce quota de transport n'est pas défini, ou si le transport n'a pas recours à la diffusion en continu, la valeur de quota est identique à la plus petite de ces deux valeurs de quota : `MaxReceivedMessageSize` et <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Integer|1|10|Nombre maximal de connexions sortantes qui peuvent être associées à un point de terminaison particulier.<br /><br /> Ce paramètre ne s'applique qu'aux connexions en groupe.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Durée maximale à attendre après une opération d'envoi pour traiter par lot des messages supplémentaires dans une opération unique. Les messages sont envoyés plus tôt si la mémoire tampon du transport sous-jacent est pleine. L'envoi de messages supplémentaires ne réinitialise pas la période d'attente.|  
|`MaxPendingAccepts`|Integer|1|1|Nombre maximal de canaux que l'écouteur peut mettre en attente d'acceptation.<br /><br /> Il existe un intervalle entre la fin de l'acceptation en cours et le début d'une nouvelle acceptation. Augmenter la taille de cette collection peut empêcher la suppression des clients qui se connectent pendant cet intervalle.|  
|`MaxPendingConnections`|Integer|1|10|Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application. Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation.<br /><br /> Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions. Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota.|  
|`MaxReceivedMessageSize`|Long|1|64 Ko|Taille maximale, en octets, d'un message reçu (en-têtes compris) avant que le transport ne lève une exception.|  
|`OpenTimeout`|TimeSpan|0|1 minute|Durée maximale à attendre pour qu'une connexion soit établie avant que le transport ne lève une exception.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Durée maximale à attendre pour qu'une opération de lecture se termine avant que le transport ne lève une exception.|  
|`SendTimeout`|Timespan|0|1 minute|Durée maximale à attendre pour qu'une opération d'écriture se termine avant que le transport ne lève une exception.|  
  
 Les quotas de transport `MaxPendingConnections` et `MaxOutboundConnectionsPerEndpoint` sont combinés dans un quota de transport unique appelé `MaxConnections` en cas de définition par la liaison ou la configuration. Seul l’élément de liaison autorise la définition de ces valeurs de quota une par une. Le quota de transport `MaxConnections` a les mêmes valeurs minimale et par défaut.  
  
## <a name="setting-transport-quotas"></a>Définition des quotas de transport  

 Les quotas de transport sont définis au moyen de l’élément de liaison de transport, la liaison de transport, la configuration de l’application ou la stratégie hôte. Ce document n'aborde pas le paramétrage des transports par la stratégie hôte. Consultez la documentation relative au transport sous-jacent pour découvrir les paramètres des quotas de stratégie hôte. La rubrique [configuration de http et HTTPS](configuring-http-and-https.md) décrit les paramètres de quota pour le pilote Http.sys. Recherchez plus d'informations sur la configuration des limites de Windows pour des connexions HTTP, TCP/IP et de canal nommé dans la Base de connaissances Microsoft.  
  
 D'autres types de quotas s'appliquent indirectement aux transports. L'encodeur de message que le transport utilise pour transformer un message en octets peut avoir ses propres paramètres de quota. Toutefois, ces quotas sont indépendants du type de transport utilisé.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Contrôle des quotas de transport depuis l’élément de liaison  

 La définition des quotas de transport au moyen de l’élément de liaison offre le maximum de souplesse pour contrôler le comportement du transport. Les délais par défaut pour les opérations de fermeture, d'ouverture, de réception et d'envoi sont issus de la liaison lorsqu'un canal est construit.  
  
|Nom|HTTP|TCP/IP|Canal nommé|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Contrôle des quotas de transport depuis la liaison  

 La définition des quotas de transport au moyen de la liaison permet de choisir parmi un ensemble de quotas simplifié tout en conservant l’accès aux valeurs de quota les plus courantes.  
  
|Nom|HTTP|TCP/IP|Canal nommé|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1. Le quota de transport `MaxBufferSize` est uniquement disponible sur la liaison `BasicHttp`. Les liaisons `WSHttp` sont destinées aux scénarios qui ne prennent pas en charge les modes de transport diffusés en continu.  
  
2. Les quotas de transport `MaxPendingConnections` et `MaxOutboundConnectionsPerEndpoint` sont combinés dans un quota de transport unique appelé `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Contrôle des quotas de transport depuis la configuration  

 La configuration de l’application peut définir les mêmes quotas de transport qu’en accédant directement aux propriétés d’une liaison. Dans les fichiers de configuration, le nom d'un quota de transport commence toujours par une minuscule. Par exemple, la propriété `CloseTimeout` d’une liaison correspond au paramètre `closeTimeout` dans la configuration et la propriété `MaxConnections` d’une liaison correspond au paramètre `maxConnections` dans la configuration.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
