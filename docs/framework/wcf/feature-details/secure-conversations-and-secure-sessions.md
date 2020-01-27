---
title: Conversations sécurisées et sessions sécurisées
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 887b2e6e6553a910de046950514869907519cf35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746451"
---
# <a name="secure-conversations-and-secure-sessions"></a>Conversations sécurisées et sessions sécurisées
Une fonctionnalité de Windows Communication Foundation (WCF) est la possibilité d’établir des sessions sécurisées entre deux points de terminaison qui s’authentifient mutuellement et s’accordent sur un chiffrement et un processus de signature numérique. Par exemple, le point de terminaison de service peut demander qu'un point de terminaison de client envoie un jeton de sécurité basé sur un certificat X.509 pour l'authentification. Une fois que le client est authentifié, le point de terminaison de service renvoie un jeton de contexte de sécurité (SCT) au client, utilisé ensuite pour sécuriser tous les messages suivants dans la session. L'établissement de cette session sécurisée permet d'améliorer l'ensemble des messages échangés entre les deux points de terminaison, parce que le SCT a une clé symétrique. Les clés asymétriques, sur lesquelles les certificats X.509 sont basés, requièrent beaucoup plus de puissance de calcul que les clés symétriques pour générer une signature numérique ou chiffrer un jeu de données.  
  
 La stratégie de démarrage (définie dans la section 6.2.7 de la norme [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) ) contient les assertions de sécurité de message utilisées pour sécuriser le canal et authentifier le client avant l’échange RST/SCT et RSTR/SCT. Certaines liaisons standard WCF ont une propriété `Security.Message.EstablishSecurityContext` qui contrôle si la conversation sécurisée est utilisée. Lors de l’utilisation de liaisons personnalisées, le bootstrap est indiqué en imbriquant les éléments de liaison de sécurité, soit via [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dans le fichier de configuration, soit en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> dans le code.  
  
 Pour plus d’informations sur les sessions, consultez [utilisation de sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Guide pratique pour créer un service qui requiert des sessions](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
