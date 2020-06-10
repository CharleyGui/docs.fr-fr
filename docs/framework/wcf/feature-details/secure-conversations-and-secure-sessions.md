---
title: Conversations sécurisées et sessions sécurisées
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 3245c062db003cc387eff7af92fabe1554311c73
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590226"
---
# <a name="secure-conversations-and-secure-sessions"></a>Conversations sécurisées et sessions sécurisées
Une fonctionnalité de Windows Communication Foundation (WCF) est la possibilité d’établir des sessions sécurisées entre deux points de terminaison qui s’authentifient mutuellement et s’accordent sur un chiffrement et un processus de signature numérique. Par exemple, le point de terminaison de service peut demander qu'un point de terminaison de client envoie un jeton de sécurité basé sur un certificat X.509 pour l'authentification. Une fois que le client est authentifié, le point de terminaison de service renvoie un jeton de contexte de sécurité (SCT) au client, utilisé ensuite pour sécuriser tous les messages suivants dans la session. L'établissement de cette session sécurisée permet d'améliorer l'ensemble des messages échangés entre les deux points de terminaison, parce que le SCT a une clé symétrique. Les clés asymétriques, sur lesquelles les certificats X.509 sont basés, requièrent beaucoup plus de puissance de calcul que les clés symétriques pour générer une signature numérique ou chiffrer un jeu de données.  
  
 La stratégie de démarrage (définie dans la section 6.2.7 de la norme [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) ) contient les assertions de sécurité de message utilisées pour sécuriser le canal et authentifier le client avant l’échange RST/SCT et RSTR/SCT. Certaines liaisons standard WCF ont une `Security.Message.EstablishSecurityContext` propriété qui contrôle si la conversation sécurisée est utilisée. Lors de l’utilisation de liaisons personnalisées, le bootstrap est indiqué en imbriquant les éléments de liaison de sécurité, soit via [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) dans le fichier de configuration, soit en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> dans le code.  
  
 Pour plus d’informations sur les sessions, consultez [utilisation de sessions](../using-sessions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sessions, instanciation et concurrence](sessions-instancing-and-concurrency.md)
- [Comment : créer un service qui requiert des sessions](how-to-create-a-service-that-requires-sessions.md)
