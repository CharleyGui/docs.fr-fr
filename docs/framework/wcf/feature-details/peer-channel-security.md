---
title: Sécurité de canal homologue
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: a237987a0139f0f72f2e49be318da0f62c4f2691
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247861"
---
# <a name="peer-channel-security"></a>Sécurité de canal homologue

Le canal homologue active divers types d'applications distribuées qui dépendent de la messagerie entre plusieurs parties. Certains exemples incluent la distribution de contenu Internet, où une source fiable distribue du contenu (tel que des supports ou mises à jour logicielles), un groupe d’amis échange de la musique et des photos, ou une équipe de collègues modifie de manière collaborative un document. Chacun de ces scénarios requiert un modèle de sécurité unique. Le modèle de sécurité du canal homologue est conçu pour gérer ces scénarios et fournit un modèle de sécurité complet adapté aux besoins spécifiques des divers modèles d'identité, d'authentification et d'autorisation.  
  
## <a name="security-scenarios"></a>Scénarios de sécurité  

 Un scénario de distribution de contenu requiert que chaque destinataire identifie la source du contenu. En raison de la nature distribuée du scénario, il n'est pas toujours possible de savoir et d'avoir confiance dans les intermédiaires qui traitent ou interceptent les messages. Pour atténuer efficacement les risques de falsification des messages par un intermédiaire non fiable, les applications peuvent sécuriser le message au niveau de l'expéditeur afin de détecter facilement les tentatives de falsification. Dans ce cas, selon la confidentialité du contenu, le chiffrement peut s'avérer nécessaire.  
  
 Les scénarios de collaboration tels que la collaboration de documents de groupe requièrent souvent l'authentification et l'identification individuelles de chaque membre participant à la session. Un mécanisme permettant de définir des groupes d'utilisateurs et d'effectuer une authentification par rapport à ces groupes est donc nécessaire pour avoir une session sécurisée. De plus, les applications peuvent exiger le suivi de chaque message par authentification au niveau du message. Dans ces types d'applications, la performance peut être sacrifiée au bénéfice d'une méthode de sécurité plus puissante.  
  
 Une session de communication au sein d'un groupe d'utilisateurs informels peut exiger des modèles de sécurité informels, tels que la connaissance d'un secret commun au sein de ce groupe. Pour ces types d'applications, il est plus important de disposer d'un modèle de sécurité facile à mettre en place et à configurer que d'avoir le formulaire d'authentification le plus puissant ou de proposer des mesures de non-répudiation. Pour ces scénarios, un mécanisme d'authentification par mot de passe permet de sécuriser la couche de communication tout en permettant toujours l'authentification des messages. La sécurité par mot de passe est le paramètre par défaut du canal homologue.  
  
## <a name="token-types"></a>Types de jetons  

 Le canal homologue reconnaît un seul type de jeton pour les certificats d'identification X.509 puissants qui fournissent un modèle d'identité performant basé sur le type d'authentification et d'autorisation qui peut être implémenté. Les certificats permettent d'assurer facilement la confidentialité et l'intégrité. Toutefois, les certificats X.509 peuvent s'avérer difficiles à utiliser et à déployer.  
  
 Le canal homologue prend également en charge les applications simples via l'utilisation de mots de passe. Les applications peuvent choisir d'installer des groupes d'homologues rapides et simples en fonction d'un mot de passe fourni. Dans ce cas, un propriétaire de groupe décide et communique le mot de passe aux membres. Chaque membre doit se connecter à l'aide de ce mot de passe avant de pouvoir se joindre à la session. Les mots de passe peuvent uniquement être utilisés pour autoriser l'entrée à la session, mais ne peuvent pas l'être pour effectuer l'authentification des messages. Cela et dû au fait qu'un jeton symétrique partagé par un groupe d'homologues est difficile à utiliser et s'avère inapproprié pour l'authentification de la source.  
  
## <a name="security-model"></a>Modèle de sécurité  

 Le canal homologue permet de sécuriser les liaisons individuelles entre les homologues. Cela signifie qu'un message ne transite jamais sur un lien non sécurisé (du point de vue de l'application). En interne, chaque lien (canal de transport entre deux homologues) est sécurisé à l'aide du protocole TLS (Transport Layer Security). Cela signifie que lorsqu'un expéditeur compose et envoie un message, celui-ci est envoyé sur un transport sécurisé à chacun de ses homologues immédiats, qui accèdent au message et, à leur tour, l'envoient à leurs homologues immédiats sur des connexions sécurisées. Cette sécurité fonctionne uniquement au niveau du transport et est indépendante des modèles de sécurité de message.  
  
 Le canal homologue permet également de sécuriser les messages indépendamment de la sécurité de transport utilisée. Dans ce modèle, le message est sécurisé à la source à l'aide du jeton de sécurité de la source, même si actuellement seuls les certificats X.509 sont pris en charge. Le message sécurisé est ensuite transmis sur le réseau d'homologues. Chaque homologue de réception peut vérifier l'authenticité de la source. Notez que le message est sécurisé afin que les intermédiaires ne puissent pas le falsifier.  
  
 Pour assurer la confidentialité, les applications peuvent associer la sécurité de transport avec des méthodes d'appartenance au groupe puissantes afin d'empêcher l'accès non autorisé au message.  
  
 Le canal homologue ne requiert pas de modèle d'identité spécifique tant que l'application choisit l'un des types de jetons pris en charge. Les applications gèrent entièrement le cycle de vie de ces identités et des décisions d'authentification.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications de canal homologue](securing-peer-channel-applications.md)
- [Concepts relatifs au canal homologue](peer-channel-concepts.md)
- [Création d'une application de canal homologue](building-a-peer-channel-application.md)
