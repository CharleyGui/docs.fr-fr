---
title: Communication basée sur des messages asynchrones
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Les communications asynchrones par messages représentent un concept essentiel dans l’architecture de microservices, car elles constituent le meilleur moyen de maintenir l’indépendance des microservices les uns par rapport aux autres tout en les synchronisant au bout du compte.
ms.date: 09/20/2018
ms.openlocfilehash: 476e42ccb39374c2bb50f22e41f60c10c563dc66
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144342"
---
# <a name="asynchronous-message-based-communication"></a>Communication basée sur des messages asynchrones

La messagerie asynchrone et la communication pilotée par les événements sont des fonctionnalités essentielles lors de la propagation de changements sur plusieurs microservices et leurs modèles de domaine connexes. Comme mentionné précédemment dans la discussion sur les microservices et les contextes délimités (BC, Bounded Context), les modèles comme User, Customer, Product, Account, etc. peuvent avoir des significations différentes pour différents microservices ou BC. Quand des changements ont lieu, vous devez donc les rapprocher entre les différents modèles. Une solution consiste à utiliser la cohérence à terme et la communication par messagerie asynchrone pilotée par les événements.

Quand vous utilisez la messagerie, les processus communiquent en échangeant des messages de façon asynchrone. Un client exécute une commande ou une requête sur un service en lui envoyant un message. Si le service doit répondre, il retourne un autre message au client. Dans la mesure où la communication est basée sur les messages, le client part du principe que les réponses ne sont pas immédiates, et qu’il est possible qu’il ne reçoive aucune réponse.

Un message comprend un en-tête (composé de métadonnées telles que des informations d’identification ou de sécurité) et un corps. Les messages sont généralement envoyés par le biais de protocoles asynchrones comme AMQP.

Dans la communauté des microservices, l’infrastructure de choix pour ce type de communication est un répartiteur de messages léger, dont la conception diffère de celle des grands répartiteurs et orchestrateurs utilisés dans SOA. Constitué en général d’une infrastructure « passive », le répartiteur de messages léger se limite à la répartition des messages. Ses implémentations sont simples, par exemple RabbitMQ ou Azure Service Bus (un Service Bus scalable dans le cloud). Dans ce scénario, la plupart des fonctions « intelligentes » résident toujours dans les points de terminaison qui produisent et consomment des messages, c’est-à-dire dans les microservices.

Une autre règle, que nous vous conseillons de suivre dans la mesure du possible, consiste à utiliser uniquement la messagerie asynchrone entre les services internes et à utiliser uniquement la communication synchrone (comme HTTP) des applications clientes aux services frontend (passerelles API, plus le premier niveau des microservices).

La communication asynchrone basée sur les messages se présente sous deux formes : celle avec un récepteur unique et celle avec plusieurs récepteurs. Les sections suivantes fournissent les détails correspondants.

## <a name="single-receiver-message-based-communication"></a>Communication basée sur les messages avec un récepteur unique

La communication asynchrone basée sur les messages avec un seul récepteur se caractérise comme suit : un message est remis à un seul des consommateurs lisant les données du canal (communication point à point), et le message n’est traité qu’une seule fois. Toutefois, il existe des situations particulières. Par exemple, dans un système cloud qui tente de procéder à une récupération automatique après une défaillance, le même message peut être envoyé plusieurs fois. En cas de panne réseau ou autre, le client doit pouvoir réessayer d’envoyer des messages, et le serveur doit implémenter une opération idempotente pour qu’un message donné ne soit traité qu’une seule fois.

La communication basée sur les messages avec un récepteur unique convient bien à l’envoi de commandes asynchrones d’un microservice à un autre. La Figure 4-18 illustre cette approche.

Une fois la communication basée sur les messages lancée (avec des commandes ou des événements), évitez de mélanger ce type de communication et la communication HTTP synchrone.

![Microservice unique recevant un message asynchrone](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Figure 4-18**. Microservice unique recevant un message asynchrone

Notez que les commandes provenant d’applications clientes peuvent être implémentées en tant que commandes synchrones HTTP. Si vous souhaitez bénéficier d’une scalabilité plus élevée ou si vous vous trouvez déjà dans un processus métier à base de messages, utilisez des commandes à base de messages.

## <a name="multiple-receivers-message-based-communication"></a>Communication basée sur les messages avec plusieurs récepteurs

Une approche plus souple consiste à utiliser un mécanisme de publication/abonnement de manière à ce que les communications de l’expéditeur soient accessibles aux microservices d’autres abonnés ou à des applications externes. Il est donc utile de suivre le [principe ouvert/fermé](https://en.wikipedia.org/wiki/Open/closed_principle) dans le service d’envoi. De cette façon, des abonnés peuvent être ajoutés sans qu’il soit nécessaire de modifier le service de l’expéditeur.

Quand vous utilisez une communication par publication/abonnement, vous pouvez utiliser une interface de bus d’événements pour publier les événements sur un abonné.

## <a name="asynchronous-event-driven-communication"></a>Communication asynchrone pilotée par les événements

Quand vous utilisez une communication asynchrone pilotée par les événements, un microservice publie un événement d’intégration dès que quelque chose se produit dans son domaine, comme un changement de prix dans un microservice de catalogue de produits, pour en informer un autre microservice. D’autres microservices peuvent s’abonner aux événements pour les recevoir de manière asynchrone. Dans ce cas, les récepteurs peuvent mettre à jour leurs propres entités de domaine, ce qui peut entraîner d’autres événements d’intégration. Ce système de publication/abonnement est généralement obtenu à l’aide de l’implémentation d’un bus d’événements. Le bus d’événements peut être conçu comme une abstraction ou une interface, avec l’API nécessaire pour s’abonner aux événements ou s’en désabonner ainsi que pour les publier. Le bus d’événements peut également avoir une ou plusieurs implémentations basées sur un répartiteur entre processus ou de messagerie, comme une file d’attente de messagerie ou un Service Bus prenant en charge la communication asynchrone, ainsi qu’un modèle de publication/abonnement.

Si un système utilise la cohérence à terme pilotée par les événements d’intégration, il est recommandé que cette approche soit clairement indiquée à l’utilisateur final. Le système ne doit pas utiliser une approche qui reproduit les événements d’intégration, par exemple SignalR ou les systèmes d’interrogation du client. L’utilisateur final et le propriétaire de l’entreprise doivent explicitement adopter la cohérence à terme dans le système. Ils doivent aussi avoir conscience que cette approche ne pose généralement aucun problème dans l’entreprise, à condition qu’elle soit explicite. Cela est important, car les utilisateurs peuvent s’attendre à voir des résultats immédiatement, ce qui ne se produit pas forcément avec une cohérence à terme.

Comme indiqué précédemment dans la section [Défis et solutions pour la gestion de données distribuée](distributed-data-management.md), vous pouvez utiliser des événements d’intégration pour implémenter des tâches d’entreprise qui s’étendent sur plusieurs microservices. Vous bénéficiez ainsi d’une cohérence à terme entre ces services. Une transaction cohérente à terme se compose d’une collection d’actions distribuées. À chaque action, le microservice connexe met à jour une entité de domaine et publie un autre événement d’intégration qui déclenche l’action suivante au sein de la même tâche d’entreprise de bout en bout.

Il est important de noter qu’il est possible de communiquer avec plusieurs microservices qui sont abonnés au même événement. Pour ce faire, vous pouvez utiliser la messagerie par publication/abonnement basée sur la communication pilotée par les événements, comme le montre la figure 4-19. Ce mécanisme de publication/d’abonnement n’est pas réservé à l’architecture des microservices. Il est similaire à la façon dont les [contextes délimités](https://martinfowler.com/bliki/BoundedContext.html) dans DDD doivent communiquer, ou à la façon dont vous propagez les mises à jour de la base de données accessible en écriture à la base de données accessible en lecture dans le modèle d’architecture [CQRS (séparation des responsabilités en matière de commande et de requête)](https://martinfowler.com/bliki/CQRS.html). L’objectif est d’obtenir une cohérence à terme entre plusieurs sources de données dans votre système distribué.

![Diagramme montrant les communications asynchrones pilotées par les événements.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Figure 4-19**. Communication par message asynchrone pilotée par les événements

Dans une communication asynchrone pilotée par les événements, un microservice publie les événements sur un bus d’événements. De nombreux microservices peuvent s’y abonner pour recevoir des notifications et agir en conséquence. Votre implémentation détermine le protocole à utiliser pour les communications basées sur messages et pilotées par les événements. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) peut vous aider à obtenir une communication en file d’attente fiable.

Quand vous utilisez un bus d’événements, vous pouvez utiliser un niveau d’abstraction (par exemple, une interface de bus d’événements) basé sur une implémentation connexe dans des classes avec du code utilisant l’API d’un répartiteur de message comme [RabbitMQ](https://www.rabbitmq.com/) ou d’un Service Bus comme [Azure Service Bus avec des rubriques](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Vous pouvez également utiliser un Service Bus de niveau supérieur comme NServiceBus, MassTransit ou Brighter pour définir votre bus d’événements et votre système de publication/abonnement.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Remarque à propos des technologies de messagerie pour les systèmes de production

Les technologies de messagerie disponibles pour implémenter votre bus d’événements abstraits se répartissent en plusieurs niveaux. Par exemple, des produits comme RabbitMQ (transport pour répartiteur de message) et Azure Service Bus sont à un niveau inférieur par rapport à d’autres produits comme NServiceBus, MassTransit ou Brighter qui peuvent s’appuyer sur RabbitMQ et Azure Service Bus pour offrir davantage de fonctionnalités. Votre choix dépend du nombre de fonctionnalités avancées au niveau application et du niveau de scalabilité prête à l’emploi dont vous avez besoin pour votre application. Si vous souhaitez uniquement implémenter un bus d’événements en guise de preuve de concept pour votre environnement de développement, comme dans l’exemple eShopOnContainers, une simple implémentation reposant sur RabbitMQ sur un conteneur Docker peut suffire.

Toutefois, pour les systèmes stratégiques et les systèmes de production qui nécessitent un haut niveau de scalabilité, il peut être utile d’évaluer Azure Service Bus. Pour les abstractions et les fonctionnalités de haut niveau qui facilitent le développement des applications distribuées, nous vous recommandons d’évaluer d’autres Service Bus commerciaux et open source, tels que NServiceBus, MassTransit et Brighter. Bien entendu, vous pouvez créer vos propres fonctionnalités Service Bus sur des technologies de niveau inférieur comme RabbitMQ et Docker. Mais tout ce travail peut coûter très cher pour une application d’entreprise personnalisée.

## <a name="resiliently-publishing-to-the-event-bus"></a>Publication résiliente sur le bus d’événements

L’implémentation d’une architecture pilotée par les événements sur plusieurs microservices soulève le problème suivant : comment mettre à jour atomiquement l’état dans le microservice d’origine tout en publiant avec résilience son événement d’intégration connexe dans le bus d’événements et en tenant compte des transactions. Voici quelques manières d’y parvenir, mais d’autres approches peuvent être envisagées.

- Utilisation d’une file d’attente transactionnelle, basée sur DTC, comme MSMQ. (Toutefois, il s’agit d’une approche héritée.)

- Utiliser [l’exploration des données du journal des transactions](https://www.scoop.it/t/sql-server-transaction-log-mining)

- Utilisation de la version complète du [modèle d’approvisionnement en événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Utilisation du [modèle Outbox](https://www.kamilgrzybek.com/design/the-outbox-pattern/) : table de base de données transactionnelle définie comme file d’attente de messages qui sert de base à un composant créateur d’événement qui crée l’événement et le publie.

Si vous envisagez d’utiliser la communication asynchrone, veillez également à tenir compte de l’idempotence et de la déduplication des messages. Ces rubriques sont traitées dans la section [Implémentation de la communication basée sur les événements entre les microservices (événements d’intégration)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) plus loin dans ce guide.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Messagerie pilotée par les événements** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Canal de publication/abonnement** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **UDI Dahan. CQRS clarifié** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

- **Séparation des responsabilités en matière de commande et de requête (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Communication entre les contextes délimités** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Cohérence éventuelle** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy bogard. Refactorisation vers la résilience : évaluation du couplage** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Précédent](communication-in-microservice-architecture.md) 
>  [Suivant](maintain-microservice-apis.md)
