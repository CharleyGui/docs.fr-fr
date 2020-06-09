---
title: Vue d'ensemble des sessions fiables
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601086"
---
# <a name="reliable-sessions-overview"></a>Vue d'ensemble des sessions fiables

La messagerie fiable SOAP Windows Communication Foundation (WCF) fournit une fiabilité de transfert de messages de bout en bout entre les points de terminaison SOAP. Elle permet cela sur des réseaux peu fiables en remédiant aux échecs de transport et aux échecs au niveau du message SOAP. Notamment, elle fournit une remise basée sur session, unique et ordonnée (facultativement) pour les messages envoyés via SOAP ou des intermédiaires de transport. La remise basée sur la session permet de regrouper des messages dans une session avec un classement facultatif des messages.

Cette rubrique décrit les sessions fiables, comment et quand les utiliser, et comment les sécuriser.

## <a name="wcf-reliable-sessions"></a>Sessions fiables WCF

Les sessions fiables WCF sont une implémentation de la messagerie SOAP Reliable telle que définie par le protocole WS-ReliableMessaging.

La messagerie fiable SOAP SOAP fournit une session fiable de bout en bout entre deux points de terminaison, quel que soit le nombre ou le type d’intermédiaires qui séparent les points de terminaison de messagerie. Cela comprend tous les intermédiaires de transport qui n’utilisent pas le protocole SOAP (par exemple, les proxies HTTP) ou les intermédiaires qui utilisent le protocole SOAP (par exemple, les routeurs ou ponts basés sur SOAP) qui sont requis pour le transit des messages entre les points de terminaison. Un canal de session fiable prend en charge les communications *interactives* afin que les services connectés par ce canal s’exécutent simultanément et échangent et traitent des messages dans des conditions de faible latence, autrement dit, dans des intervalles relativement courts. Ce couplage signifie que ces composants font l’ensemble de la progression ou échouent ensemble, de sorte qu’il n’y a pas d’isolation entre eux.

Une session fiable masque deux types d'échecs :

- Échecs au niveau du message SOAP, incluant les messages perdus ou dupliqués et les messages qui arrivent dans un ordre différent de l'ordre dans lequel ils ont été envoyés.

- Échecs de transport

Une session fiable implémente le protocole WS-ReliableMessaging et une fenêtre de transfert en mémoire pour masquer les échecs au niveau du message SOAP et rétablit des connexions en cas d'échecs de transport.

Une session fiable gère les messages SOAP de la même façon que TCP gère les paquets IP. Une connexion de socket TCP fournit un transfert unique et symétrique des paquets IP entre les nœuds. Le canal fiable fournit le même type de transfert fiable, mais il diffère de la fiabilité fournie par le socket TCP des façons suivantes :

- La fiabilité est fournie au niveau du message SOAP, non pour un paquet d'octets arbitrairement dimensionné.

- La fiabilité est indépendante du transport, pas seulement pour le transfert via TCP.

- La fiabilité n’est pas liée à une session de transport particulière (par exemple, la session qu’une connexion TCP fournit) et peut utiliser plusieurs sessions de transport simultanément ou séquentiellement au cours de la durée de vie de la session fiable.

- La session fiable existe entre les points de terminaison SOAP de l'expéditeur et du récepteur, indépendamment du nombre de connexions de transport requis pour la connectivité entre eux. En bref, la fiabilité TCP se termine là où la connexion de transport se termine, tandis qu’une session fiable fournit une fiabilité de bout en bout.

## <a name="reliable-sessions-and-bindings"></a>Sessions fiables et liaisons

Comme mentionné précédemment, une session fiable est indépendante du transport. En outre, vous pouvez établir une session fiable sur de nombreux modèles d’échange de messages, tels que la demande-réponse ou le duplex. Une session fiable WCF est exposée en tant que propriété d’un ensemble de liaisons.

Utilisez une session fiable sur les points de terminaison qui utilisent :

- Des liaisons standard de transport basées sur HTTP :

  - `WsHttpBinding` et expose des contrats demande-réponse ou unidirectionnels.

  - Lors de l’utilisation d’une session fiable sur un contrat de service unidirectionnel ou de demande-réponse.

  - `WsDualHttpBinding` et expose des contrats duplex, demande-réponse ou unidirectionnels.

  - `WsFederationHttpBinding` et expose des contrats demande-réponse ou unidirectionnels.

- Des liaisons standard de transport basées sur TCP :

  - `NetTcpBinding` et expose des contrats duplex, demande-réponse ou unidirectionnels.

Utilisez une session fiable sur toutes les autres liaisons en créant une liaison personnalisée, telle que HTTPs (pour plus d’informations sur les problèmes, consultez <a href="#reliable-sessions-and-security">sessions fiables et sécurité</a>) ou une liaison de canal nommé.

Vous pouvez empiler une session fiable sur différents types de canaux sous-jacents et la forme du canal de session fiable résultant varie. Sur le client et le serveur, le type de canal de session fiable pris en charge dépend du type de canal sous-jacent utilisé. Le tableau suivant répertorie les types de canaux de session pris en charge sur le client en fonction du type de canal sous-jacent.

| Types de canaux de session fiables pris en charge&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Oui               | Oui                      | Oui              | Oui                     |
| `IRequestSessionChannel`                        | Oui               | Oui                      | Non               | Non                      |
| `IDuplexSessionChannel`                         | Non                | Non                       | Oui              | Oui                     |

&#8224;les types de canaux pris en charge sont les valeurs disponibles pour la `TChannel` valeur de paramètre générique qui est passée dans la <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> méthode.

Le tableau suivant répertorie les types de canaux de session pris en charge sur le serveur en fonction du type de canal sous-jacent.

| Types de canaux de session fiables pris en charge&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Oui             | Oui                    | Oui              | Oui                     |
| `IReplySessionChannel`                          | Oui             | Oui                    | Non               | Non                      |
| `IDuplexSessionChannel`                         | Non              | Non                     | Oui              | Oui                     |

&#8225;les types de canaux pris en charge sont les valeurs disponibles pour la `TChannel` valeur de paramètre générique qui est passée dans la <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> méthode.

## <a name="reliable-sessions-and-security"></a>Sessions fiables et sécurité

La sécurisation d’une session fiable est importante pour s’assurer que les tiers communicants (service et client) sont authentifiés et que les messages échangés dans la session ne sont pas falsifiés. En outre, il est important de garantir l’intégrité de chaque session fiable individuelle. Une session fiable est sécurisée en la liant à un contexte de sécurité représenté et géré par un canal de session de sécurité. Le canal de sécurité fournit une session de sécurité. Les jetons de sécurité échangés pendant l'établissement de la session sont ensuite utilisés pour sécuriser les messages dans la session fiable.

Lorsqu’une session fiable est sur TCP-S, la session TCP est liée à la session fiable. Par conséquent, la sécurité du transport garantit que la sécurité est également liée à la session fiable. Dans ce cas, le rétablissement de la connexion est désactivé.

La seule exception est l'utilisation du protocole HTTPS. La session protocole SSL (SSL) n’est pas liée à la session fiable. Cela impose une menace, car les sessions qui partagent un contexte de sécurité (la session SSL) ne sont pas protégées les unes des autres. Cela peut être une véritable menace en fonction de l’application.

## <a name="using-reliable-sessions"></a>Utilisation de sessions fiables

Pour utiliser des sessions fiables WCF, créez un point de terminaison avec une liaison qui prend en charge une session fiable. Utilisez l’une des liaisons fournies par le système que WCF fournit avec la session fiable activée, ou créez votre propre liaison personnalisée qui effectue cette configuration.

Les liaisons définies par le système qui prennent en charge et activent une session fiable par défaut incluent :

- <xref:System.ServiceModel.WSDualHttpBinding>

Les liaisons fournies par le système qui prennent en charge une session fiable en tant qu’option, mais qui n’en activent aucune par défaut, incluent :

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Pour obtenir un exemple de création d’une liaison personnalisée, consultez [Comment : créer une liaison de session fiable personnalisée avec HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

Pour une description des liaisons WCF qui prennent en charge les sessions fiables, consultez [liaisons fournies par le système](../system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Quand utiliser des sessions fiables

Il est important de comprendre quand utiliser des sessions fiables dans votre application. WCF prend en charge les sessions fiables entre les points de terminaison actifs et actifs en même temps. Si votre application requiert que l’un des points de terminaison soit indisponible pendant une durée, utilisez des files d’attente pour obtenir la fiabilité.

Si le scénario requiert deux points de terminaison connectés via TCP, TCP peut suffire à fournir des échanges de messages fiables. Toutefois, il n’est pas nécessaire d’utiliser une session fiable, puisque TCP garantit que les paquets arrivent dans l’ordre et une seule fois.

Si votre scénario présente l’une des caractéristiques suivantes, vous devez sérieusement envisager d’utiliser une session fiable.

- Intermédiaires SOAP, tels que les routeurs SOAP

- Intermédiaires de proxy ou ponts de transport

- Connectivité intermittente

- Sessions sur HTTP

## <a name="see-also"></a>Voir aussi

- [Utilisation de liaisons pour configurer des services et des clients](../using-bindings-to-configure-services-and-clients.md)
- [WS Reliable Session](../samples/ws-reliable-session.md)
