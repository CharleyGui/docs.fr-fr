---
title: Implémentation d’un bus d’événements avec RabbitMQ pour un environnement de développement ou de test
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utiliser RabbitMQ pour implémenter une messagerie de bus d’événements pour les événements d’intégration des environnements de développement ou de test.
ms.date: 10/02/2018
ms.openlocfilehash: 1af72d18825eb610d6900178205450e2c2e34c25
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306888"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implémentation d’un bus d’événements avec RabbitMQ pour un environnement de développement ou de test

Avant tout, nous tenons à préciser la chose suivante : si vous créez votre bus d’événements personnalisé en le basant sur l’exécution de RabbitMQ dans un conteneur, comme le fait l’application eShopOnContainers, utilisez ce bus d’événements personnalisé uniquement pour vos environnements de développement et de test. Ne l’utilisez pas pour votre environnement de production, sauf si vous le générez dans le cadre d’un service bus prêt pour la production. Dans un bus d’événements personnalisé simplifié, il manque de nombreuses fonctionnalités critiques prêtes pour la production, contrairement à un Service Bus commercial.

L’une des implémentations personnalisées du bus d’événements dans eShopOnContainers est fondamentalement une bibliothèque utilisant l’API RabbitMQ. (Il existe une autre implémentation basée sur Azure Service Bus.)

L’implémentation du bus d’événements avec RabbitMQ permet aux microservices de s’abonner aux événements, aux événements de publication et aux événements de réception, comme le montre la figure 6-21.

![Diagramme montrant les RabbitMQ entre l’expéditeur et le récepteur du message.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Figure 6-21.** Implémentation RabbitMQ d’un bus d’événements

RabbitMQ fonctionne comme un intermédiaire entre le serveur de publication des messages et les abonnés pour gérer la distribution. Dans le code, la classe EventBusRabbitMQ implémente l’interface IEventBus générique. Cette opération est basée sur une injection de dépendances pour vous permettre de passer de cette version de développement/test à une version de production.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

L’implémentation RabbitMQ d’un exemple de bus d’événements de développement/de test correspond à du code standard. Elle doit prendre en charge la connexion au serveur RabbitMQ et fournir le code nécessaire à la publication d’un événement de message sur les files d’attente. Elle doit également implémenter un dictionnaire de collections de gestionnaires d’événements d’intégration pour chaque type d’événement ; ces types d’événement peuvent avoir une instanciation différente et des abonnements distincts pour chaque microservice de réception, comme le montre la figure 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implémentation d’une méthode de publication simplifiée avec RabbitMQ

Le code suivant est une version ***simplifiée*** de l’implémentation d’un bus d’événements pour RabbitMQ, qui présente le scénario. On ne gère pas la connexion de cette façon. Pour voir l’implémentation complète, consultez le code dans le référentiel [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs).

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

Le [code réel](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de la méthode Publish de l’application eShopOnContainers est amélioré à l’aide d’une stratégie de nouvelles tentatives d’[interrogation](https://github.com/App-vNext/Polly). Cette stratégie consiste à réessayer d’exécuter la tâche un certain nombre de fois, au cas où le conteneur RabbitMQ ne serait pas prêt. Cela peut se produire quand docker-compose démarre les conteneurs. Par exemple, le conteneur RabbitMQ peut démarrer plus lentement que les autres conteneurs.

Comme indiqué précédemment, il existe de nombreuses configurations possibles dans RabbitMQ. Ce code doit donc être utilisé uniquement pour les environnements de développement/test.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implémentation du code d’abonnement avec l’API RabbitMQ

Comme pour le code de publication, le code suivant est une simplification d’une partie de l’implémentation du bus d’événements pour RabbitMQ. Là encore, vous n’avez généralement pas besoin de le changer, sauf pour l’améliorer.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

Chaque type d’événement a un canal associé qui permet d’obtenir les événements à partir de RabbitMQ. Vous pouvez avoir autant de gestionnaires d’événements par canal et par type d’événement que nécessaire.

La méthode Subscribe accepte un objet IIntegrationEventHandler, qui est semblable à une méthode de rappel dans le microservice actuel, en plus de son objet IntegrationEvent associé. Le code ajoute ensuite ce gestionnaire d’événements à la liste des gestionnaires d’événements que chaque type d’événement d’intégration peut avoir par microservice client. Si le code du client n’est pas déjà abonné à l’événement, il crée un canal pour le type d’événement afin de permettre la réception d’événements par envoi (push) à partir de RabbitMQ, quand l’événement concerné est publié depuis un autre service.

Comme indiqué ci-dessus, le bus d’événements implémenté dans eShopOnContainers a uniquement et à des fins pédagogiques, car il ne gère que les principaux scénarios, donc il n’est pas prêt pour la production.

Pour les scénarios de production, vérifiez les ressources supplémentaires ci-dessous, spécifiques à RabbitMQ, et la section implémentation de la [communication basée sur les événements entre les microservices](./integration-event-based-microservice-communications.md#additional-resources) .

## <a name="additional-resources"></a>Ressources supplémentaires

Solution prête pour la production avec prise en charge de RabbitMQ.

- **EasyNetQ** -client API .net Open source pour RabbitMQ \
  <https://easynetq.com/>

- **MassTransit** \
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> [Précédent](integration-event-based-microservice-communications.md) 
>  [Suivant](subscribe-events.md)
