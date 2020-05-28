---
title: Implémentation d’un bus d’événements avec RabbitMQ pour un environnement de développement ou de test
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utiliser RabbitMQ pour implémenter une messagerie de bus d’événements pour les événements d’intégration des environnements de développement ou de test.
ms.date: 10/02/2018
ms.openlocfilehash: 32259c76fe81d324ba3ea9b35f7fddc6a0f9cdbc
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144290"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="ad80d-103">Implémentation d’un bus d’événements avec RabbitMQ pour un environnement de développement ou de test</span><span class="sxs-lookup"><span data-stu-id="ad80d-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="ad80d-104">Avant tout, nous tenons à préciser la chose suivante : si vous créez votre bus d’événements personnalisé en le basant sur l’exécution de RabbitMQ dans un conteneur, comme le fait l’application eShopOnContainers, utilisez ce bus d’événements personnalisé uniquement pour vos environnements de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="ad80d-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="ad80d-105">Ne l’utilisez pas pour votre environnement de production, sauf si vous le générez dans le cadre d’un Service Bus prêt pour la production.</span><span class="sxs-lookup"><span data-stu-id="ad80d-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="ad80d-106">Dans un bus d’événements personnalisé simplifié, il manque de nombreuses fonctionnalités critiques prêtes pour la production, contrairement à un Service Bus commercial.</span><span class="sxs-lookup"><span data-stu-id="ad80d-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="ad80d-107">L’une des implémentations personnalisées du bus d’événements dans eShopOnContainers est fondamentalement une bibliothèque utilisant l’API RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="ad80d-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="ad80d-108">(Il existe une autre implémentation basée sur Azure Service Bus.)</span><span class="sxs-lookup"><span data-stu-id="ad80d-108">(There's another implementation based on Azure Service Bus.)</span></span>

<span data-ttu-id="ad80d-109">L’implémentation du bus d’événements avec RabbitMQ permet aux microservices de s’abonner aux événements, aux événements de publication et aux événements de réception, comme le montre la figure 6-21.</span><span class="sxs-lookup"><span data-stu-id="ad80d-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Diagramme montrant les RabbitMQ entre l’expéditeur et le récepteur du message.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="ad80d-111">**Figure 6-21.**</span><span class="sxs-lookup"><span data-stu-id="ad80d-111">**Figure 6-21.**</span></span> <span data-ttu-id="ad80d-112">Implémentation RabbitMQ d’un bus d’événements</span><span class="sxs-lookup"><span data-stu-id="ad80d-112">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="ad80d-113">RabbitMQ fonctionne comme un intermédiaire entre le serveur de publication des messages et les abonnés pour gérer la distribution.</span><span class="sxs-lookup"><span data-stu-id="ad80d-113">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="ad80d-114">Dans le code, la classe EventBusRabbitMQ implémente l’interface IEventBus générique.</span><span class="sxs-lookup"><span data-stu-id="ad80d-114">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="ad80d-115">Cette opération est basée sur une injection de dépendances pour vous permettre de passer de cette version de développement/test à une version de production.</span><span class="sxs-lookup"><span data-stu-id="ad80d-115">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="ad80d-116">L’implémentation RabbitMQ d’un exemple de bus d’événements de développement/de test correspond à du code standard.</span><span class="sxs-lookup"><span data-stu-id="ad80d-116">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="ad80d-117">Elle doit prendre en charge la connexion au serveur RabbitMQ et fournir le code nécessaire à la publication d’un événement de message sur les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="ad80d-117">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="ad80d-118">Elle doit également implémenter un dictionnaire de collections de gestionnaires d’événements d’intégration pour chaque type d’événement ; ces types d’événement peuvent avoir une instanciation différente et des abonnements distincts pour chaque microservice de réception, comme le montre la figure 6-21.</span><span class="sxs-lookup"><span data-stu-id="ad80d-118">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="ad80d-119">Implémentation d’une méthode de publication simplifiée avec RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="ad80d-119">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="ad80d-120">Le code suivant est une version ***simplifiée*** de l’implémentation d’un bus d’événements pour RabbitMQ, qui présente le scénario.</span><span class="sxs-lookup"><span data-stu-id="ad80d-120">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="ad80d-121">On ne gère pas la connexion de cette façon.</span><span class="sxs-lookup"><span data-stu-id="ad80d-121">You don't really handle the connection this way.</span></span> <span data-ttu-id="ad80d-122">Pour voir l’implémentation complète, consultez le code dans le référentiel [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs).</span><span class="sxs-lookup"><span data-stu-id="ad80d-122">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="ad80d-123">Le [code réel](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de la méthode Publish de l’application eShopOnContainers est amélioré à l’aide d’une stratégie de nouvelles tentatives d’[interrogation](https://github.com/App-vNext/Polly). Cette stratégie consiste à réessayer d’exécuter la tâche un certain nombre de fois, au cas où le conteneur RabbitMQ ne serait pas prêt.</span><span class="sxs-lookup"><span data-stu-id="ad80d-123">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="ad80d-124">Cela peut se produire quand docker-compose démarre les conteneurs. Par exemple, le conteneur RabbitMQ peut démarrer plus lentement que les autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ad80d-124">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="ad80d-125">Comme indiqué précédemment, il existe de nombreuses configurations possibles dans RabbitMQ. Ce code doit donc être utilisé uniquement pour les environnements de développement/test.</span><span class="sxs-lookup"><span data-stu-id="ad80d-125">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="ad80d-126">Implémentation du code d’abonnement avec l’API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="ad80d-126">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="ad80d-127">Comme pour le code de publication, le code suivant est une simplification d’une partie de l’implémentation du bus d’événements pour RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="ad80d-127">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="ad80d-128">Là encore, vous n’avez généralement pas besoin de le changer, sauf pour l’améliorer.</span><span class="sxs-lookup"><span data-stu-id="ad80d-128">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="ad80d-129">Chaque type d’événement a un canal associé qui permet d’obtenir les événements à partir de RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="ad80d-129">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="ad80d-130">Vous pouvez avoir autant de gestionnaires d’événements par canal et par type d’événement que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ad80d-130">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="ad80d-131">La méthode Subscribe accepte un objet IIntegrationEventHandler, qui est semblable à une méthode de rappel dans le microservice actuel, en plus de son objet IntegrationEvent associé.</span><span class="sxs-lookup"><span data-stu-id="ad80d-131">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="ad80d-132">Le code ajoute ensuite ce gestionnaire d’événements à la liste des gestionnaires d’événements que chaque type d’événement d’intégration peut avoir par microservice client.</span><span class="sxs-lookup"><span data-stu-id="ad80d-132">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="ad80d-133">Si le code du client n’est pas déjà abonné à l’événement, il crée un canal pour le type d’événement afin de permettre la réception d’événements par envoi (push) à partir de RabbitMQ, quand l’événement concerné est publié depuis un autre service.</span><span class="sxs-lookup"><span data-stu-id="ad80d-133">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="ad80d-134">Comme indiqué ci-dessus, le bus d’événements implémenté dans eShopOnContainers a uniquement et à des fins pédagogiques, car il ne gère que les principaux scénarios, donc il n’est pas prêt pour la production.</span><span class="sxs-lookup"><span data-stu-id="ad80d-134">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="ad80d-135">Pour les scénarios de production, vérifiez les ressources supplémentaires ci-dessous, spécifiques à RabbitMQ, et la section implémentation de la [communication basée sur les événements entre les microservices](./integration-event-based-microservice-communications.md#additional-resources) .</span><span class="sxs-lookup"><span data-stu-id="ad80d-135">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ad80d-136">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ad80d-136">Additional resources</span></span>

<span data-ttu-id="ad80d-137">Solutions prêtes pour la production avec prise en charge de RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="ad80d-137">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="ad80d-138">**EasyNetQ** -client API .net Open source pour RabbitMQ </span><span class="sxs-lookup"><span data-stu-id="ad80d-138">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <https://easynetq.com/>

- <span data-ttu-id="ad80d-139">**MassTransit** </span><span class="sxs-lookup"><span data-stu-id="ad80d-139">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> <span data-ttu-id="ad80d-140">[Précédent](integration-event-based-microservice-communications.md) 
>  [Suivant](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="ad80d-140">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
