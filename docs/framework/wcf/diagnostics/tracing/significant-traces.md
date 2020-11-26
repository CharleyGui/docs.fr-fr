---
title: Suivis principaux
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 9ad7c217b528cb2ad22169c1aea6391462bab1ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248668"
---
# <a name="significant-traces"></a>Suivis principaux

Cette rubrique répertorie quelques-unes des principales traces émises par Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Suivis principaux  
  
|Trace|Description|  
|-----------|-----------------|  
|Suivi du journal des messages|Le suivi est émis lorsqu’un message WCF est enregistré par la fonctionnalité d’enregistrement des messages lorsque la `System.ServiceModel.MessageLogging` source de suivi est activée. Un clic sur ce suivi permet d'afficher le message. Il existe quatre points d'enregistrement configurables pour un message : `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, également indiqués par l'attribut Message Source dans le suivi du journal des messages.|  
|Suivi de message reçu|Cette trace est émise lors de la réception d’un message WCF si la `System.ServiceModel` source de suivi est activée au niveau des informations ou des commentaires. Ce suivi est nécessaire pour consulter la flèche de corrélation du message dans la vue du graphique d'activité.|  
|Suivi de message envoyé|Ce suivi est émis lorsqu’un message WCF est envoyé si la `System.ServiceModel` source de suivi est activée au niveau des informations ou des commentaires. Ce suivi est nécessaire pour consulter la flèche de corrélation du message dans la vue du graphique d'activité.|  
|Obtenir ChannelEndpointElement|Ce suivi est émis dans la fabrication de canal Construct, au niveau des informations. Il fournit une description du point de terminaison auquel le client parle (adresse distante, liaison, nom de contrat).|  
|Obtenir ServiceElement|Ce suivi est émis dans l'hôte du service Construct, au niveau des informations. Elle fournit une description du contrat de service et de la liaison.|  
|Créer SocketConnection|Ce suivi est émis dans la première action Process exécutée par le client et dans l'activité Receive bytes du service. Il fournit les adresses IP locales et distantes. Il est émis au niveau Informations.|
