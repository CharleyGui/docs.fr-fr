---
title: Files d'attente et sessions fiables
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: db47838db1608dac4e0fe22252795b6dd33a0b6e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244689"
---
# <a name="queues-and-reliable-sessions"></a>Files d'attente et sessions fiables

Les files d’attente et les sessions fiables sont les fonctionnalités de Windows Communication Foundation (WCF) qui implémentent la messagerie fiable. Les rubriques contenues dans cette section traitent des fonctionnalités de messagerie fiable WCF.  
  
 La messagerie fiable correspond à un dispositif selon lequel une source de messagerie fiable (appelée la source) transfère de manière fiable des messages vers une destination de messagerie fiable (appelée la destination).  
  
 Les principaux aspects d'une messagerie fiable sont les suivants :  
  
- Assurances de transfert pour les messages envoyés depuis une source vers une destination, et ce quelles que soient les défaillances rencontrées par le transport ou le transfert de ces messages.  
  
- Séparation entre source et destination, pour un échec et une récupération indépendantes de la source et de la destination et pour le transfert et la remise fiables des messages même si la source ou la destination n'est pas disponible.  
  
 La messagerie fiable présente l'inconvénient d'engendrer une latence élevée. La latence correspond au temps nécessaire au message pour parvenir à la destination depuis la source. WCF fournit donc les types suivants de messagerie fiable :  
  
- Des [sessions fiables](reliable-sessions.md), qui offrent un transfert fiable sans le coût de la latence élevée  
  
- Les [files d’attente dans WCF](queues-in-wcf.md), qui offrent à la fois les transferts fiables et la séparation entre la source et la destination.  
  
## <a name="reliable-sessions"></a>Sessions fiables  

 À l'aide du protocole de messagerie WS-Reliable, les sessions fiables assurent un transfert fiable des messages de bout en bout entre source et destination quels que soient les nombre et type d'intermédiaires figurant entre les points de terminaison (source et destination) de la messagerie. Au rang de ces intermédiaires figurent notamment tous les transports qui n'utilisent pas le protocole SOAP (par exemple, les proxys HTTP) ou les intermédiaires qui utilisent SOAP (par exemple, les routeurs ou les ponts SOAP), nécessaires à la circulation des messages entre les points de terminaison. Les sessions fiables utilisent une fenêtre de transfert en mémoire pour masquer les défaillances survenant au niveau des messages SOAP et rétablir les connexions en cas de défaillance des transports.  
  
 Les sessions fiables assurent le transfert fiable à faible latence des messages. Elles accomplissent pour les messages SOAP sur tous proxys ou intermédiaires, ce que le service TCP accomplit pour les paquets sur les ponts IP. Pour plus d’informations sur les sessions fiables, consultez [sessions fiables](reliable-sessions.md).  
  
## <a name="queues"></a>Files d’attente  

 Les files d’attente dans WCF fournissent des transferts fiables de messages et une séparation entre les sources et les destinations au détriment de la latence élevée. La communication en file d’attente WCF repose sur Message Queuing (également appelé MSMQ).  
  
 MSMQ est incluse en tant qu'option dans Windows et s'exécute comme un service NT. Elle capture, au nom de la source, les messages à transmettre figurant dans la file d'attente de transmission, puis les remet à la file d'attente cible. La file d'attente cible accepte ces messages au nom de la destination pour les lui remettre ultérieurement dès qu'elle en fera la demande. Les Gestionnaires des files d'attente MSMQ implémentent un protocole de transfert de message fiable qui empêche la perte de messages au cours de la transmission. Il peut s'agir d'un protocole natif ou d'un protocole basé sur SOAP, comme le protocole SRMP (SOAP, Reliable Messaging Protocole).  
  
 La séparation, associée aux transferts fiables de messages entre les files d'attente, permet aux applications faiblement couplées de communiquer de manière fiable. À la différence des sessions fiables, dans le cadre d'une séparation, la source et la destination n'ont pas besoin de s'exécuter simultanément. Cela permet, de manière indirecte, d'utiliser les files d'attente comme dispositif de régulation de la charge lorsqu'il y a un écart entre le taux de production de messages de la source et le taux de consommation de messages de la destination. Pour plus d’informations sur les files d’attente, consultez [files d’attente dans WCF](queues-in-wcf.md).  
  
## <a name="see-also"></a>Voir aussi

- [Files d’attente dans WCF](queues-in-wcf.md)
- [Mise en file d'attente dans WCF](queuing-in-wcf.md)
- [Sessions fiables](reliable-sessions.md)
- [Vue d'ensemble des sessions fiables](reliable-sessions-overview.md)
