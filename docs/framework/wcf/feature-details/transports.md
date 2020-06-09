---
title: Transports dans Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598669"
---
# <a name="transports-in-windows-communication-foundation"></a>Transports dans Windows Communication Foundation
La couche de transport se situe au niveau le plus bas de la pile des canaux. Les transports principaux utilisés dans Windows Communication Foundation (WCF) sont HTTP, HTTPs, TCP et les canaux nommés. Les rubriques de cette section contiennent des conseils et des instructions permettant de savoir quel protocole choisir, de le configurer et de définir les propriétés de réglage afférentes.  
  
 WCF comprend des transports supplémentaires. Pour plus d’informations sur le transport Message Queuing (également appelé MSMQ), consultez [files d’attente et sessions fiables](queues-and-reliable-sessions.md). Pour plus d’informations sur le transport d’égal à égal, consultez [mise en réseau pair à pair](peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Choix d'un transport](choosing-a-transport.md)  
 Présente les trois transports principaux et aborde les différents points à prendre en considération lors de leur sélection.  
  
 [Sélection d'un encodeur de message](choosing-a-message-encoder.md)  
 Aborde les facteurs à prendre en considération lors de la sélection d’un élément de liaison d’encodage de message.  
  
 [Transfert des messages par diffusion en continu](streaming-message-transfer.md)  
 Contient des instructions permettant de configurer la couche de transport pour une diffusion en continu.  
  
 [Configuration de HTTP et HTTPS](configuring-http-and-https.md)  
 Contient des instructions permettant de configurer les éléments de liaison de transport HTTP et HTTPS.  
  
 [Procédure : remplacer la réservation d'URL WCF par une réservation restreinte](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Décrit comment utiliser des réservations restreintes WCFURL.  
  
 [Quotas de transport](transport-quotas.md)  
 Aborde les points à prendre en considération lors de la définition de quotas pour la couche de transport.  
  
 [Utilisation des NAT et des pare-feu](working-with-nats-and-firewalls.md)  
 Contient des instructions permettant de configurer la couche de transport lorsque les messages envoyés ou reçus rencontrent un pare-feu ou lorsqu'un traducteur d'adresses réseau (NAT) est utilisé.  
  
 [Partage de ports Net.TCP](net-tcp-port-sharing.md)  
 Décrit comment utiliser le composant de partage de port Net. TCP de WCF.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Sections connexes  
 [Liaisons](bindings.md)  
  
 [Extension de liaisons](../extending/extending-bindings.md)
