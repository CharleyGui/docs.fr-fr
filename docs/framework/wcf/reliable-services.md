---
title: Services fiables (Reliable Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: d028af80a30fd18b6aa6e9678e7fd8788e7b7b95
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249746"
---
# <a name="reliable-services"></a>Services fiables (Reliable Services)

Les files d’attente et les sessions fiables sont les fonctionnalités de Windows Communication Foundation (WCF) qui implémentent la messagerie fiable. Cette rubrique décrit les fonctionnalités de messagerie fiable de WCF.  
  
 La *messagerie fiable* est la manière dont une source de messagerie fiable (appelée *source*) transfère les messages de manière fiable vers une destination de messagerie fiable (appelée *destination*).  
  
 La messagerie fiable effectue les tâches suivantes :  
  
- Elle assure le transfert des assurances de messages envoyés depuis une source vers une destination, et ce quelles que soient les défaillances rencontrées par le transport ou le transfert de ces messages.  
  
- Elle sépare la source de la destination. Ceci garantit l'indépendance des systèmes de défaillance et de récupération de la source et de la destination ainsi que le transfert et la remise fiables des messages même en cas d'indisponibilité de l'une ou de l'autre.  
  
 La messagerie fiable présente l'inconvénient d'engendrer une latence élevée. La *latence* est le temps nécessaire pour que le message atteigne la destination à partir de la source. WCF fournit donc les types suivants de messagerie fiable :  
  
- Des [sessions fiables](./feature-details/reliable-sessions.md), qui offrent un transfert fiable sans le coût de la latence élevée.  
  
- Les [files d’attente dans WCF](./feature-details/queues-in-wcf.md), qui offrent à la fois les transferts fiables et la séparation entre la source et la destination.  
  
## <a name="reliable-sessions"></a>Sessions fiables  

 À l'aide du protocole WS-Reliable Messaging, les sessions fiables assurent un transfert fiable des messages de bout en bout entre source et destination quels que soient les nombre et type d'intermédiaires figurant entre les points de terminaison (source et destination) de la messagerie. Au rang de ces intermédiaires figurent notamment tous les transports qui n'utilisent pas le protocole SOAP (par exemple, les proxys HTTP) ou les intermédiaires qui utilisent SOAP (par exemple, les routeurs ou les ponts SOAP), nécessaires à la circulation des messages entre les points de terminaison. Les sessions fiables utilisent une fenêtre de transfert en mémoire pour masquer les défaillances survenant au niveau des messages SOAP et rétablir les connexions en cas de défaillance des transports.  
  
 Les sessions fiables assurent le transfert fiable à faible latence des messages. Elles accomplissent pour les messages SOAP sur tous proxys ou intermédiaires, ce que le service TCP accomplit pour les paquets sur les ponts IP. Pour plus d’informations sur les sessions fiables, consultez [sessions fiables](./feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Files d’attente  

 Les files d’attente dans WCF fournissent des transferts fiables de messages et une séparation entre les sources et les destinations au détriment de la latence élevée. La communication en file d’attente WCF repose sur Message Queuing (MSMQ).  
  
 Le service MSMQ est un composant en option de Windows. Ce service s'exécute en tant que service Windows. Elle capture, au nom de la source, les messages à transmettre figurant dans la file d'attente de transmission, puis les remet à la file d'attente cible. La file d'attente cible accepte ces messages au nom de la destination pour les lui remettre ultérieurement dès qu'elle en fera la demande. Les gestionnaires MSMQ implémentent un protocole de transfert de message fiable afin d'éviter que les messages ne soient égarés pendant leur transmission. Il peut s'agir d'un protocole natif ou du protocole SOAP appelé protocole SRMP (SOAP Reliable Messaging Protocole).  
  
 La séparation, associée aux transferts fiables de messages entre les files d'attente, permet aux applications faiblement couplées de communiquer de manière fiable. À la différence des sessions fiables, dans le cadre d'une séparation, la source et la destination n'ont pas besoin de s'exécuter simultanément. Cela permet, de manière indirecte, d'utiliser les files d'attente comme dispositif de régulation de la charge lorsqu'il y a un écart entre le taux de production de messages de la source et le taux de réception de messages de la destination. Pour plus d’informations sur les files d’attente, consultez [files d’attente dans WCF](./feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des sessions fiables](./feature-details/reliable-sessions-overview.md)
- [Mise en file d'attente dans WCF](./feature-details/queuing-in-wcf.md)
